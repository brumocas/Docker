# Dockerfiles Documentation

This document provides an overview and detailed instructions on how to work with the Dockerfiles in this project.

## Table of Contents

- [Introduction](#introduction)
- [Directory Structure](#directory-structure)
- [Dockerfile Overview](#dockerfile-overview)
- [Building Docker Images](#building-docker-images)
- [Running Docker Containers](#running-docker-containers)
- [Dockerfile Best Practices](#dockerfile-best-practices)
- [Troubleshooting](#troubleshooting)
- [Additional Resources](#additional-resources)

## Introduction

This project includes several Dockerfiles used to build Docker images for different components of the application. Each Dockerfile defines a set of instructions to build an image with the necessary environment and dependencies.

## Directory Structure

Provide a brief description of the directory structure, especially where the Dockerfiles are located.

```
/project-root
│
├── /app
│   ├── Dockerfile       # Dockerfile for the app component
│   ├── ...
│
├── /database
│   ├── Dockerfile       # Dockerfile for the database component
│   ├── ...
│
└── README.md            # This README file
```

## Dockerfile Overview

### App Component

Path: `/app/Dockerfile`

```dockerfile
# Use the official Ubuntu base image
FROM ubuntu:20.04

# Set environment variables
ENV DEBIAN_FRONTEND=noninteractive

# Install dependencies
RUN apt-get update && apt-get install -y \
    python3 \
    python3-pip \
    && rm -rf /var/lib/apt/lists/*

# Copy application files
COPY . /app

# Set working directory
WORKDIR /app

# Install Python dependencies
RUN pip3 install -r requirements.txt

# Expose port
EXPOSE 8080

# Define the command to run the application
CMD ["python3", "app.py"]
```

### Database Component

Path: `/database/Dockerfile`

```dockerfile
# Use the official MySQL base image
FROM mysql:5.7

# Set environment variables
ENV MYSQL_ROOT_PASSWORD=rootpassword
ENV MYSQL_DATABASE=mydatabase

# Copy initialization scripts
COPY ./init-db.sql /docker-entrypoint-initdb.d/

# Expose port
EXPOSE 3306
```

## Building Docker Images

Explain how to build the Docker images using the Dockerfiles provided.

### Building the App Image

Navigate to the directory containing the Dockerfile and run the following command:

```sh
cd app
sudo docker build -t myapp:latest .
```

### Building the Database Image

Navigate to the directory containing the Dockerfile and run the following command:

```sh
cd database
sudo docker build -t mydatabase:latest .
```

## Running Docker Containers

Provide instructions for running the Docker containers based on the built images.

### Running the App Container

```sh
sudo docker run -d -p 8080:8080 --name myapp myapp:latest
```

### Running the Database Container

```sh
sudo docker run -d -p 3306:3306 --name mydatabase -e MYSQL_ROOT_PASSWORD=rootpassword -e MYSQL_DATABASE=mydatabase mydatabase:latest
```

## Dockerfile Best Practices

Share best practices for writing Dockerfiles.

- **Use Official Base Images**: Start with official base images to ensure security and stability.
- **Minimize Layers**: Combine commands to minimize the number of layers and reduce image size.
- **Use `.dockerignore`**: Exclude unnecessary files using a `.dockerignore` file.
- **Leverage Build Caching**: Order commands to take advantage of Docker’s layer caching.
- **Set Appropriate Permissions**: Ensure that files and directories have appropriate permissions.
- **Clean Up After Installations**: Remove package lists and temporary files to keep the image clean.

## Troubleshooting

Provide common issues and their solutions.

### Issue: Image Build Fails

**Solution:** Check the Dockerfile for syntax errors and ensure all dependencies are correctly specified.

### Issue: Container Fails to Start

**Solution:** Review the Docker logs to identify the error. Use the `docker logs <container_id>` command.

### Issue: Changes Not Reflected

**Solution:** Ensure that the image is rebuilt after making changes to the Dockerfile or application code.

```sh
sudo docker build -t myapp:latest .
sudo docker run -d -p 8080:8080 --name myapp myapp:latest
```

## Additional Resources

- [Docker Documentation](https://docs.docker.com/)
- [Best Practices for Writing Dockerfiles](https://docs.docker.com/develop/develop-images/dockerfile_best-practices/)
- [Docker Cheat Sheet](https://github.com/wsargent/docker-cheat-sheet)

---

This template provides a comprehensive guide specifically for working with Dockerfiles in your project. Adjust the examples and instructions to fit your actual project setup and requirements.