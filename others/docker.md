## How to Start Using Docker in Windows

1. **Install Docker Desktop**:

   - Download Docker Desktop for Windows from [Docker's official website](https://www.docker.com/products/docker-desktop).
   - Run the installer and follow the on-screen instructions.
   - After installation, start Docker Desktop from the Start menu.

2. **Configuration**:

   - During the first launch, Docker Desktop will ask you to log in with your Docker Hub account. If you don’t have an account, you can create one [here](https://hub.docker.com/).
   - Docker Desktop may require you to enable the WSL 2 feature on Windows. Follow the prompts to enable it if necessary.

3. **Verify Installation**:

   - Open PowerShell or Command Prompt and run the following command to verify Docker is installed correctly:
     ```sh
     docker --version
     ```
   - You should see the Docker version information.

4. **Run Docker**:

   - Start Docker Desktop if it’s not already running.
   - To check if Docker is running correctly, you can run:
     ```sh
     docker run hello-world
     ```
   - This command downloads a test image and runs it in a container. If Docker is installed correctly, you will see a "Hello from Docker!" message.

5. **Start Docker if Not Running**:
   - If Docker is not running, you can start it using the following methods:
     - **From the Start Menu**: Search for "Docker Desktop" and click to start it.

## Login

- `docker login`: Log in to a Docker registry.

  - `echo "your-password" | docker login --username your-username --password-stdin`

- `docker logout`: Log out from a Docker registry.

## Create an Image and Push

- `docker build -t <image_name> .`: Build an image from the Dockerfile in the current directory.

  - Example: `docker build -t my_image:<tag> .`(docker build -t rcengine:1.0 .)

- `docker tag <image_name> <repository>/<image_name>:<tag>`: Tag an image to a repository.

  - Example: `docker tag my_image my_repo/my_image:v1`(docker tag rcengine:1.0 kaljessy/rcengine:1.0)

- `docker push <repository>/<image_name>:<tag>`: Push an image to a repository.
  - Example: `docker push my_repo/my_image:v1`(docker push kaljessy/rcengine:1.0)

## Docker Commands for Managing Running Containers

| Command                                    | Description                                                      | Example                            |
| ------------------------------------------ | ---------------------------------------------------------------- | ---------------------------------- |
| `docker ps`                                | List all running containers.                                     | `docker ps`                        |
| `docker stop <container_id>`               | Stop a running container.                                        | `docker stop abc123`               |
| `docker start <container_id>`              | Start a stopped container.                                       | `docker start abc123`              |
| `docker restart <container_id>`            | Restart a container.                                             | `docker restart abc123`            |
| `docker rm <container_id>`                 | Remove a container.                                              | `docker rm abc123`                 |
| `docker logs <container_id>`               | Fetch the logs of a container.                                   | `docker logs abc123`               |
| `docker exec -it <container_id> <command>` | Run a command in a running container.                            | `docker exec -it abc123 /bin/bash` |
| `docker inspect <container_id>`            | Display detailed information on a container.                     | `docker inspect abc123`            |
| `docker stats <container_id>`              | Display a live stream of container(s) resource usage statistics. | `docker stats abc123`              |

## Running

```sh
# -p 8007:8080: This option maps a port on the host to a port in the container.

# The first 8007 is the port number on the host (your machine).
# The second 8080 is the port number inside the container.
# This means that any traffic sent to port 8007 on the host will be forwarded to port 8080 in the container.
# kaljessy/rcengine:1.0: This specifies the Docker image to use for the container and its tag.

# kaljessy/rcengine is the name of the Docker image.
# 1.0 is the tag of the image, which usually indicates the version.

docker run -p 8007:8080 kaljessy/rcengine:1.0

```

## Sample Docker File for Java SpringBoot Application

```docker
# Use an official OpenJDK runtime as the base image
FROM amazoncorretto:19.0.2

# Set the working directory in the container
WORKDIR /app

# Copy the Spring Boot application JAR file into the container
#COPY target/*.jar app.jar
COPY build/libs/*.jar app.jar

# Expose the port that the Spring Boot application will run on
# This is just a instruction to the container, it doesn't actually publish the port
# This should be identical to the port that the Spring Boot application is configured to run on
EXPOSE 7070

# Define environment variables (if needed)
#ENV SPRING_PROFILES_ACTIVE=dev

# Command to run the Spring Boot application when the container starts
CMD ["java", "-jar", "app.jar"]
```
