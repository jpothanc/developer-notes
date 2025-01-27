# Environment Variables and PATH Cheat Sheet

```bash
## 1. What Are Environment Variables?
Environment variables are key-value pairs used to configure the behavior of processes. They are critical in production environments to manage configurations without hardcoding values into applications.

---

## 2. Viewing Environment Variables
# List all environment variables
printenv
env

# Display a specific variable
echo $VARIABLE_NAME
# Example: echo $PATH

---

## 3. Setting Environment Variables
### Temporarily (For Current Session Only)
# Set an environment variable
export VARIABLE_NAME="value"
# Example: export MY_VAR="production"

# Add to PATH temporarily
export PATH=$PATH:/new/directory
# Example: export PATH=$PATH:/opt/myapp/bin

# Check the updated PATH
echo $PATH

### Permanently (For All Sessions)
# Add variables to shell configuration files:
# For bash:
nano ~/.bashrc
# For zsh:
nano ~/.zshrc
# For all users (system-wide):
sudo nano /etc/environment

# Add the following lines:
VARIABLE_NAME="value"
PATH=$PATH:/new/directory

# Apply changes to the current session
source ~/.bashrc

---

## 4. Persistent PATH Configuration Examples
# Add a directory to PATH permanently
echo 'export PATH=$PATH:/new/directory' >> ~/.bashrc
source ~/.bashrc

# Add multiple directories to PATH
echo 'export PATH=$PATH:/dir1:/dir2' >> ~/.bashrc
source ~/.bashrc

---

## 5. Setting Environment Variables for Production Deployments

### For Shell-Based Servers
# Set environment variables directly in the server's shell configuration
sudo nano /etc/environment
# Example:
APP_ENV="production"
DB_HOST="127.0.0.1"
DB_PORT="5432"

# Reload environment variables
source /etc/environment

### Using Application Service Managers
#### Systemd Service File
# Define environment variables inside a service file:
sudo nano /etc/systemd/system/myapp.service
# Example:
[Service]
Environment="APP_ENV=production"
Environment="DB_HOST=127.0.0.1"
Environment="DB_PORT=5432"
ExecStart=/path/to/myapp

# Reload and start the service
sudo systemctl daemon-reload
sudo systemctl start myapp

#### Docker Containers
# Pass environment variables as arguments
docker run -e APP_ENV=production -e DB_HOST=127.0.0.1 myapp

# Use an `.env` file with Docker Compose:
nano .env
# Example:
APP_ENV=production
DB_HOST=127.0.0.1

docker-compose up

### Kubernetes (K8s)
# Set environment variables in a Pod or Deployment manifest:
nano deployment.yaml
# Example:
env:
  - name: APP_ENV
    value: "production"
  - name: DB_HOST
    value: "127.0.0.1"

kubectl apply -f deployment.yaml

---

## 6. Removing Environment Variables
# Unset a variable (temporarily for the current session)
unset VARIABLE_NAME
# Example: unset APP_ENV

# Remove a PATH entry (temporarily)
export PATH=$(echo $PATH | sed -e 's;:/directory/to/remove;;')

---

## 7. Useful Commands for Debugging
# View the current PATH
echo $PATH

# Check if a program is in the PATH
which program_name
# Example: which python

# Test environment variable changes
env | grep VARIABLE_NAME
# Example: env | grep APP_ENV

---

## 8. Setting Environment Variables in Crontab
# Edit the crontab and add variables at the top
crontab -e
# Example:
SHELL=/bin/bash
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
APP_ENV="production"
* * * * * /path/to/script.sh

---

## 9. Best Practices for Production
1. **Use `.env` Files**:
   - Store environment variables in a `.env` file for better organization.
   - Example:
     APP_ENV=production
     DB_HOST=127.0.0.1

2. **Avoid Hardcoding Variables**:
   - Use environment variables to manage sensitive data and configurations.

3. **Secure Sensitive Variables**:
   - Use tools like **Vault**, **AWS Secrets Manager**, or **Azure Key Vault** for managing sensitive credentials.

4. **Separate Configurations by Environment**:
   - Use distinct sets of variables for `development`, `staging`, and `production`.

5. **Audit and Document**:
   - Regularly review and document the environment variables required for your application.

---

## 10. Removing Redundant PATH Entries
# Check for duplicate entries in PATH
echo $PATH | tr ':' '\n' | uniq

# Remove duplicates (temporarily)
export PATH=$(echo $PATH | tr ':' '\n' | uniq | tr '\n' ':' | sed 's/:$//')
```

Here's a script to read variables from a .env file, set them as environment variables for all sessions, and then delete the .env file:

```bash
#!/bin/bash

# Path to the .env file
ENV_FILE="/path/to/.env"

# Check if the .env file exists
if [ -f "$ENV_FILE" ]; then
  echo "Reading variables from $ENV_FILE..."

  # Add the environment variables to /etc/environment (system-wide)
  while IFS= read -r line || [ -n "$line" ]; do
    # Ignore empty lines and comments
    if [[ -n "$line" && "$line" != \#* ]]; then
      # Append to /etc/environment
      sudo sh -c "echo $line >> /etc/environment"
    fi
  done < "$ENV_FILE"

  # Reload /etc/environment to apply changes immediately
  echo "Reloading environment variables..."
  source /etc/environment

  # Delete the .env file for security
  echo "Deleting the .env file..."
  rm -f "$ENV_FILE"

  echo "Environment variables set and .env file deleted."
else
  echo "Error: $ENV_FILE not found!"
fi

```

/etc/environment is a system-wide configuration file in Linux used to define environment variables that are accessible to all users and processes on the system.

```bash
# View the contents of /etc/environment

# 1. Using cat
cat /etc/environment

# 2. Using less (useful for long files, press 'q' to exit)
less /etc/environment

# 3. Using nano (for viewing or editing, requires sudo for changes)
sudo nano /etc/environment

# 4. Using vi or vim (for advanced editing)
sudo vi /etc/environment
# - Press 'i' to enter insert mode (edit mode)
# - Press 'Esc' and type ':q!' to exit without saving
# - Or type ':wq' to save and exit

# 5. Using grep (to search for specific variables, e.g., PATH)
grep PATH /etc/environment

# 6. Use echo to check if a variable is set (e.g., APP_ENV)
echo $VARIABLE_NAME
# Example:
echo $APP_ENV

```
