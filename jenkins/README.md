# JENKINS NOTES

### ADITIONAL AUTOMATION
- Setup Git repository polling
- Deployment to our tomcat servers
- We will setup a couple of tasks to run in parallel
- And we will briefly explain how to setup tomcat on EC2 in Amazon Web Service

### MASTER SLAVE CONFIGURATION IN JENKINS
##### Different ways to start slave agent
- The master can start the slave agents via SSH.
- Start the slave agent manually using Java Web Start
- Install the slave agent as a Windows Service.
- Start the slave agent directly from the command line on the slave machine.

In Linux environment the most convenient way to start a Jenkis slave is undoubtedly to use SSH

##### Required commands
###### Connect to our dropplet via SSH.
```bash
ssh root@ip
change the password
```

###### Install jenkins throught the terminal
```bash
wget -q -O - http://pkg.jenkins-ci.org/debian/jenkins-ci.org.key | apt-key add -
 
echo deb http://pkg.jenkins-ci.org/debian binary/ > /etc/apt/sources.list.d/jenkins.list
 
apt-get update
 
apt-get install jenkins

less <link provided in the initial of jenkins>
01393e4ea0504e639f4710c32c9565e1
```

###### Start the slave agent
* Master node will start the slave agent on the slave machine via SSH
* Automatic SSH login without password from master node to the slave is needed.
* Master node will be running as a specific user called JENKINS to start the slave agent.

###### In master node
```bash
sudo -iu jenkins
ssh-keygen -t rsa
ssh root@slave-ip mkdir -p .ssh
Type the root password of the slave machine to proceed

cat .ssh/id_rsa.pub | ssh root@slave-ip 'cat >> .ssh/authorized_keys'
Enter a root password of the slave node.

From now, we can login to the slave from the master node, without password.
ssh root@slave-ip

ssh root@slave-ip mkdir -p .ssh
```


###### In slave node
```bash

mkdir bin
cd bin/
pwd
wget http://<master-node-ip>:8080/jnlpJars/slave.jar
wget http://142.93.66.109:8080/jnlpJars/agent.jar
ls
install java to slave node
sudo apt-get install default-jre

wget http://142.93.66.109:8080/jnlpJars/agent.jar
```

###### In jenkins terminal (Master Node)
- Manage jenkins
- Manage nodes
- New node
- add a name
- enter required information

###### Executor
* A jenkins executor is one of the basic building blocks which allow a build to run on a node.
* Think of an executor as a single "Process ID", or as the basic unit of resource that jenkins executes on your machine to run a build.
* This number executors basically specifies the maximun number of concurrent builds that jenkins may perform on this agent.
* A good value for the number of executors to start with would be the number of CPU cores on the machine.
* Setting a higher value would cause each build to take longer, but could increase the overall throughput.
* For example, one build might be CPU-bound, while a second build running at the same time
might be I/O-bound. So the second build could take advantage of the spare I/O capacity at that moment.

#of executors: 2
- Remote directory: ```/var/jenkins```
- Launch command: ```ssh root@ip-slave java -jar /root/bin/slave.jar```
- SAVE




Launch agent via execution of command on the master

- sudo java -jar jenkins-cli.jar -s http://142.93.66.109:8080/ version
- wget http://142.93.66.109:8080/jnlpJars/jenkins-cli.jar



# JENKINS & DOCKER
#### Docker Installation

``` bash
Config file /lib/systemd/system/docker.service
```

##### CentOS
``` bash
# Utilities
sudo yum install -y yum-utils device-mapper-persistent-data lvm2

# Add to the docker repository
sudo yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo

# Install docker
sudo yum install docker-ce -y

# Start the service
sudo systemctl start docker

# Initialize with the system (once the OS starts)
sudo systemctl enable docker

# Add the user to the docker group
# whoami # To know the user name.
sudo usermod -aG docker <result_of_whoami_command>

# Exit from the sesion
exit

# Init docker container again with the user and test.
docker run hello-world
```
##### Fedora
The installation is similar to CentOS, we only need to change the repository URL.

``` bash
# Utilities
sudo yum install -y yum-utils device-mapper-persistent-data lvm2

# Add to the docker repository
sudo yum-config-manager --add-repo https://download.docker.com/linux/fedora/docker-ce.repo

# Install docker
sudo yum install docker-ce -y

# Initialize with the system (once the OS starts)
sudo systemctl enable docker

# Add the user to the docker group
# whoami # To know the user name.
sudo usermod -aG docker <result_of_whoami_command>

# Exit from the sesion
exit

# Init docker container again with the user and test.
docker run hello-world
```

