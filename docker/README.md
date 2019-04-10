# DOCKER NOTES

#### Basic Commands:

- Get a docker image
``` bash
docker image pull <docker-image-path>
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

























