```python
from ftplib import FTP_TLS

def send_file_to_ftps(host, port, username, password, file_path, destination_path):
    try:
        # Connect to the FTPS server
        ftps = FTP_TLS()
        ftps.connect(host, port)
        ftps.login(username, password)

        # Use secure data connection
        ftps.prot_p()

        # Transfer the file
        with open(file_path, 'rb') as file:
            ftps.storbinary(f'STOR {destination_path}', file)

        print(f"File '{file_path}' uploaded successfully to '{destination_path}' on FTPS server.")

        # Quit
        ftps.quit()
    except Exception as e:
        print(f"An error occurred: {e}")

# Example usage:
host = 'ftp.example.com'
port = 21  # Default FTPS port
username = 'your_username'
password = 'your_password'
file_path = 'local_file.txt'
destination_path = '/remote_directory/remote_file.txt'

send_file_to_ftps(host, port, username, password, file_path, destination_path)

```
