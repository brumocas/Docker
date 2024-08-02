# Docker Basic Commands

Welcome to the Docker Basic Commands guide! This README provides a comprehensive list of essential Docker commands to help you get started with containerization. Docker enables you to develop, ship, and run applications inside containers efficiently.

## Table of Contents

1. [Installation](#installation)
2. [Docker Commands](#docker-commands)
   - [Docker Version and Info](#docker-version-and-info)
   - [Images](#images)
   - [Containers](#containers)
   - [Volumes](#volumes)
   - [Networks](#networks)
   - [Docker Compose](#docker-compose)
3. [Resources](#resources)
4. [Contributing](#contributing)
5. [License](#license)

## Installation

Before you start using Docker, you need to install it on your machine. Follow the official Docker installation guide for your operating system:

- [Docker Desktop for Windows](https://docs.docker.com/desktop/install/windows-install/)
- [Docker Desktop for macOS](https://docs.docker.com/desktop/install/mac-install/)
- [Docker Engine for Linux](https://docs.docker.com/engine/install/)

## Docker Commands

### Docker Version and Info

- **Check Docker version:**
  ```sh
  docker --version
  ```

- **Display system-wide information:**
  ```sh
  docker info
  ```

### Images

- **Pull an image from Docker Hub:**
  ```sh
  docker pull <image_name>
  ```
  Example:
  ```sh
  docker pull nginx
  ```

- **List all images:**
  ```sh
  docker images
  ```

- **Build an image from a Dockerfile:**
  ```sh
  docker build -t <image_name> <path_to_dockerfile>
  ```
  Example:
  ```sh
  docker build -t my_app .
  ```

- **Remove an image:**
  ```sh
  docker rmi <image_name>
  ```
  Example:
  ```sh
  docker rmi nginx
  ```

### Containers

- **Run a container:**
  ```sh
  docker run -d --name <container_name> <image_name>
  ```
  Example:
  ```sh
  docker run -d --name my_nginx nginx
  ```

- **List running containers:**
  ```sh
  docker ps
  ```

- **List all containers (including stopped ones):**
  ```sh
  docker ps -a
  ```

- **Stop a running container:**
  ```sh
  docker stop <container_name>
  ```
  Example:
  ```sh
  docker stop my_nginx
  ```

- **Start a stopped container:**
  ```sh
  docker start <container_name>
  ```
  Example:
  ```sh
  docker start my_nginx
  ```

- **Remove a container:**
  ```sh
  docker rm <container_name>
  ```
  Example:
  ```sh
  docker rm my_nginx
  ```

### Volumes

- **Create a volume:**
  ```sh
  docker volume create <volume_name>
  ```
  Example:
  ```sh
  docker volume create my_volume
  ```

- **List all volumes:**
  ```sh
  docker volume ls
  ```

- **Remove a volume:**
  ```sh
  docker volume rm <volume_name>
  ```
  Example:
  ```sh
  docker volume rm my_volume
  ```

- **Run a container with a volume:**
  ```sh
  docker run -d --name <container_name> -v <volume_name>:<container_path> <image_name>
  ```
  Example:
  ```sh
  docker run -d --name my_nginx -v my_volume:/usr/share/nginx/html nginx
  ```

### Networks

- **Create a network:**
  ```sh
  docker network create <network_name>
  ```
  Example:
  ```sh
  docker network create my_network
  ```

- **List all networks:**
  ```sh
  docker network ls
  ```

- **Connect a container to a network:**
  ```sh
  docker network connect <network_name> <container_name>
  ```
  Example:
  ```sh
  docker network connect my_network my_nginx
  ```

- **Disconnect a container from a network:**
  ```sh
  docker network disconnect <network_name> <container_name>
  ```
  Example:
  ```sh
  docker network disconnect my_network my_nginx
  ```

- **Remove a network:**
  ```sh
  docker network rm <network_name>
  ```
  Example:
  ```sh
  docker network rm my_network
  ```

### Docker Compose

- **Start services defined in `docker-compose.yml`:**
  ```sh
  docker-compose up
  ```

- **Start services in detached mode:**
  ```sh
  docker-compose up -d
  ```

- **Stop services:**
  ```sh
  docker-compose down
  ```

## Resources

- [Docker Documentation](https://docs.docker.com/)
- [Docker Hub](https://hub.docker.com/)
- [Docker Cheat Sheet](https://dockerlabs.collabnix.com/docker/cheatsheet/)

## Contributing

Contributions are welcome! If you have suggestions or improvements, feel free to open an issue or submit a pull request.

## License

This project is licensed under the MIT License.

---

Happy Dockering!

---
