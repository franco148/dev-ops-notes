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

























