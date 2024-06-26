# curl Commands

# curl: Command Line Tool for URL

curl is a powerful command-line tool and library for transferring data with URLs. It supports various protocols, including HTTP, HTTPS, FTP, and more. curl is widely used for testing APIs, downloading files, and interacting with web services from the command line.

## Relevance of curl

- **API Testing**: Allows developers to easily test and debug APIs.
- **Automation**: Useful for scripting and automating data transfer tasks.
- **Flexibility**: Supports a wide range of protocols and customization options.
- **Cross-Platform**: Available on multiple operating systems, including Windows, macOS, and Linux.

## Where to Download curl

- **Windows**: Download from the [official website](https://curl.se/windows/).
- **macOS**: curl is pre-installed on macOS. You can also use Homebrew to install or update it:
  ```sh
  brew install curl
  ```
- **Linux**: Use your package manager to install curl.
  ```sh
  sudo apt-get install curl
  ```

```sh
# Basic GET Request
curl http://example.com

# GET Request with Custom Headers

curl -H "Content-Type: application/json" http://example.com

# POST Request with Data

curl -X POST -d "param1=value1&param2=value2" http://example.com

# POST Request with JSON Data

curl -X POST -H "Content-Type: application/json" -d '{"key1":"value1", "key2":"value2"}' http://example.com

# PUT Request

curl -X PUT -d "param1=value1&param2=value2" http://example.com/resource/1

# DELETE Request

curl -X DELETE http://example.com/resource/1

# Download a File

curl -O http://example.com/file.zip

# Upload a File

curl -F "file=@/path/to/file" http://example.com/upload

# Follow Redirects

curl -L http://example.com

## Set Timeout

curl --max-time 30 http://example.com

# Include Response Headers in Output

curl -i http://example.com

# Send Authentication

curl -u username:password http://example.com

# Save Response to a File

curl -o output.txt http://example.com

# Use a Proxy

curl -x http://proxy.example.com:8080 http://example.com

# Specify HTTP Method

curl -X METHOD http://example.com

# Pass Data from a File

curl -d "@data.json" http://example.com

# Send Custom Request Headers

curl -H "Authorization: Bearer token" http://example.com

# Download Multiple Files

curl -O http://example.com/file1.zip -O http://example.com/file2.zip

# Show Only Response Code

curl -o /dev/null -w "%{http_code}" http://example.com
```
