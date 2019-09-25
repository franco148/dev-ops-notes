# AWS CERTIFIED DEVELOPER ASSOCIATE
#### Certification Roadmap

<table>
    <tr>
        <th>AWS Certified</th>
        <th colspan="4">Role - Based Certifications</th>
        <th>Specialty Certifications</th>
    </tr>
    <tr>
        <td>Profesional</td>
        <td></td>
        <td>
          AWS Certified<br>
          <b>Solutions Architect</b><br>
          <i>- Profesional</i>
        </td>
        <td>
          AWS Certified<br>
          <b>DevOps Engineer</b><br>
          <i>- Profesional</i>
        </td>
        <td>
          AWS Certified<br>
          <b>DevOps Engineer</b><br>
          <i>- Profesional</i>
        </td>
        <td>
          AWS Certified<br>
          <b>Advanced Networking</b><br>
          <i>- Specialty</i>
        </td>
    </tr>
    <tr>
        <td>Associate</td>
        <td></td>
        <td>
          AWS Certified<br>
          <b>Solutions Architect</b><br>
          <i>- Associate</i>
        </td>
        <td>
          AWS Certified<br>
          <b>Developer</b><br>
          <i>- Associate</i>
        </td>
        <td>
          AWS Certified<br>
          <b>SysOps Administrator</b><br>
          <i>- Associate</i>
        </td>
        <td>
          AWS Certified<br>
          <b>Big Data</b><br>
          <i>- Specialty</i>
        </td>
    </tr>
    <tr>
        <td>Foundational</td>
        <td>
          AWS Certified<br>
          <b>Cloud Practitioner</b><br>
        </td>
        <td>
          AWS Certified<br>
          <b>Cloud Practitioner</b><br>
          <i>- Optional</i>
        </td>
        <td>
          AWS Certified<br>
          <b>Cloud Practitioner</b><br>
          <i>- Optional</i>
        </td>
        <td>
          AWS Certified<br>
          <b>Cloud Practitioner</b><br>
          <i>- Optional</i>
        </td>
        <td>
          AWS Certified<br>
          <b>Security</b><br>
          <i>- Specialty</i>
        </td>
    </tr>
    <tr>
        <td></td>
        <td>Cloud Practitioner</td>
        <td>Architect</td>
        <td>Developer</td>
        <td>Operations</td>
    </tr>
</table>

#### AWS topics structure
- Amazon EC2
- Amazon ECR
- Amazon ECS
- Amazon Elastic Beanstalk
- AWS Lambda
- Elastic Load Balancing
- Amazon CloudFront
- Amazon Kinesis
- Amazon Route S3
- Amazon S3
- Amazon RDS
- Amazon DynamoDB
- Amazon DynamoDB Accelerator
- Amazon ElastiCache
- Amazon SQS
- Amazon SNS
- AWS Step Functions
- Amazon SWF
- Amazon API Gateway
- Amazon SES
- Amazon Cognito
- IAM
- Amazon CloudWatch
- Amazon EC2 System Manager
- AWS CloudFormation
- AWS CloudTrail
- AWS CodeCommit
- AWS CodeBuild
- AWS CodeDeploy
- AWS CodePipeline
- AWS X-Ray
- AWS KMS


#### AWS Management Console
- Go to our account
- Click on Billing Dashboard
- In left side are a menu: Cost Management -> Budgets Click on it.
- Create a budget
- Cost Budget
- Set budget
- Fill the required fields.
- Spend money would be configured form 0.01 $us
- Click on configure alerts.
- Fill required fields.
- Confirm budget.
- Create.

#### IAM Introduction
- IAM (Identity and Access Management)
- Your whole AWS security is there:
  - Users
  - Groups
  - Roles
- Root account should never be used (and shared)
- Users must be created with proper permissions 
- IAM is at the center of AWS 
- Policies are written in JSON (JavaScript Object Notation): Defines what each of the above can and cannot do.



- IAM has a globalview: It will be across all the regions
- Permissions are governed by Policies (JSON) 
- MFA (Multi Factor Authentication) can be setup 
- IAM has predefined “managed policies” 
- We’ll see IAM policies in details in the future 
- It’s best to give users the minimal amount of permissions they need to perform their job (least privilege principles)


For big enterprises it is used something called:
##### IAM Federation 
- Big enterprises usually integrate their own repository of users with IAM 
- This way, one can login into AWS using their company credentials 
- Identity Federation uses the SAML standard (Active Directory)

