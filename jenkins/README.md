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

#### Docker & Jenkins SSH
1. First create a folder, then create a Dockerfile in it with the following content.
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

4. Create the docker compose which will contain Jenkins and remote host images.
``` bash
# docker-compose.yml
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
      context: centos7 #cento7 is the folder in which we have the dockerfile for centos.
    networks:
      - net
networks:
  net:
```

5. Once the docker-compose file is created we need to execute the following:
``` bash
docker-compose build

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




