##### Ubuntu
``` bash
# Update the repositories
sudo apt-get update

# Install the utilities
sudo apt-get install apt-transport-https ca-certificates curl software-properties-common -y
 
# Add the gpg
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -

# Add the repositories
 sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"

# Update the repositories again
 sudo apt-get update

# Docker installation
 sudo apt-get install docker-ce

# Start with the system.
sudo systemctl enable docker

# Add the user to the docker group
# whoami # To know the user name.
sudo usermod -aG docker <result_of_whoami_command>

# Exit from the sesion
exit

# Init docker container again with the user and test.
docker run hello-world
```

##### Debian
``` bash
# Update the repositories
sudo apt-get update

# Install the utilities
sudo apt-get install apt-transport-https ca-certificates curl gnupg2 software-properties-common -y

# Add the gpg 
curl -fsSL https://download.docker.com/linux/debian/gpg | sudo apt-key add -

# Add the repositories
 sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/debian $(lsb_release -cs) stable"

# Update the repositories again
 sudo apt-get update

# Docker installation
 sudo apt-get install docker-ce

# Start with the system.
sudo systemctl enable docker

# Add the user to the docker group
# whoami # To know the user name.
sudo usermod -aG docker <result_of_whoami_command>

# Exit from the sesion
exit

# Init docker container again with the user and test.
docker run hello-world
```

#### Jenkins Installation (Docker image)
1. Current link for docker jenkins: https://hub.docker.com/r/jenkins/jenkins/
2. Execute command: `docker pull jenkins/jenkins`, read the oficial documentation for more information.
3. Verify with: `docker images`
4. Create a folder where we will save some jenkins information.
5. Give it some permissions to the folder: `chown 1000 jenkins`
6. Create a `docker-compose.yml` file inside jenkins folder.
``` yaml
# docker-compose.yml for linux
version: '3'
services:
  jenkins:
    container_name: jenkins
      image: jenkins/jenkins
      ports:
        - "9555:8080"
      volumes:
        - $PWD/jenkins_home:/var/jenkins_home
      networks:
        - jenkins_net
networks:
  - jenkins_net
```

``` yaml
# docker-compose.yml for windows version 1
version: '3'
services:
  jenkins:
    container_name: jenkins
    image: jenkins/jenkins
    ports:
      - "5001:8080"
    volumes:
      - //d/LEARNING/DevOps/jenkins/jenkins_home:/var/jenkins_home
    networks:
      - net
networks:
  net:
```

``` yaml
# docker-compose.yml for windows version 2
version: '3'
services:
  jenkins:
    container_name: jenkins
    image: jenkins/jenkins
    ports:
      - "5001:8080"
    volumes:
      - jenkinsdata:/var/jenkins_home
    networks:
      - net
networks:
  net:
volumes:
  jenkinsdata:
```
7. Then execute the following command: `docker-compose up -d`
8. We can see the image running with: `docker ps`
9. If we want to see what docker has executed: `docker logs -f`
10. Go to `localhost:<specified_port>` for accessing to docker.
11. `cat jenkins_home/secrets/initialAdminPassword`. Copy and paste as initial password. So another option is access to the image with: Ubuntu: `docker exec -it jenkins bash` and Windows: `winpty docker exec -it jenkins bash`, then `cat /var/jenkins_home/secrets/initialAdminPassword`
12. We can install suggested plugins as initial operation.
13. Just follow all the steps until complete the process.

#### Jinkins first steps
Basically Jenkins is for executing some tasks in remote machines. So for that we can create some tasks.

###### Execute an script with our first job.
1. Create the scrip file
```bash
#!/bin/bash

NOMBRE=$1
APELLIDO=$2
MOSTRAR=$3

if [ "$MOSTRAR" = "true" ]; then
	echo "Hola, $NOMBRE, $APELLIDO"
else
	echo "Si quieres ver el nombre, selecciona la casilla de MOSTRAR"
fi
```
2. Set perssions: `chmod +x script.sh`
3. copy the script to the container with: `docker cp script.sh <container-name>:/opt` in this case: `docker cp script.sh jenkins:/opt`
4. Go to jenkins dashboard and create a `Job -> Build -> Execute Shell`
5. Add the reference to the script file as follows.
```bash
NOMBRE=MyName
APELLIDO=MyLastName
MOSTRAR=true

/opt/script.sh $NOMBRE $APELLIDO $MOSTRAR
```
6. Another option is to add the parameters in jenkins, and then use them in the script. Which means without defining the parameters in the script text field.
```bash
/opt/script.sh $NOMBRE $APELLIDO $MOSTRAR
```

