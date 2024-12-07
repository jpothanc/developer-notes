# Advanced Message Processing System

How to run and test in windows using WSL

```shell
1. Install Ubuntu (Windows Subsystem for Linux) from Windows Store.2.
2. Download AMPS Server v5.3.4.78 / Linux (64 bit) from https://eval.crankuptheamps.com/
3. Open Ubuntu terminal and browse to windows download directory
   cd /mnt/c/Users/kalje/Downloads
   Note: /mnt/c/Users/kalje/Downloads corresponds directly to  C:\Users\kalje\Downloads on the Windows side.
4. Extract the tar file with command tar -xvzf AMPS-5.3.4.78-Release-Linux.tar.gz
5. Go to extracted dir cd /mnt C:\Users\kalje\Downloads\AMPS-5.3.4.78-Release-Linux
6. Create a sample amps config file by running ./bin/ampServer --sample-config > config.xml
7.run amps ./bin/ampServer config.xml

Troubleshooting: If you see the message, "Error: /proc/sys/fs/file-max
is set less than the minimum of 262144" then the file-max size needs
to be increased. The recommended value is 2097152. To set the value,
enter the following command as root, where the number is the file-max
size to use.

Fix this by any of the below commands
- echo 2097152 > /proc/sys/fs/file-max
- sudo sh -c "echo 2097152 > /proc/sys/fs/file-max"

8. In a different Ubuntu shell, run  ss -tulnp | grep ampServer to see connection details of amps server.

9. AMPS Web Monitoring or Management interface will be available at: http://localhost:8085/#/
```

## AMPS Server Started

```shell
jpothanc@LAPTOP-UMF83CB2:/mnt/c/Users/kalje/Downloads/AMPS-5.3.4.78-Release-Linux$ ./bin/ampServer config.xml
AMPS 5.3.4.78.928656.fa0d0b4 - Copyright (c) 2006-2024 60East Technologies Inc.
(Built: 2024-12-04T21:19:07Z)
For all support questions: support@crankuptheamps.com

Warning: ulimit -n is set less than the recommended value of 32768

Warning: /sys/kernel/mm/transparent_hugepage/enabled is not set to the recommended value of [madvise] or the acceptable value of [never]

libnuma: Warning: /sys not mounted or invalid. Assuming one node: No such file or directory
2024-12-06T22:17:58.9661630+08:00 [1] info: 00-0015 AMPS initialization completed (1 seconds).
```

## Check AMPS Server

```Shell
jpothanc@LAPTOP-UMF83CB2:~$ ss -tulnp | grep ampServer
tcp   LISTEN 0      200          0.0.0.0:8085      0.0.0.0:*    users:(("ampServer",pid=258,fd=31))
tcp   LISTEN 0      4096               *:9007            *:*    users:(("ampServer",pid=258,fd=3))
tcp   LISTEN 0      4096               *:9008            *:*    users:(("ampServer",pid=258,fd=4))
tcp   LISTEN 0      200             [::]:8085         [::]:*    users:(("ampServer",pid=258,fd=32))
```

## Python Server

```python
1.Open Pycharm and create a new project called amps-server
2 Install python amps client : pip install amps_python_client

import json
import AMPS
import sys

uri_ = "tcp://localhost:9007/amps/json"

client = AMPS.Client("examplePublisher")

order_message = {
    "order_id": "1000",
    "product": "0005.HK",
    "quantity": 1000,
    "price": 50,
    "customer": "Acme Corp",
    "status": "NEW"
}

try:
    client.connect(uri_)
    client.logon()
    # client.publish("messages", '{ "hi" : "Hello, world!"}')
    message_str = json.dumps(order_message)
    client.publish("orders", message_str)

except AMPS.AMPSException as e:
    sys.stderr.write(str(e))

client.publish_flush()
client.close()
```

## Python Client

```python
1.Open Pycharm and create a new project called amps-client
2 Install python amps client : pip install amps_python_client

from AMPS import Client

# Here, we create a Client object and connect to an AMPS server.
client = Client("test")
client.connect("tcp://127.0.0.1:9007/amps/json")
client.logon()

#for message in client.subscribe("messages"):
    #print(message.get_data())

from AMPS import Client, Message

# Here, we create a Client object and connect to an AMPS server.
client = Client("test")
client.connect("tcp://127.0.0.1:9007/amps/json")
client.logon()

topic_name = "simple_order_view"

# runs the SOW query, processes all of the messages
# from the query, and then returns.
for message in client.sow(topic_name):
    if message.get_command() == Message.Command.SOW:
        print(message.get_data())

for message in client.subscribe(topic_name):
    print(message.get_data())

```

## SOW and Views

```xml
<SOW>
<Topic>
    <Name>orders</Name>
    <MessageType>json</MessageType>
    <Key>/order_id</Key>
    <Durability>transient</Du
    rability >
</Topic>
<View>
    <Name>simple_order_view</Name>
    <UnderlyingTopic>orders</UnderlyingTopic>
    <MessageType>json</MessageType>
    <Projection>
        <Field>/order_id</Field>
        <Field>/product</Field>
        <Field>/quantity</Field>
        <Field>/customer</Field>
        <Field>/price</Field>
        <!-- Formula columns. -->
		<Field>SUM(/quantity * /price) AS /notional</Field>
    </Projection>
    <Select>/order_id, /product, /quantity</Select>
    <Grouping>
        <Field>/order_id</Field>
    </Grouping>
</View>

<View>
    <Name>aggregated_product_view</Name>
    <UnderlyingTopic>orders</UnderlyingTopic>
    <MessageType>json</MessageType>
    <Projection>
        <Field>/product</Field>
        <!-- counts the underlying unique  orders in the aggregation. -->
        <Field>COUNT(/order_id) AS /completedOrders</Field>
        <!-- aggregate the quantity based on unique products. -->
        <Field>SUM(/quantity) AS /totalQuantity</Field>
    </Projection>
    <Select>/order_id, /product, /quantity</Select>
    <!-- Group by product and quantity. -->
    <Grouping>
        <Field>/product</Field>
        <Field>/quantity</Field>
    </Grouping>
    <Filter>/status = 'complete'</Filter>
</View>
</SOW>
```
