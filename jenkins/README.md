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

# Install docker compose
# Step 1
$which docker-compose
/usr/bin/docker-compose

# Step 2
$sudo rm /usr/bin/docker-compose
curl -L https://github.com/docker/compose/releases/download/1.24.0/docker-compose-`uname -s`-`uname -m` > ~/docker-compose

# Step 3
chmod +x ~/docker-compose
sudo mv ~/docker-compose /usr/local/bin/docker-compose
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
      - ${PWD}/jenkins_home:/var/jenkins_home
    networks:
      - jenkins_net
networks:
  jenkins_net:
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
      - jenkinsdata:/var/jenkins_home
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
ssh remote_user@remote_host # Trying to connect from jenkins to remote-server, but it will ask the remote_host password.

# Now trying to connect from jenkins to remote-server with ssh key.
docker cp remote-key jenkins:/tmp # Copying the ssh key into the jenkins container
docker exec -it jenkins bash # Here we can verify if the ssh is copied.
ssh -i remote-key remote_user@remote_host # It will be connected to remote-server

# Only as a note: the following command is executed for removing the container
docker rm -fv remote-host
```

###### Install plugins in Jenkins (SSH Plugin)
1. Go to the main dashboard
2. `Manage Jenkins -> Manage Plugins`
3. Go to `all plugins` tab, and look for `ssh` plugin.
4. Click in the required plugin and install it. Then restart jenkins.
5. `Manage Jenkins -> Manage Plugins -> Installed` then verify if the previous plugin has been installed.

###### Integrate jenkins with remote-server
1. `Manage Jenkins -> System configuration`
2. Then look for `ssh remote hosts` section.
3. Then fill all the required fields there. We may need to add the credentials first in CREDENTIALS menu.
4. During the creation of the credentials, we will need to add the remote-key content into the jenkins.
5. Then after test the connection, it should be successful.
6. After that we can create the jobs that will be executed in the remote-server.

Here some notes regarding to some issues.
Looks like you're using keyfile authentication, so you'll get this error from Jenkins if you haven't set the permissions correctly on your `.ssh` folder and/or `~/.ssh/authorized_keys` file.

- the `.ssh` folder should have `drwx------` permissions (read/write/execute owner only)
- the `authorized_keys` file should have `-rw-------` permissions (read/write owner only)

To fix it:
- `chmod 700 ~/.ssh`
- `chmod 600 ~/.ssh/authorized_keys`

#### Docker & AWS
##### Create a MySQL container
1. First we will edit our docker-compose.yml file
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
      - ${PWD}/jenkins_home:/var/jenkins_home
    networks:
      - net
  remote_host:
    container_name: remote-host
    image: remote-host
    build:
      context: centos8 #cento8 is the folder in which we have the dockerfile for centos.
    networks:
      - net
  mysql_host:
    container_name: mysql-db
    image: mysql:5.7
    environment:
      - "MYSQL_ROOT_PASSWORD=123456"
    volumes:
      - ${PWD}/db_data:/var/lib/mysql
    networks:
      - net
networks:
  net:
```
2. Once the new docker container with mysql image has been created, we can verify following these commands:
``` bash
# Access to the mysql container
docker exec -it mysql-db bash

# Login to mysql database
mysql -u root -p

# Then we can create databases, tables, insert information to them, etc.
```
##### Connecting to AWS
###### Installing MySQL Client and AWS CLI to Remote-Host
1. Update the docker file.
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

RUN yum -y install mysql

RUN yum -y install epel-release && \
    yum -y install python-pip && \
    pip install --upgrade pip && \
    pip install awscli

CMD /usr/sbin/sshd -D
```
2. Once updated the docker file, we will need to execute `docker-compose build` command for updating our containers.
3. We may get an error message to upgrade pip version. So we can add a command to Dockerfile for upgrading in the Container. `Add the new command after python-pip`
4. Then recreate the remote_host `docker-compose up -d`
5. Verify if phyton pip is installed.
6. Once `mysql client` and `aws cli` are installed, then we can connect from `remote_host` to the `mysql_host`.
```bash
# Connecting to the remote machine
mysql -u root -h mysql_host -p

show databases;
create database testdb;
use testdb;
create table info (name varchar(20), lastname varchar(20), age int(2));
desc info;
insert into info values('UserA', 'LastNameA', 21);
```
###### Configuring AWS
1. Create a bucket with default configuration.
2. Create a new user which is going to have a `programatic access` and with permissions to `Amazon S3: Amazon S3 Full Acess`.
3. Once a new user is created, we will able to download a `csv file` with the credentials that we will require for accessing to S3.

###### Take MySQL backup and store it to S3
1. Manually we can follow the following steps:
``` bash
# Access to the container
docker exec -it remote-host bash