#### Docker & Jenkins SSH
1. First create a folder(in this case with name centos8), then create a Dockerfile in it with the following content.
``` bash
# First Part
FROM centos
RUN yum -y install openssh-server
RUN useradd remote_user && \
    echo "123456" | passwd remote_user --stdin && \
	mkdir /home/remote_user/.ssh && \
	chmod 700 /home/remote_user/.ssh
```

2. We will need a SSH key. So then we need to generate it.
``` bash
# Command: ssh-keygen -f <some-name>
ssh-keygen -f remote-key
ls
# We will need to copy the file .pub into the container, with this key the jenkins will able to communicate with the remote server.
```

3. Continue working on Dockerfile
``` bash
# Second Part
FROM centos
RUN yum -y install openssh-server
RUN useradd remote_user && \
    echo "123456" | passwd remote_user --stdin && \
	mkdir /home/remote_user/.ssh && \
	chmod 700 /home/remote_user/.ssh
COPY remote-key.pub /home/remote_user/.ssh/authorized_keys
RUN chown remote_user:remote_user -R /home/remote_user && \
	chmod 600 /home/remote_user/.ssh/authorized_keys
RUN /usr/sbin/sshd-keygen > /dev/null 2>&1
CMD /usr/sbin/sshd -D	
```

Previous scripts does not work with the latest centos version, but it does if we specifically execute centos7 as follows:
```bash
FROM centos:7

RUN yum -y install openssh-server

RUN useradd remote_user && \
    echo "123456" | passwd remote_user --stdin && \
	mkdir /home/remote_user/.ssh && \
	chmod 700 /home/remote_user/.ssh
	
COPY remote-key.pub /home/remote_user/.ssh/authorized_keys

RUN chown remote_user:remote_user   -R /home/remote_user && \
    chmod 600 /home/remote_user/.ssh/authorized_keys

RUN /usr/sbin/sshd-keygen > /dev/null 2>&1

CMD /usr/sbin/sshd -D
```

4. Create the docker compose which will contain Jenkins and remote host images.
``` bash
# docker-compose.yml in linux
version: '3'
services:
  jenkins:
    container_name: jenkins
    image: jenkins/jenkins
    ports:
      - "8080:8080"
    volumes:
      - $PWD/jenkins_home:/var/jenkins_home
    networks:
      - net
  remote_host:
    container_name: remote-host
    image: remote-host
    build:
      context: centos8 #cento8 is the folder in which we have the dockerfile for centos.
    networks:
      - net
networks:
  net:
```

``` bash
# docker-compose.yml in windows
version: '3'
services:
  jenkins:
    container_name: jenkins
    image: jenkins/jenkins
    ports:
      - "8080:8080"
    volumes:
      - $PWD/jenkins_home:/var/jenkins_home
    networks:
      - net
  remote_host:
    container_name: remote-host
    image: remote-host
    build:
      context: centos8 #cento8 is the folder in which we have the dockerfile for centos.
    networks:
      - net
networks:
  net:
volumes:
  jenkinsdata:
```

5. Once the docker-compose file is created we need to execute the following:
``` bash
docker-compose build # For recreating the container that was already created.

docker-compose up -d 

docker ps

# Verify if jenkins has connection to remote-host
docker exec -it  jenkins bash # Starting jenkins container.
ping remote_host # This command should work
ssh remote_user@remote_host # Trying to connect from jenkins to remote-server

# Now trying to connect from jenkins to remote-server with ssh key.
docker cp remote-key jenkins:/tmp # Copying the ssh key into the jenkins container
docker exec -it jenkins bash # Here we can verify if the ssh is copied.
ssh -i remote-key remote_user@remote_host # It will be connected to remote-server

# Only as a note: the following command is executed for removing the container
docker rm -fv remote-host
```

##### Install plugins in Jenkins (SSH Plugin)
1. Go to the main dashboard
2. `Manage Jenkins -> Manage Plugins`
3. Go to `all plugins` tab, and look for `ssh` plugin.
4. Click in the required plugin and install it. Then restart jenkins.
5. `Manage Jenkins -> Manage Plugins -> Installed` then verify if the previous plugin has been installed.

##### Integrate jenkins with remote-server
1. `Manage Jenkins -> System configuration`
2. Then look for `ssh remote hosts` section.
3. Then fill all the required fields there. We may need to add the credentials first in CREDENTIALS menu.
4. During the creation of the credentials, we will need to add the remote-key content into the jenkins.
5. Then after test the connection, it should be successful.
6. After that we can create the jobs that will be executed in the remote-server.




















