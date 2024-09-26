```python
import os
from pathlib import Path
import shutil
import zipfile
import hashlib
import fcntl  # Only available on Unix-like systems
import time

# 1. Check if a file exists

# Using os.path.exists()
file_path = 'path/to/your/file.txt'
if os.path.exists(file_path):
    print(f"The file {file_path} exists using os.path.exists().")
else:
    print(f"The file {file_path} does not exist using os.path.exists().")

# Using pathlib.Path.exists()
file_path = Path('path/to/your/file.txt')
if file_path.exists():
    print(f"The file {file_path} exists using pathlib.")
else:
    print(f"The file {file_path} does not exist using pathlib.")

# 2. Check if the path is a file or directory

# Check if it's a file
if file_path.is_file():
    print(f"{file_path} is a file.")

# Check if it's a directory
if file_path.is_dir():
    print(f"{file_path} is a directory.")

# 3. Reading files

# Reading the entire file
with open('path/to/your/file.txt', 'r') as file:
    content = file.read()
    print("File content:", content)

# Reading file line by line
with open('path/to/your/file.txt', 'r') as file:
    for line in file:
        print(line.strip())

# 4. Writing to a file

# Writing (overwriting) to a file
with open('path/to/your/file.txt', 'w') as file:
    file.write('This is some new content.\n')

# Appending to a file
with open('path/to/your/file.txt', 'a') as file:
    file.write('This is additional content.\n')

# 5. Deleting a file

# Deleting a file using os.remove()
if os.path.exists(file_path):
    os.remove(file_path)
    print(f"{file_path} has been deleted.")
else:
    print(f"The file {file_path} does not exist.")

# 6. Copying and moving files

# Copy a file using shutil.copy()
source = 'path/to/source/file.txt'
destination = 'path/to/destination/file.txt'
shutil.copy(source, destination)
print(f"Copied {source} to {destination}")

# Move a file using shutil.move()
shutil.move(source, destination)
print(f"Moved {source} to {destination}")

# 7. Getting file size

# Get the size of the file
file_path = 'path/to/your/file.txt'
file_size = os.path.getsize(file_path)
print(f"The size of {file_path} is {file_size} bytes.")

# 8. Checking file permissions

# Check if the file is readable
if os.access(file_path, os.R_OK):
    print(f"{file_path} is readable.")

# Check if the file is writable
if os.access(file_path, os.W_OK):
    print(f"{file_path} is writable.")

# Check if the file is executable
if os.access(file_path, os.X_OK):
    print(f"{file_path} is executable.")

# 9. Zipping files

# Creating a zip file
with zipfile.ZipFile('path/to/your/zipfile.zip', 'w') as zipf:
    zipf.write('path/to/your/file1.txt')
    zipf.write('path/to/your/file2.txt')
    print("Files have been zipped.")

# Extracting a zip file
with zipfile.ZipFile('path/to/your/zipfile.zip', 'r') as zipf:
    zipf.extractall('path/to/extracted_files')
    print("Files have been extracted.")

# 10. Calculate the checksum of a file (MD5, SHA-256, etc.)

# Function to calculate the checksum of a file
def calculate_checksum(file_path, algorithm='md5'):
    hash_func = hashlib.new(algorithm)
    with open(file_path, 'rb') as f:
        while chunk := f.read(8192):
            hash_func.update(chunk)
    return hash_func.hexdigest()

# Example usage (MD5 checksum)
file_path = 'path/to/your/file.txt'
checksum_md5 = calculate_checksum(file_path, 'md5')
print(f"MD5 checksum of {file_path}: {checksum_md5}")

# Example usage (SHA-256 checksum)
checksum_sha256 = calculate_checksum(file_path, 'sha256')
print(f"SHA-256 checksum of {file_path}: {checksum_sha256}")

# 11. File Locking (Unix-based systems, requires fcntl)

# Open a file and lock it
with open('path/to/your/file.txt', 'w') as f:
    try:
        fcntl.flock(f, fcntl.LOCK_EX | fcntl.LOCK_NB)
        print(f"File {file_path} is locked for writing.")
        # Perform file operations here
    except IOError:
        print(f"Cannot lock the file {file_path}. It may already be locked.")
    finally:
        fcntl.flock(f, fcntl.LOCK_UN)
        print(f"File {file_path} has been unlocked.")

# 12. Monitor File Changes (Simple polling mechanism)

# Monitor a file for changes by checking its last modified time
def monitor_file_changes(file_path):
    last_modified_time = os.path.getmtime(file_path)
    while True:
        time.sleep(5)  # Poll every 5 seconds
        current_modified_time = os.path.getmtime(file_path)
        if current_modified_time != last_modified_time:
            print(f"{file_path} has been modified.")
            last_modified_time = current_modified_time

# Example usage:
# monitor_file_changes('path/to/your/file.txt')  # This will run indefinitely

```
