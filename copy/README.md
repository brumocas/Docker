# Copying Files to a Docker Container

This guide explains how to use the `docker cp` command to copy files and directories from the host machine to a Docker container.

## Prerequisites

- Docker must be installed on your system.
- You should have a running Docker container.
- Basic knowledge of terminal commands is assumed.

## Commands Overview

### Copying a Single File

To copy a single file from the host to a container, use the following command:

```sh
sudo docker cp <file_path_on_host> <container_id>:<path_in_container>
```

### Copying Multiple Files or a Directory

To copy multiple files or an entire directory, specify the directory path instead of using a wildcard (`*`):

```sh
sudo docker cp <directory_path_on_host> <container_id>:<destination_directory_in_container>
```

## Example

### Step-by-Step Guide

Assume you want to copy the entire `dataset` directory from your host machine to the `/root/` directory inside a Docker container with ID `30bb18209b59`.

1. **Navigate to the Correct Directory on Host**:
   Open your terminal and navigate to the directory where your `dataset` directory is located. For example:

   ```sh
   cd ~/Master/DOPE/train/docker
   ```

2. **Copy the `dataset` Directory**:
   Use the `docker cp` command to copy the directory to the container:

   ```sh
   sudo docker cp ../../dataset 30bb18209b59:/root/
   ```

   This command will copy the entire `dataset` directory, including all its contents, from your host machine to the `/root/` directory inside the Docker container.

### Verifying the Copy Operation

To ensure that the files have been copied correctly, follow these steps:

1. **Access the Docker Container**:
   Use the following command to get a bash shell inside the running container:

   ```sh
   sudo docker exec -it 30bb18209b59 /bin/bash
   ```

2. **List the Contents in the Container**:
   Once inside the container, navigate to the destination directory and list the contents to verify:

   ```sh
   ls /root/dataset
   ```

   This should display the files and directories copied from your host machine’s `dataset` directory.

## Troubleshooting

### Common Issues

1. **Incorrect Container ID**:
   Ensure the container ID (`30bb18209b59`) is correct. You can list all running containers with:

   ```sh
   sudo docker ps
   ```

2. **Invalid Destination Path**:
   Make sure the destination path (`/root/`) exists in the container. You can create the directory inside the container if it doesn't exist:

   ```sh
   sudo docker exec -it 30bb18209b59 /bin/bash -c "mkdir -p /root/dataset"
   ```

3. **Permissions**:
   You might need to run these commands with `sudo` depending on your system's permissions.

## Conclusion

Using the `docker cp` command is a straightforward way to copy files and directories between your host and Docker containers. This guide should help you perform these operations efficiently.