# Create the backup
mysqldump -u root -h mysql_host -p<mypassword> <databasename> > /tmp/db.sql

# Add required environment variables for AWS
export AWS_ACCESS_KEY_ID=<AccessKeyID>
export AWS_SECRET_ACCESS_KEY=<SecretAcessKey>

# Copy backup to S3
aws s3 cp <my-backup-path> s3://<my-bucket-name>
```
2. Create a script for performing the previous process automatically.
``` bash
# The backup will be uploaded to amazon from the remote-host
docker exec -it remote-host bash

# Create the script
vi /tmp/script.sh

# Script content
#!/bin/bash
DATE=$(date +%H-%M-%S)
DB_HOST=$1
DB_PASSWORD=$2
DB_NAME=$3
AWS_SECRET=$4
BUCKET_NAME=$5
mysqldump -u root -h $DB_HOST -p$DB_PASSWORD $DB_NAME > /tmp/mysqldb-$DATE.sql && \
export AWS_ACCESS_KEY_ID=<AccessKeyID> && \
export AWS_SECRET_ACCESS_KEY=$AWS_SECRET && \
aws s3 cp /tmp/mysqldb-$DATE.sql s3://$BUCKET_NAME
```
3. Once everything is configure, we will need to create the secrets in jenkins.
4. We will need to give some permissions to the script file stored in the `remote-host` container: `chmod +x /tmp/script.sh`
5. Create a new job in jenkins, and then add the required parameters to this. In this case not sensitive information like DB_HOST, DB_NAME and BUCKET_NAME.
6. For sensitive information in jenkins check `use secret text(s) or file(s)` in `Build Environment` section. Add them by `Secret Text` option.
7. Add the required command in `Build` section: `/tmp/script.sh <list of parameters>`

###### Make the Script permanent in remote-host
1. Add a new volume for remote-host
```bash
version: '3'
services:
  jenkins:
    container_name: jenkins
    image: jenkins/jenkins
    ports:
      - "8080:8080"
    volumes:
      - ${PWD}/jenkins_home:/var/jenkins_home
    networks:
      - jnet
  remote_host:
    container_name: remote-host
    image: remote-host
    build:
      context: centos7
    volumes:
      - ${PWD}/centos7/dbscript.sh:/tmp/dbscript.sh
    networks:
      - jnet
  mysql_host:
    container_name: mysql-db
    image: mysql:5.7
    environment:
      - "MYSQL_ROOT_PASSWORD=123456"
    volumes:
      - ${PWD}/db_data:/var/lib/mysql
    networks:
      - jnet
networks:
  jnet:
```
2. Give permissions to the script: `chmod +x scriptfile`

#### Jenkins Tips & Tricks
##### Available Environment Variables
- Look for JENKINS ENVIRONMENT VARIABLES
- Go to section: JENKINS SET ENVIRONMENT VARIABLES.
- We can use them directly.

##### Create our own environment variables.
- We can define it in: `Manage jenkins -> System Configuration -> Environment Variables`

##### Change Jenkins URL
- `Manage jenkins -> System Configuration -> Jenkins Location`

##### Trigger jobs with CRON
- Go to the JOB
- Go to the settings `execution trigger -> execute periodically`
- Then add the settings based on CRON syntax: See CronTab https://crontab.guru
  - Example: `0 3 * * *` But jenkins will show us an warning message which says that onother jobs may be scheduled at the same time, So adding H instead of 0 will fix it. Because it means that during 60 minutos, jenkins will see which time is the best momento to execute the job.
  
##### Create a user with permissions for executing a JOB.
- Go to the console where we can manage the roles.
- Give it read and write to the TASKS
- Create the user and assign the role.

##### Trigger jobs with CURL
1. Without Parameters

It will be required to have a script file: e.g. `crumb.sh`
```bash
crumb=$(curl -u "jenkins:1234" -s 'http://jenkins.local:8080/crumbIssuer/api/xml?xpath=concat(//crumbRequestField,":",//crumb)')

curl -u "jenkins:1234" -H "$crumb" -X POST http://jenkins.local:8080/job/ansible-job2/build

