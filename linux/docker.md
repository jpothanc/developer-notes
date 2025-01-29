# Docker userful commands

```bash
# List all running containers
docker ps

# List all containers (running and stopped)
docker ps -a

# List containers and filter by name
docker ps -a | grep productstorejs

# Remove a specific container by name
docker rm <container_name>

# Remove a container by image name
docker rm kaljessy/productstorejs

# List containers filtered by a specific image
docker ps -a --filter "ancestor=kaljessy/productstorejs:latest"

# Forcefully remove all containers created from a specific image
docker rm -f $(docker ps -a --filter "ancestor=kaljessy/productstorejs:latest" -q)

# List all Docker images
docker images

# Remove a specific Docker image
docker rmi <image_name>

# Remove all unused (dangling) images
docker image prune

# Remove all stopped containers, unused networks, and dangling images
docker system prune

# Stop a running container
docker stop <container_name>

# Start a stopped container
docker start <container_name>

# Restart a container
docker restart <container_name>

# View logs of a container
docker logs <container_name>

# View real-time logs of a container
docker logs -f <container_name>

# Execute a command inside a running container
docker exec -it <container_name> <command>

# Run a new container from an image
docker run -d --name <container_name> -p <host_port>:<container_port> <image_name>

# Build a Docker image from a Dockerfile
docker build -t <image_name> .

# Push an image to a Docker registry
docker push <image_name>

# Pull an image from a Docker registry
docker pull <image_name>

# Inspect details of a container or image
docker inspect <container_name_or_image_name>

# List all Docker networks
docker network ls

# Create a new Docker network
docker network create <network_name>

# Connect a container to a network
docker network connect <network_name> <container_name>

# Disconnect a container from a network
docker network disconnect <network_name> <container_name>

# List all Docker volumes
docker volume ls

# Create a new Docker volume
docker volume create <volume_name>

# Remove a Docker volume
docker volume rm <volume_name>


```