##### Summary

- One IAM User per PHYSICAL PERSON: Do not share with anyone, your account is your account!
- One IAM Role per Application 
- IAM credentials should NEVER BE SHARED 
- Never, ever, ever, ever, write IAM credentials in code. EVER. 
- And even less, NEVER EVER EVER COMMIT YOUR IAM credentials 
- Never use the ROOT account except for initial setup. 
- Never use ROOT IAM Credentials

##### IAM Hands-On
1. Go to AWS Console
2. Select IAM in the services dashboard: Remember that this operations are global, it is not specific for a region.
3. Delete your root access keys: Is the first operation that we will need to do (This is going to be performed).
4. Activate MFA rule.
   - Enable to credentials
   - Multi-factor authentication (MAF) sub menu -> Activate MFA
   - (Virtual or Hardware) If it is virtual, we can use an application. Such us google authenticator.
   - We will need to scan a QR code, then fill the fields based on the result of the scan.
   - After filled the fields, press Activate
   - Finish
5. Create individual IAM Users.
   - Manage users
   - Add user -> Fill the user name field -> Select AWS access type
     - In this case selecting both (Programmatic access and AWS Management Console access)
   - Console password
     - The options are: Autogenerated password or Custom Password.
   - Require password reset
     - Checked in this case.
   - Next (Set Permission)
   - In this case selecting ```Attach existing policies directly```
     - Giving in this case ```Administrator Access```
   - Set Permissions boundary
     - Create user without a permissions boundary (in this case)
   - Next (Review)
   - Create User
   - Close.
6. Manage groups
   - Create a new group
     - For this scenario named it ```admin```
   - Next step
     - Administrator Access
   - Next step
   - Create group
   - Go to the created group
   - User Tab -> Add Users to Group -> Add the user created in previous steps.
   - Go to the user, verify that it has the group, and detach the ```Attached directly``` roles.
7. Apply an IAM password policy
   - Manage password policy
   - Set password policy -> Configure all requerid policies
   - Save changes.

After performed all the steps above, you should see all green status for IAM Management dashboard.

8. In IAM dashboard we can assign an alias to the conection. Press customize link and add a name. So the link is going to change based on the name added. It is going to be used for signIn into our AWS console.

```https://fraldemoacc.signin.aws.amazon.com/console```

#### What is EC2?
- EC2 is one of most popular of AWS offering 
- It mainly consists in the capability of : 
  - Launching virtual machines in the cloud.
  - Renting virtual machines (EC2) 
  - Storing data on virtual drives (EBS) 
  - Distributing load across machines (ELB) 
  - Scaling the services using an auto-scaling group (ASG)
- Knowing EC2 is fundamental to understand how the Cloud works

##### Hands-On: Launching an EC2 Instance running Linux
- We’ll be launching our first virtual server using the AWS Console 
- We’ll get a first high level approach to the various parameters 
- We’ll learn how to start / stop / terminate our instance.

1. Go to AWS console
2. Go to EC2 Service
   - Before continue, make sure that you are in the region that is close to you.
3. Launch Instance: Choose an Amazon Machine Image (AMI)
   - For our case we are going to choose ```Amazon Linux 2 AMI```
4. Select the AMI: Choose an instance type
   - Select t2.micro
   - Then press NEXT: Configure instance details
5. Step 3: Configure Instance Details
   - For this first scenario, leave all fields with their default values.
   - Click NEXT: Add Storage
6. Step 4: Add Storage
   - For this first scenario, leave all fields with their default values.
   - Click NEXT: Add Tags
7. Step 5: Add Tags. 
   - Tags are basically key value pairs which allow you to just identify that Instance and classify it.
   - Example: Name -> FirstInstance
   - It can be added as many tags as required.
   - Click NEXT: Configure Security Group
8. Step 6: Configure Security Group
   - This is going to be basically a firewall for the instance.
   - The following fields are filled.
     - Security group name: ```ec2a-security-group```
     - Description: ```Create with my first EC2 Instance```
   - Click on Review and Lunch
9. Step 7: Review Instance Lunch
   - There is a WARNING message that says: ```Your security group is open to the world```. This needs to be fixed, but for now it is ok.
   - Click on LAUNCH
10. Select an existing key pair or create a new key pair.
    - For now choose create a new key pair
    - Add a key pair name and download it.
    - Then press in LAUNCH INSTANCES
    - Then View Instances

