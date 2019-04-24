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

## CREATE A NEW DOCKER IMAGE WITH JDK INSTALLED IN IT
###### STEPS
```bash
docker image ls
docker container run -it ubuntu (connected to its terminal)
apt-get update
apt-get install # We can use the command line to install JDK, but sometimes we may not know about the correct package, so we can proceed in another way.
apet-cache search jdk # before executing install
                      # Choose one option from the list
apt-get install -y openjdk-8-jdk
javac # For verifying that java is installed.
exit
docker container ls # For verifying that no containers are running.

# -----------------------------------------------------------------
# Now we will create a new image from our current state: docs.docker.com for more information.
# -----------------------------------------------------------------

docker container commit [many-parameters]
docker container commit -a "Franco Arratia franco.robert.fral@gmail.com" <container-id> <new-image-name>

# -----------------------------------------------------------------
# If the image will not be published to dockerhub, the image name my-jdk-image will be helpful locally.
# -----------------------------------------------------------------

docker image ls
docker container prune # Remove all unused containers
docker container run -it <my-new-image-name>


# -----------------------------------------------------------------
# Once executed, we should able to verify the java version that we have installed in previous steps.
# -----------------------------------------------------------------
```




