# Obviusly we will need to execute our jobs. Above is only an example.
```
We will need to execute the previous script.

2. With Parameters.
If we want to execute the jobs using CURL with parameters, we will need to execute the following:
```bash
curl -u "jenkins:1234" -H "$crumb" -X POST http://jenkins.local:8080/job/ansible-job2/buildWithParameters?key=value&key=value
```

#### Jenkins & Email
###### With AWS
1. We need to install a plugin `mailer`
2. Go to `Manage Jenkins -> System Configuration -> Notification by Email (SMTP)`
3. For this we need an email server/service. If we do not have one, we can use the one that AWS provides us like SES.
  - Use the `Server Name` that we can see there in `SMTP Settings` section.
  - We will need to use the SMTP credentials there. It will create a IAM user only for email operations.
  - The credentials can be downloaded in the csv file.
  - We will need to use one of the ports available for SMTP in AWS.

###### With GMAIL
1. Look for smtp gmail settings. So we will use it in our jenkins configuration
  - smtp.gmail.com
2. But it may not work, we will need to look for: LET LESS SECURE APPS ACCESS YOUR ACCOUNT (aplicaciones menos seguras gmail)
3. Just enable it.

###### Integrate email notification to our jobs
- We will only need to add a new task `email notification` as a `Post Action` of the job.

#### Jenkins & Git
- First look for `gitlab ce docker`
- Update our docker compose based on the previous result from https://docs.gitlab.com/omnibus/docker/
```bash
# docker-compose for linux
version: '3'
services:
  jenkins:
    container_name: jenkins
    image: jenkins/jenkins
    ports:
      - "8080:8080"
    volumes:
      - ${PWD}/jenkins_home:/var/jenkins_home
    networks:
      - jnet
  remote_host:
    container_name: remote-host
    image: remote-host
    build:
      context: centos7
    volumes:
      - ${PWD}/centos7/dbscript.sh:/tmp/dbscript.sh
    networks:
      - jnet
  mysql_host:
    container_name: mysql-db
    image: mysql:5.7
    environment:
      - "MYSQL_ROOT_PASSWORD=123456"
    volumes:
      - ${PWD}/db_data:/var/lib/mysql
    networks:
      - jnet
  gitlab_server:
    container_name: git-server
    hostname: gitlab.example.com
    ports:
      - "443:443"
      - "80:80"
    restart: always
    volumes:
      - /srv/gitlab/config:/etc/gitlab
      - /srv/gitlab/logs:/var/log/gitlab
      - /srv/gitlab/data:/var/opt/gitlab
    image: gitlab/gitlab-ce
    networks:
      - jnet
networks:
  jnet:
```

```bash
# docker-compose for windows
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
  remote_host:
    container_name: remote-host
    image: remote-host
    build:
      context: centos8
    networks:
      - net 
  gitlab_server:
    container_name: git-server
    hostname: gitlab.example.com
    ports:
      - "443:443"
      - "80:80"
    restart: always
    volumes:
      - jenkinsdata:/etc/gitlab
      - jenkinsdata:/var/log/gitlab
      - jenkinsdata:/var/opt/gitlab
    image: gitlab/gitlab-ce
    networks:
      - net
networks:
  net:
volumes:
  jenkinsdata:
```
- Then execute the command `docker-compose up -d`

##### Create a Repository in GitLab
- Gitlab is going to take a little long to start, once it is ready, we will need to change the password (minimum characters 8).
- Once changed the password, we can login in it with `roor` user and the password changed previously.
- Since our hostname is gitlab.example.com, we will need to expose it as it is defined. So for that we well need to update our hosts file like:

```bash
sudo vi /etc/hosts
<my-ip> gitlab.example.com
```
Then we can access to it through the specified name.
- Then we will need to create a `group` in which we are going to save our projects: `jenkinsci`
- After that create a new project: `maven`
- After that we will able to integrate it with our jenkins server.

After all previous steps:
- We will need to create a user which can be used by our Jenkins Server. This user will also need to have a 8 long password.
- We will need to give the new user access to the project that we created previously.
- Clone our repository, and create a java app in it.
- 

##### Git Hooks
- Events when something happens.
- Let's enter to the jenkins server machine and verify perform the following commands.
```bash
docker exec -it jenkins bash
cd /var/opt/gitlab/git-data/repositories/jenkinsci/maven.git
mkdir custom_hooks
vi post-receive
```

File.
```bash
#!/bin/bash


# Get branch name from ref head

if ! [ -t 0 ]; then
  read -a ref
fi
IFS='/' read -ra REF <<< "${ref[2]}"
branch="${REF[2]}"

