# DOCKER NOTES

#### Basic Commands:

- Get a docker image
``` bash
docker image pull <docker-image-path>
```

- List docker images
```bash
docker image ls
```

- Instantiate a image
``` bash
docker container run -p <external-portnumber>:<internal-portnumber> <image-name>

# p: Stands for publish, if P is not mentioned, it will not expose the port.
```
- Connect the container to the terminal
``` bash
docker container run -it ubuntu

# it: Interactive command. It connects the container to the terminal.
```
- Detached execution of a container
```bash
docker container run -d -p 80:8080 <image-name>

# d: Means detached (in background)
```

- Verify running containers
```bash
# For docker in Windows 10
docker container ls
docker container ls -a

# For docker toolbox
docker-machine ip
```
- Stop a running container
```bash
docker container stop <container-id>
```

- Get other images (based on dockerhub images)
```bash
docker pull ubuntu
#or
docker image pull ubuntu
#both are the same command.
```
- Verify docker processes
```bash
docker ps
docker ps -a
```

- Starting a stopped container
```bash
docker container start <container-id>
```

- Attach by ID and Name
```bash
docker attach 665b4a1e17b6 # By ID
docker attach loving_heisenberg # By Name
```

- Removing containers
```bash
docker container rm <container-id> # Removing a specific container
docker container prune # Removing all containers
```

- Logs from Docker Containers
```bash
docker container logs <container-id>
```

- SSH executions
```bash
docker container exec <container-id> bash
docker container exec -it <container-id> bash
```





