##### How to SSH into your EC2 Instance
###### Linux / Mac OSX

1. We’ll learn how to SSH into your EC2 instance using Linux / Mac 
2. SSH is one of the most important function. It allows you to control a remote machine, all using the command line.

> On the TAB Description we can see some important information regarding to public IPs and DNS. And this is basically how we can connect over the web to our EC2 Instance.
We can also see in `Security Groups` section a `view inbound rules` which shows us the enable ports for this instance.

> We need to follow these steps:
   
   - Open the terminal
   - Execute the following command. `ssh ec2-user@<public-ec2-ip>` where _ec2-user_ is basically the Linux user into our Amazon Linux machine, and _@_ basically defines the IP.
   - But you may get a `Permission Denied` error message. That is because we need to use the key (.pem file)
   - `ssh -i <pem-file> ec2-user@<public-ec2-ip>`
   - At this time I get another error message (exam question): `WARNING: UNPROTECTED PRIVATE KEY FILE!` _Permissions 0644 for 'pem file' are too open_ So basically because the private key is accesible by others it will say bad permissions, and it will not allow you to SSH into that machine.
   - So to fix the previous error: `chmod 0400 <pem-file>`
   - `ssh -i <pem-file> ec2-user@<public-ec2-ip>`
   - So the connection should be success!
   - `whoami` command should show _ec2-user_

3. We will see how we can configure OpenSSH ```~/.ssh/configto``` facilitate the SSH into our EC2 instance

###### Windows

1. We’ll learn how to SSH into your EC2 instance using Windows 
2. SSH is one of the most important function. It allows you to control a remote machine, all using the command line.
3. We will configure all the required parameters necessary for doing SSH on Windows using the free tool Putty.

###### Steps
- Install Putty
- Run putty and go to PuTTygen. Using this tool we are going to convert the key we have downloaded from the EC2 console and we are going to convert it into a format that puTTY likes, which is called PPK.
  - Click on File menu
  - Load private key
  - Select the private key. `It will show a message: Successfully imported foreign key.....`
  - Click on `Save private key`, then choose a location where to save the new ppk file.
  - Click on `Save` and close the generator
- Go to the `programs` menu and choose putty.
  - Enter the IP address of our ec2 machine in the following format: `ec2-user@<ec2-instance-ip>`
  - We can save the session giving it a name, and clicking on `save` button.
  - Click twice in the instance and you may get an error message like: `No supported authentication methods available .....`. It is because we haven't linked our private key file. Close the window.
  - Go to putty again, and load the instance.
  - Go to `connection -> SSH -> Auth -> <Here we can find a field 'private key file for authentication'>`
  - Browser and load the ppk file, but dot not close the window yet!
  - Go to `Session` then save it again selecting the right session name.
  - Double click, and we are inside the machine.
  - exit for closing the connection.

#### Security Groups?
##### Introduction

1. Security Groups are the fundamental of network security in AWS 
2. They control how traffic is allowed into or out of our EC2 Machines.
3. It is the most fundamental skill to learn to troubleshoot networking issues 
4. In this lecture, we’ll learn how to use them to `allow`, `inbound` and `outboundport`

###### Hands-On
- When you are located in a instance, you can click on `Description tab -> security group -> link before inbound rules`
- Or you can navigate in the left menu to `Network & Security -> Security Groups`
- In the security groups we have some tabs `DESCRIPTION | INBOUND | OUTBOUND | TAGS`
  - Under `inbound`: This is all the rules that will allow traffic into our EC2 machine. And by default, there is no rules and we have to add rules.
  - Under `outbound`: By default all traffic is enabled out of the machine. And that means that the machine can communicate everything, everywhere (that is fine by the way).
  - Under `Tags` is if you want to add a name tag, or whatever you want for your EC2 for your security group
- What happens when we delete the default `inbound` rule? So when you try to connect again, while the port 22 is not allowed it will just wait, and wait and wait TIME OUT. That is because we are not allowing nothing in port 22.

##### Deeper Dive

1. Security groups are acting as a “firewall” on EC2 instances 
2. They regulate: 
   - Access to Ports 
   - Authorised IP ranges –IPv4 and IPv6 
   - Control of inbound network (from other to the instance) 
   - Control of outbound network (from the instance to other)