if [ $branch == "master" ]; then
crumb=$(curl -u "jenkins:1234" -s 'http://jenkins:8080/crumbIssuer/api/xml?xpath=concat(//crumbRequestField,":",//crumb)')
curl -u "jenkins:1234" -H "$crumb" -X POST http://jenkins:8080/job/maven/build?delay=0sec

  if [ $? -eq 0 ] ; then
    echo "*** Ok"
  else
    echo "*** Error"
  fi
fi
```

Giving access to the script. This is going to be execute everytime some changes are added into the master branch.
```bash
chmod +x post-receive
cd ..
chown git:git custom_hooks/ -R
```
#### Jenkins & DSL
- It is a plugin for creating jobs automatically. First, we will need to install it. Look for `jenkins dsl`

1. We will create a new job. This is going to be a parent job.
2. Once the Job is created go to `build -> process Job DSLs`
3. For this, we will have two approaches for it. 
  - First using a file
  - Second adding the required commands into the text box.

Second approach example:
1. We need to look for jenkins + dsl for having more details about this plugin.
2. We need the following piece of code for creating a new job.
```bash
job('job_dsl_example') {

}
```
3. Once saved the previous piece of code, and then execute the build. It will create a new job with the name specified in the code. In this case `job_dsl_example`
4. Piece of code for adding a description in the job created automatically.
```bash
job('job_dsl_example') {

    description('This is my awesome Job')
}

```
5. For specifying parameter, we need the following.
```bash
job('job_dsl_example') {

    description('This is my awesome Job')
    
    parameters {
        stringParam('Planet', defaultValue = 'world', description = 'This is the world')
	booleanParam('FLAG', true)
        choiceParam('OPTION', ['option 1 (default)', 'option 2', 'option 3'])
    }

}
```
6. Source Control Management with DSL.
```bash
job('job_dsl_example') {

    description('This is my awesome Job')

    parameters {
        stringParam('Planet', defaultValue = 'world', description = 'This is the world')
	booleanParam('FLAG', true)
        choiceParam('OPTION', ['option 1 (default)', 'option 2', 'option 3'])
    }

    scm {
        git('https://github.com/jenkins-docs/simple-java-maven-app', 'master')
    }
}

```
7. DSL triggers. We know that the triggers are managed by `cron`
```bash
job('job_dsl_example') {

    description('This is my awesome Job')
  
    parameters {
        stringParam('Planet', defaultValue = 'world', description = 'This is the world')
	booleanParam('FLAG', true)
        choiceParam('OPTION', ['option 1 (default)', 'option 2', 'option 3'])
    }

    scm {
        git('https://github.com/jenkins-docs/simple-java-maven-app', 'master')
    }

    triggers {
        cron('H 5 * * 7')
    }
}
```
8. Steps and Jenkins DSL.
```bash
job('job_dsl_example') {

    description('This is my awesome Job')

    parameters {
        stringParam('Planet', defaultValue = 'world', description = 'This is the world')
	booleanParam('FLAG', true)
        choiceParam('OPTION', ['option 1 (default)', 'option 2', 'option 3'])
    }

    scm {
        git('https://github.com/jenkins-docs/simple-java-maven-app', 'master')
    }

    triggers {
        cron('H 5 * * 7')
    }

    steps {
        shell("echo 'Hello World'")
    }
}
```
9. Jenkins DSL and Post Steps (Mailer)
```bash
job('job_dsl_example') {

    description('This is my awesome Job')
  
    parameters {
        stringParam('Planet', defaultValue = 'world', description = 'This is the world')
	booleanParam('FLAG', true)
        choiceParam('OPTION', ['option 1 (default)', 'option 2', 'option 3'])
    }

    scm {
        git('https://github.com/jenkins-docs/simple-java-maven-app', 'master')
    }

    triggers {
        cron('H 5 * * 7')
    }

    steps {
        shell("echo 'Hello World'")
        shell("echo 'Hello World2'")
    }

    publishers {
        mailer('me@example.com', true, true)
    }
}
```
10. Jenkins DSL and Ansible
```bash
job('job_dsl_example') {

    description('This is my awesome Job')
  
    parameters {
        stringParam('Planet', defaultValue = 'world', description = 'This is the world')
	booleanParam('FLAG', true)
        choiceParam('OPTION', ['option 1 (default)', 'option 2', 'option 3'])
    }

    scm {
        git('https://github.com/jenkins-docs/simple-java-maven-app', 'master')
    }

    triggers {
        cron('H 5 * * 7')
    }

    steps {

        wrappers {
            colorizeOutput(colorMap = 'xterm')
      }
        ansiblePlaybook('/etc/ansible/plays/i2b-cl/some_playbook.yml') {
            inventoryPath('/etc/ansible/plays/i2b-cl/hosts')
            tags('cool')
            forks(1)
            colorizedOutput(true)
            additionalParameters('--vault-password-file $HOME/pass-vault/i2b-cl.txt')
            extraVars {
                extraVar("whoami", '${param1}', false)
                extraVar("my_pass", 'some_pass', true)
            }
        }
    }

    publishers {
        mailer('me@example.com', true, true)
    }
}

