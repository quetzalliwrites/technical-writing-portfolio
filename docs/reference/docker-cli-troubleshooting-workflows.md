# Docker Troubleshooting Workflows CLI Cheatsheet

Welcome to your **Docker Troubleshooting Workflows Cheatsheet**! 

The following guide provides essential commands to help you diagnose and resolve common Docker container issues.

Docker CLI allows you to interact with Docker containers, images, networks, and volumes via the command line to manage and troubleshoot containerized applications.

Below are some commonly used commands and their descriptions to support you during troubleshooting workflows.

---

## Common Commands

| Command                        | Description                                                                                  | 
|--------------------------------|----------------------------------------------------------------------------------------------|
| `docker ps`                    | List all running containers and their statuses. Useful for checking if a container is running. |
| `docker logs`                  | Retrieve logs for a specific container. Helpful for debugging container-related issues.        |
| `docker exec`                  | Run a command inside a running container. Useful for inspecting the container's file system or processes. |
| `docker inspect`               | Display detailed information about a container, image, or other Docker objects.                |
| `docker stats`                 | Show real-time performance metrics of running containers.                                      |

---

## Useful Flags

The table below explains some useful flags to use with these commands for more precise troubleshooting.

| Command                  | Flags                           | Description                                             |
|--------------------------|---------------------------------|---------------------------------------------------------|
| `docker ps`              | `-a`                            | List all containers, including stopped ones.             |
|                          | `--filter`                      | Filter output based on conditions (e.g., `status=exited`).|
| `docker logs`            | `--tail`                        | Display the last **N** lines of the logs.                |
|                          | `-f` (or `--follow`)            | Follow log output in real-time.                          |
| `docker exec`            | `-it`                           | Run an interactive terminal inside the container.        |
|                          | `--user`                        | Run the command as a specified user.                     |
| `docker inspect`         | `--format`                      | Format the output using a Go template.                   |
| `docker stats`           | `--no-stream`                   | Show a one-time snapshot of the container's stats.       |

---

## Example Workflows

Here are some common Docker troubleshooting scenarios and example commands to help you navigate issues more effectively.

### Workflow 1: **Listing All Containers**
Use `docker ps` to get a list of all containers and their statuses.

#### Command:
```bash
docker ps -a
```

### Workflow 2: **Viewing Logs for a Specific Container**
Use `docker logs` to retrieve logs from a specific container, which can help identify issues with the container's application.

#### Command:
```bash
docker logs --tail 100 [container-name-or-id]
```

### Workflow 3: **Executing a Command in a Container**
Use `docker exec` to execute a command within a container for further inspection (e.g., checking a log file or running a diagnostic script).

#### Command:
```bash
docker exec -it [container-name-or-id] /bin/bash
```

### Workflow 4: **Inspecting a Container's Configuration**
Use `docker inspect` to view detailed information about a container, such as its configuration and environment variables.

#### Command:
```bash
docker inspect [container-name-or-id]
```

### Workflow 5: **Monitoring Container Performance**
Use `docker stats` to monitor real-time performance metrics, such as CPU and memory usage, for running containers.

#### Command:
```bash
docker stats
```

---

## Additional Resources

For more information on Docker CLI, see the official documentation:

- [Docker Command-Line Reference](https://docs.docker.com/engine/reference/commandline/docker/)
- [Docker Troubleshooting Guide](https://docs.docker.com/config/daemon/troubleshoot/)