###### Example
<table>
    <tr>
        <th>Type</th>
        <th>Protocol</th>
        <th>Port Range</th>
        <th>Source</th>
        <th>Description</th>
    </tr>
    <tr>
        <td>HTTP</td>
        <td>TCP</td>
        <td>80</td>
        <td>0.0.0.0/0</td>
        <td>Test http page</td>
    </tr>
    <tr>
        <td>SSH</td>
        <td>TCP</td>
        <td>22</td>
        <td>192.149.196.85/32</td>
        <td></td>
    </tr>
    <tr>
        <td>Custom TCP Rule</td>
        <td>TCP</td>
        <td>4567</td>
        <td>0.0.0.0/0</td>
        <td>My App</td>
    </tr>
</table>

###### Good to know

1. Can be attached to multiple instances 
2. Locked down to a region / VPC combination 
3. Does live “outside” the EC2 –if traffic is blocked the EC2 instance won’t see it 
4. _It’s good to maintain one separate security group for SSH access_
5. If your application is not accessible (time out), then it’s a security group issue 
6. If your application gives a “connection refused“ error, then it’s an application error or it’s not launched 
7. All inbound traffic is `blocked` by default 
8. All outbound traffic is `authorised` by default


#### Private vs Public IP (IPv4)

1. Networking has two sorts of IPs. IPv4 and IPv6: 
   - IPv4: 1.160.10.240 
   - IPv6: 3ffe: 1900:4545:3:200:f8ff:fe21:67cf 
2. In my example, I will only be using IPv4. 
3. IPv4 is still the most common format used online. 
4. IPv6 is newer and solves problems for the Internet of Things (IoT).
5. IPv4 allows for 3.7 billion different addresses in the public space 
6. IPv4: [0-255].[0-255].[0-255].[0-255].

##### Fundamental Differences

1. Public IP: 
   - Public IP means the machine can be identified on the internet (WWW) 
   - Must be unique across the whole web (not two machines can have the same public IP). 
   - Can be geo-located easily

2. Private IP: 
   - Private IP means the machine can only be identified on a private network only 
   - The IP must be unique across the private network 
   - BUT two different private networks (two companies) can have the same IPs. 
   - Machines connect to WWW using an internet gateway (a proxy) 
   - Only a specified range of IPs can be used as private I

3. Elastic IPs

1. When you stop and then start an EC2 instance, it can change its public IP. 
2. If you need to have a fixed public IP for your instance, you need an Elastic IP 
3. An Elastic IP is a public IPv4 IP you own as long as you don’t delete it 
4. You can attach it to one instance at a time
5. With an ElasticIPaddress, you can mask the failure of an instance or software by rapidly remapping the address to another instance in your account. 
6. You can only have 5 Elastic IP in your account (you can ask AWS to increase that).
7. Overall, `try to avoid using Elastic IP`: 
   - They often reflect poor architectural decisions 
   - Instead, use a random public IP and register a DNS name to it 
   - Or, as we’ll see later, use a Load Balancer and don’t use a public IP

##### Hands-On

1. By default, your EC2 machine comes with: 
   - A private IP for the internal AWS Network 
   - A public IP, for the WWW. 
2. When we are doing SSH into our EC2 machines: 
   - We can’t use a private IP, because we are not in the same network 
   - We can only use the public IP. 
3. If your machine is stopped and then started, `the public IP can change`

###### Steps
- Connect SSH with the instance.
- So if we use the private IP, nothing happens, because we are not in the same network.
- But if we stop our instance, the IP is lost, and when we start again, the public IP changes.

- We can see also Elastic IPs in the left menu.
  - `Network and Security -> Elastic IPs`
  - Click on `Allocate new address` then `Allocate`. So we get an elastic IP.
- Once allocated a elastic IP, what we can do is right click and associate that address with our instance
  - Right click -> Associate Address -> Fill all the fields -> click on Associate
  - If we go back to our instance, we can find that the IPv4 public IP now is the ALLOCATED ONE.
  - Now if we stop the instance and restart it, the same IP will be associated.
- For removing the Elastic IP
  - Right click on the instance -> Networking -> Disassociate Elastic IP Address -> Yes, disassociate
  - Go to elastic IPs -> Right click -> Release Elastic IP -> Release
  - It is not good idea to have enable it, because if we do not use it we are going to be billed for it.
- Once release the Elastic IP.
  - Next time a new public IP will be assigned to our instance.






