```
11. If we want to have more than one job created, we can define a new `job` command below the first one.
12. Build Maven Job with DSL.
```bash
job('job_dsl_maven') {

    description('Maven dsl project')

    scm {
        git('https://github.com/jenkins-docs/simple-java-maven-app', 'master', {node -> node / 'extensions' << '' })
    }
  
    steps {
        maven {
            mavenInstallation('jenkins-maven')
            goals('-B -DskipTests clean package')
        }
        maven {
            mavenInstallation('jenkins-maven')
            goals('test')
        }
        shell('''
            echo ************RUNNING THE JAR************************     
            java -jar /var/jenkins_home/workspace/gitlab-maven-job/target/my-app-1.0-SNAPSHOT.jar
        ''')
    }

    publishers {
        archiveArtifacts('target/*.jar')
        archiveJunit('target/surefire-reports/*.xml')
        mailer('franco.robert.fral@gmail.com', true, true)
    }
}
```
Important link to take into account: https://stackoverflow.com/questions/35347269/javax-mail-authenticationfailedexception-535-5-7-8-username-and-password-not-ac, https://www.360logica.com/blog/email-notification-in-jenkins/


#### Jenkins Pipeline - Jenkinsfile
###### First pipeline
1. Let's create a new job but as a jenkins pipeline job.
2. In the pipeline section, we can specify the pipeline commands or take it from a SCM (Like DSL).
```bash
pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building..'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
}

```
###### Multiple steps
3. We can have more than one step in a stage.
```bash
pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                sh 'echo "Este es mi primer pipeline"'
                sh '''
                    echo "Por cierto, puedo ejecutar más acciones aquí"
                    ls -lah
                '''
            }
        }
    }
}
```
###### Retry
4. Means that we can try as much as the value is specified in the parameter.
```bash
pipeline {
    agent any
    stages {
        stage('Timeout') {
            steps {
                retry(3) {
                    sh 'No voy a funcionar :c'
                }
            }
        }
    }
}
```
###### Timeouts
5. When a task takes some time and we need to specify a time for waiting it.
```bash
pipeline {
    agent any
    stages {
        stage('Deploy') {
            steps {
                retry(3) {
                    sh 'echo hola'
                }

                timeout(time: 3, unit: 'SECONDS') {
                    sh 'sleep 5'
                }
            }
        }
    }
}

#########

pipeline {
    agent any
    stages {
        stage('Deploy') {
            steps {
                timeout(time: 2, unit: 'SECONDS') {
                    retry(5) {
                        sh 'sleep 3'
                    }
                }
            }
        }
    }
}
```
###### Post Actions
6. It is the last tasks when the job finishes.
```bash
pipeline {
    agent any
    stages {
        stage('Test') {
            steps {
                sh 'echo "Fail!"; exit 1'
            }
        }
    }
    post {
        always {
            echo 'Siempre me voy a ejecutar :D'
        }
        success {
            echo 'Solo me ejecutaré si el build no falla'
        }
        failure {
            echo 'Solo me ejecutaré si el build falla'
        }
        unstable {
            echo 'Solo me ejecutaré si me marco como inestable'
        }
        changed {
            echo 'El pipeline estaba fallando pero ahora está correcto o visceversa'
        }
    }
}
```
###### Environment Variables
7. Defining enironment variables for the jo.
```bash
pipeline {
    agent any

    environment {
        NOMBRE = 'ricardo'
        APELLIDO    = 'gonzalez'
    }

    stages {
        stage('Build') {
            steps {
                sh 'echo $NOMBRE $APELLIDO'
            }
        }
    }
}
```
###### Credentials
8. We can use the credentials created/defined in previous examples.
```bash
pipeline {
    agent any
    
    environment {
        secretito = credentials('TEST')
    }
    stages {
        stage('Example stage 1') {
            steps {
                sh 'echo $secretito'
            }
        }
    }
}
```

#### Jenkins CI/CD





















