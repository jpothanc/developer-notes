```bash
#!/bin/bash

# Automated Docker Installation Script for Linux

# Step 1: Uninstall Old Versions of Docker (if any)
echo "Removing old Docker versions (if any)..."
sudo apt remove -y docker docker-engine docker.io containerd runc

# Step 2: Update Your System
echo "Updating system packages..."
sudo apt update -y
sudo apt upgrade -y

# Step 3: Install Required Dependencies
echo "Installing dependencies..."
sudo apt install -y apt-transport-https ca-certificates curl software-properties-common

# Step 4: Add Docker’s Official GPG Key
echo "Adding Docker's GPG key..."
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg

# Step 5: Add Docker Repository
echo "Adding Docker repository..."
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

# Step 6: Install Docker
echo "Installing Docker..."
sudo apt update -y
sudo apt install -y docker-ce docker-ce-cli containerd.io

# Step 7: Verify Docker Installation
echo "Verifying Docker installation..."
docker --version
sudo systemctl start docker
sudo systemctl enable docker
sudo systemctl status docker

# Step 8: Run Docker as a Non-Root User (Optional)
echo "Adding current user to the Docker group..."
sudo usermod -aG docker $USER
echo "Please log out and log back in for the changes to take effect."
echo "After logging back in, run 'docker run hello-world' to verify Docker works without sudo."

# Step 9: Install Docker Compose (Optional)
echo "Installing Docker Compose..."
sudo curl -L "https://github.com/docker/compose/releases/download/v2.20.0/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
sudo chmod +x /usr/local/bin/docker-compose
docker-compose --version

echo "Docker installation and setup complete!"

# Troubleshooting Tips
# - If you get a permission error, ensure your user is in the `docker` group and you’ve logged out and back in.
# - If Docker is not starting, check the status: `sudo systemctl status docker`.
# - Ensure your firewall allows Docker traffic.
```
