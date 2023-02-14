
# AWS SOLUTIONS ARCHITECH

## INTRODUCTION TO AWS CORE TECHNOLOGIES

### Benefits of Cloud computing
- Agility
- Elasticity
- Cost savings
- Deploy globally in minutes

##### What is cloud computing
Cloud computing is on-demand delivery of compute power, database, storage, applications, 
and other IT resources via the internet with pay-as-you-go pricing.

##### AWS Global Infrastructure
###### Regions (multiple locations)
- Completely isolated from each other
- Certain resources tied to regions
- Each ZA isolated from other AZs within the region
- High-speed, low latency connection between AZs within a region


##### Core Technologies: Compute
- Amazon EC2: Resizable compute capacity
- Amazon EC2 Auto Scaling: Increase or decrease number of instances
- Elastic Load Balancing: Distribute incoming traffic
- Amazon Elastic Container Service: Run applications on a managed cluster
- Amazon Elastic Kubernetes Service: Run Kubernetes applications on AWS and on-premises
- AWS Lambda: Run code in response to events

###### Benefits of Amazon EC2
- Elasticity
- Control
- Flexibility
- Integrated
- Reliable
- Secure
- Cost-effective
- Easy to get started

###### Instance Types
- General purpose: Mac, T2, M6g, A1
- Compute optimized
- Memory optimized
- Accelerated Computing
- Storage optimized

###### Why Scaling Matters - Scaling on AWS
- Launch new instances in advance of peak periods
- Use monitoring to programmatically scale out
- Automatically scale in
- Pay for the resources needed, only when needed

###### Amazon EC2 Auto Scaling group
- Automatically adjusts resource capacity
- Define where Amazon EC2 Auto Scaling deploys resources
- Specify the Amazon VPC and subnets

ASG are configured based on Minimum, Maximum, and desired capacity

###### Amazon Elastic Load Balancing - ELB
- Automatically distribute traffic across multiple EC2 instances
  - Increase availability and fault tolerance
  - Configure health checks
  - Offload encryption and decryption
- Types:
  - Application Load Balancer (app layer)
  - Network Load Balancer (network layer)
  - Gateway Load Balancer (third-party virtual appliances)

##### Core Technologies: Storage
A reliable, scalable, and secure place for data
- Amazon Elastic Block Store: Persistent block-level storage
- Amazon S3: Durable scalable object storage
- Amazon S3 Glacier: Data archiving and backup
- AWS Storage Gateway: Integrate cloud storage with on-site workloads
- Amazon Elastic File System: File storage for Amazon EC2 instances
- Amazon FSx: File storage for widely-used file systems.

###### Amazon Elastic Block Store (EBS)
Network-attached block storage for use with Amazon EC2 instances.
- Persist independently from instance
- Used like a physical hard drive
- Automatically replicated
- Attached to any instance in the same AZ
- One EBS volume to one EC2 instance
- One instance to many EBS volumes
- EBS volumes can retain data after EC2 instance termination.
- Allow point-in-time snapshots to S3 GiB increments

###### Amazon Simple Storage Service (Amazon S3)
- Infinite scalability, greater analysis, and faster data retrieval
- Highly scalable object storage with 99.9999% durabilitdy and 99.99% availability
- Comon S3 use cases:
  - Data lakes
  - Backup and storage
  - Application hosting
  - Media hosting
  - Software delivery
  
###### Storage classes on Amazon S3
- Amazon S3 Standard
- Amazon S3 Standard-Infrequent Access
- Amazon S3 One Zone-Infrequent Access
- S3 Glacier storage classes
- S3 Intelligent-Tiering automatically moves objects between tiers based on access patterns.
 
##### Core Technologies: Databases
Purpose-build for specific application use cases
Offload time-consuming management tasks

- Amazon RDS: Cost-efficient and resizable capacity. Incluses 6 popular database engines like: Amazon Aurora, Postgresql, mysql, mariadb, oracle, sql server
- Amazon DynamoDB: A no SQL database, fast and predictable performance. 
- Amazon ElastiCache: A cache service. Fast, managed information retrieval.

###### EC2-hosted vs AWS Database Services
- AWS Database Service
  - Easy to set up, manage, maintain
  - Reduce undifferentiated heavy lifting
  - Push-button high availability
  - Automatic backup/recovery
  - Scale up or down based upon pattern
- Databases on Amazon EC2
  - More control/flexibility
  - Operating system access
  - Need features of specific application

##### Core Technologies: Networking
Isolate cloud infrastructure and scale request-handling capacity
- Amazon VPC: Build a virtual network in the cloud
- Security Groups: Control access to instances
- Network Access Control Lists (NACL): Controls access to subnets
- Amazon Route 53: Route end users to internet applications

###### Amazon Virtual Private Cloud (VPC)

Amazon Virtual Private Cloud (VPC)
- Networking layer for AWS resources
- A virtual network dedicated to a customer's AWS account

Subnet
- A range of IP addresses in a VPC

Securing a VPC
- Network Access Control Lists: control traffic at the subnet level
- Security Groups: control traffic at the instance level
- Flow logs: Capture network flow information
- Host-based firewalls: Operating system firewalls

##### Core Technologies: Security
Cloud security at AWS is the highest priority
- Inherit benefits from AWS data center and network architecture
- Similar to on premises data centers, without maintaining facilities and hardware
- Can be easily automated
- Inherit all the best practices of AWS

###### Security, identity, and compliance services
- Infrastructure Protection: Inspect and filter traffic to prevent unauthorized resource access at the host, network and application level boundaries
  - AWS Network Firewall
  - AWS Shield
  - AWS WAF
  - AWS Firewall
- Identity & access management: Enables customer's to securily manage identities, resources and permissions, network and application protection services 
  - AWS IAM
  - AWS Single Sign-on
  - AWS Organizations
  - AWS Resource Access Manager
  - AWS Directory Service
  - Amazon Cognito
- Detection: Infrastructure protection, data protection, incidense response and compliance
  - Amazon GuardDuty
  - Amazon Inspector
  - AWS CloudTrail
  - AWS Security Hub
  - AWS Config
  - AWS IoT Device Defender
- Data Protection: AWS provides services to protect data, accounts, and workloads from unauthorized access. Provides encryption, key management and thread detection. 
  - Amazon Macie
  - AWS CloudHSM
  - AWS Secrets Manager
  - AWS KMS
  - AWS Certificate Manager
- Compliance: 
  - AWS Artifact
  - AWS Audit Manager 
- Incident Response
  - Amazon Detective
  - CloudEndure Disaster Recovery

###### Amazon Identity and Access Management (IAM)
Securely manage access to AWS services and resources
- Fine-grained access control to AWS resources
- Multi-factor authentication
- The ability to analyze access
- Integration with corporate directories

###### AWS Cloud compliance
- Sharing information
  - Industry certifications
  - Security and control practices
  - Compliance reports directly under NDA
- Assurance Programs
  - Certifications and attestations
  - Laws, regulations, and privacy
  - Alignments and frameworks

##### Summary
- AWS management interfaces
  - AWS Management Console: Graphical web interface to facilitate cloud management
  - Command Line Interfaces (AWS CLI): Access to services via commands
  - Software Development Kits (SDKs): Access services in your code.


##### Knowledge Check and Resources
- Availability Zone: Separate geographical area within an AWS Region, designed to facilitate high availability.
- Amazon Elastic Block Store (Amazon EBS): Block storage for Amazon EC2 instances
- Amazon EC2 Auto Scaling: Service maintaining the availabilityof resources by increasing or decreasing capacity
- Security Group: Virtual firewall providing security at the instance level.

###### Resouces:
- What is cloud computing? https://docs.aws.amazon.com/whitepapers/latest/aws-overview/what-is-cloud-computing.html
- Global infrastructure: https://aws.amazon.com/about-aws/global-infrastructure/
- Compute for any workload: https://aws.amazon.com/products/compute/
- Amazon EC2 Instance Types: https://aws.amazon.com/ec2/instance-types/
- Elastic Load Balancing: https://aws.amazon.com/elasticloadbalancing/
- Cloud Storage on AWS: https://aws.amazon.com/products/storage/
- Amazon S3: https://aws.amazon.com/s3/
- Amazon S3 Storage Classes: https://aws.amazon.com/s3/storage-classes
- AWS Cloud Databases: https://aws.amazon.com/products/databases/
- AWS Networking and Content Delivery: https://aws.amazon.com/products/networking/
- Security best practices for you VPC: https://aws.amazon.com/answers/networking/vpc-security-capabilities/
- Security and Compliance: https://docs.aws.amazon.com/whitepapers/latest/aws-overview/security-and-compliance.html
- Security, Identity, and Compliance on AWS: https://aws.amazon.com/products/security/
- Shared Responsability Model: https://aws.amazon.com/compliance/shared-responsibility-model/
- AWS Identity and Access Management (IAM): https://aws.amazon.com/iam/
- AWS Compliance: http://aws.amazon.com/compliance/
- AWS Documentation: https://docs.aws.amazon.com/
- Cloud Products: https://aws.amazon.com/products/





## FROM SERVICES TO SOLUTIONS

### Introduction to Solution Design

##### AWS Solutions
- Machine Learning
- Analytics & Data Lakes
- Internet of Things
- Serverless Computing
- Containers
- Enterprise Applications
- Storage
- Windows workloads

##### Addressing Customer Challenges

##### Migration Strategies
- Rehost (lift and shift): 
  - Recreating the on-premises network, only hosted on AWS
  - Automating with tools such as AWS application migration service
- Replatform
  - It is the same than rehosting where the core architecture doesn't change
  - Retains the core architecture
  - Making targeted AWS cloud optimizations
  - Examples
    - Migrating databases to Amazon RDS
	- Migrating applications to Amazon Elastic Beanstalk
- Relocate (hypervisor-level lift and shift)
  - The same as rehost but at hypervisor level
  - Migration specific to VMWare Cloud on AWS
  - Example:
    - Migrate the hypervisor host
- Refactor (Modernize)
  - Re-imagining how the application is architected and developed
  - Using cloud-native features
- Retire
  - Shutting off non-useful applications
  - Reducing spend, management, and security
- Retain
  - Keeping certain applications on-premises
- Repurchase
  - Moving workflows to software as a service (SaaS)

##### Architectural Best Practices

1. Design for failure and nothing fails
  - Avoid single points of failure
  - Multiple instances
  - Multiple Availability Zones
  - Separate single server into multiple tiered application
  - For Amazon RDS, use Multi-AZ feature
2. Build security in every layer
  - Encrypt data at rest and in transit
  - Enforce principle of least privilege in IAM
  - Implement both Security Groups and Network Access Control Lists (NACL)
  - Consider advanced security features and services
3. Leverage different storage options
  - Move static web assets to Amazon S3
  - Use Amazon CloudFront to serve globally
  - Store session state in DynamoDB
  - User ElasticCache between host and databases
4. Implement elasticity
  - Implement auto scaling policies
  - Architect resiliency to reboot and relaunch
5. Think parallel
  - Scale horizontally, not vertically
  - Decouple compute from session/state
  - Uses Elastic Load Balancer
6. Loose coupling sets you free
  - Instad of a single, ordered workflow, use multiple queues
  - Use Amazon simple queue service
7. Don't fear constraints
  - Rethink traditional constraints
  - Need more RAM?
  - Better IOPS for databases?
  - Response to failure?

- Rightsizing instances
  - Rightsizing is the process of reviewing deployed resources and seeking 
  opportunities to downsize when possible. For example, if an application 
  instance is consistently underutilizing its RAM and CPU, switching that 
  to a smaller instance can offer significant savings while maintaining 
  the same performance.
- Increasing application elasticity
  - An example is using auto scaling to ensure that the correct number of 
  instances are available to handle the workload of an application. Scale 
  out during high demand and scale in during low demand.
- Choosing the right pricing model
  - An example is using Reserved Instances for workloads that need to run 
  most or all the time, such as production environments. This can have a 
  significant impact on savings compared to on-demand; in some cases, up 
  to 75 percent.
Optimizing storage
An example is the S3 Intelligent-Tiering storage class, which is designed to optimize costs by automatically moving data to the most cost-effective storage tier.




##### Resources in this section
- AWS Application Migration Service: https://aws.amazon.com/application-migration-service/
- AWS Well-Architected: https://aws.amazon.com/architecture/well-architected/?wa-lens-whitepapers.sort-by=item.additionalFields.sortDate&wa-lens-whitepapers.sort-order=desc&wa-guidance-whitepapers.sort-by=item.additionalFields.sortDate&wa-guidance-whitepapers.sort-order=desc
- Cloud Economics Center: https://aws.amazon.com/economics/
- AWS Cloud Adoption Framework: https://aws.amazon.com/professional-services/CAF/
- An Overview of the AWS Cloud Adoption Framework: https://d1.awsstatic.com/whitepapers/es_ES/aws-cloud-adoption-framework_XL.pdf
- Customer Success Stories: https://aws.amazon.com/solutions/case-studies/?customer-references-cards.sort-by=item.additionalFields.sortDate&customer-references-cards.sort-order=desc&awsf.content-type=*all&awsf.customer-references-location=*all&awsf.customer-references-segment=*all&awsf.customer-references-industry=*all&awsf.customer-references-use-case=*all&awsf.customer-references-tech-category=*all&awsf.customer-references-product=*all
- AWS Solutions Library: https://aws.amazon.com/solutions/
- AWS Solutions Consulting Offers: https://aws.amazon.com/solutions/consulting-offers/?solutions-consulting-offers-cards.sort-by=item.additionalFields.sortDate&solutions-consulting-offers-cards.sort-order=desc&awsf.solutions-consulting-offers-filter-tech=*all&awsf.solutions-consulting-offers-filter-industry=*all&awsf.solutions-consulting-offers-filter-region=*all
- AWS Quick Starts: https://aws.amazon.com/quickstart/?solutions-all.sort-by=item.additionalFields.sortDate&solutions-all.sort-order=desc&awsf.filter-content-type=*all&awsf.filter-tech-category=*all&awsf.filter-industry=*all




## AWS Tecnical Essentials
#### What is AWS
##### Six advantages of cloud computing
- Pay as you go: Instead of investing in data centers and hardware before you know how you are going to use them, you pay only when you use computing resources, and pay only for how much you use.
- Benefit from massive economies of scale: By using cloud computing, you can achieve a lower cost than you can get on your own. Because usage from hundreds of thousands of customers is aggregated in the cloud, AWS can achieve higher economies of scale, which translates into lower pay as-you-go prices.
- Stop guessing capacity: Eliminate guessing on your infrastructure capacity needs. When you make a capacity decision prior to deploying an application, you often end up either sitting on expensive idle resources or dealing with limited capacity. With cloud computing, these problems go away. You can access as much or as little capacity as you need, and scale up and down as required with only a few minutes notice.
- Increase speed and agility: IT resources are only a click away, which means that you reduce the time to make resources available to your developers from weeks to minutes. This results in a dramatic increase in agility for the organization, since the cost and time it takes to experiment and develop is significantly lower.
- Realize cost savings: Companies can focus on projects that differentiate their business instead of maintaining data centers. Cloud computing lets you focus on your customers, rather than on the heavy lifting of racking, stacking, and powering physical infrastructure. This is often referred to as undifferentiated heavy lifting.
- Go global in minutes: Applications can be deployed in multiple Regions around the world with a few clicks. This means that you can provide lower latency and a better experience for your customers at a minimal cost.

##### Resources
- https://aws.amazon.com/what-is-cloud-computing/
- http://docs.aws.amazon.com/whitepapers/latest/aws-overview/types-of-cloud-computing.html
- https://aws.amazon.com/what-is-aws/
- https://docs.aws.amazon.com/whitepapers/latest/aws-overview/aws-overview.pdf

#### AWS Global Infrastructure
##### AWS Region Considerations
When you decide which AWS Region to host your applications and workloads, consider four main aspects – latency, price, service availability, and compliance.

- Compliance: Enterprise companies often must comply with regulations that require customer data to be stored in a specific geographic territory. If applicable, choose a Region that meets your compliance requirements.
- Latency: If your application is sensitive to latency (the delay between a request for data and the response), choose a Region that is close to your user base. This helps prevent long wait times for your customers. Synchronous applications such as gaming, telephony, WebSockets, and Internet of Things (IoT) are significantly affected by high latency. Asynchronous workloads, such as ecommerce applications, can also suffer from user connectivity delays.
- Pricing: Due to the local economy and the physical nature of operating data centers, prices vary from one Region to another. Internet connectivity, imported equipment costs, customs, real estate, and other factors impact a Region's pricing. Instead of charging a flat rate worldwide, AWS charges based on the financial factors specific to each Region.
- Service availability: Some services might not be available in some Regions. The AWS documentation provides a table that shows the services available in each Region.

##### Infrastructure
Infrastructure, like data centers and networking connectivity, still exists as the foundation of every cloud application. In AWS, this physical infrastructure makes up the AWS Global Infrastructure, in the form of Regions and Availability Zones.

##### Regions
Regions are geographic locations worldwide where AWS hosts its data centers. AWS Regions are named after the location where they reside. For example, in the United States, the Region in Northern Virginia is called the Northern Virginia Region, and the Region in Oregon is called the Oregon Region. AWS has Regions in Asia Pacific, Canada, Europe, the Middle East, and South America, and we continue to expand to meet our customers' needs.

Each AWS Region is associated with a geographical name and a Region code.

AWS Regions are independent from one another. Data is not replicated from one Region to another, without explicit customer consent and authorization.

##### Availability Zones
Inside every Region is a cluster of Availability Zones (AZs). An AZ consists of one or more data centers with redundant power, networking, and connectivity. These data centers operate in discrete facilities in undisclosed locations. They are connected using redundant high-speed and low-latency links.

AZs also have a code name. Since they are located inside Regions, they can be addressed by appending a letter to the end of the Region code name. For example:

us-east-1a: An AZ in us-east-1 (N. Virginia Region)
sa-east-1b: An AZ in sa-east-1 (São Paulo Region)

Therefore, if you see that a resource exists in us-east-1c, you can infer that the resource is located in AZ c of the us-east-1 Region.

##### Scope AWS Services
Depending on the AWS service you use, your resources are either deployed at the AZ, Region, or Global level. Each service is different, so you must understand how the scope of a service might affect your application architecture.

When you operate a Region-scoped service, you only need to select the Region you want to use. If you are not asked to specify an individual AZ to deploy the service in, this is an indicator that the service operates on a Region-scope level. For Region-scoped services, AWS automatically performs actions to increase data durability and availability.

On the other hand, some services ask you to specify an AZ. With these services, you are often responsible for increasing the data durability and high availability of these resources.

##### Maintain Resiliency
To keep your application available, you must maintain high availability and resiliency. A well-known best practice for cloud architecture is to use Region-scoped, managed services. These services come with availability and resiliency built in. When that is not possible, make sure your workload is replicated across multiple AZs. At a minimum, you should use two AZs. That way, if an AZ fails, your application will have infrastructure up and running in a second AZ to take over the traffic.

##### Resources
- https://aws.amazon.com/about-aws/global-infrastructure/
- https://docs.aws.amazon.com/whitepapers/latest/aws-overview/global-infrastructure.html
- https://aws.amazon.com/about-aws/global-infrastructure/regions_az/
- https://docs.aws.amazon.com/general/latest/gr/rande.html
- https://aws.amazon.com/about-aws/global-infrastructure/regional-product-services/


#### Interacting with AWS
Every action you make in AWS is an API call that is authenticated and authorized. In AWS, you can make API calls to services and resources through the AWS Management Console, AWS Command Line Interface (AWS CLI), or AWS software development kits (SDKs).

##### The AWS Management Console
One way to manage cloud resources is through the web-based console, where you log in and choose the desired service. This can be the easiest way to create and manage resources when you first begin working with the cloud. Below is a screenshot that shows the landing page when you first log in to the AWS Management Console. 

The services are placed in categories, such as Compute, Storage, Database, and Analytics

On the upper-right corner is the Region selector. If you choose it and change the Region, you will make requests to the services in the chosen Region. The URL changes, too. Changing the Region setting directs your browser to make requests to a different AWS Region, represented by a different subdomain.

##### The AWS Command Line Interface (AWS CLI)
Consider the scenario where you run tens of servers on AWS for your application’s front end. You want to run a report to collect data from all the servers. You need to do this programmatically every day because the server details might change. Instead of manually logging in to the AWS Management Console and then copying and pasting information, you can schedule an AWS CLI script with an API call to pull this data for you.

The AWS CLI is a unified tool that you can use to manage AWS services. You can download and configure one tool that you can use to control multiple AWS services from the command line and automate them with scripts. The AWS CLI is open-source, and installers are available for Windows, Linux, and macOS.

For example, if you run the following API call against a service using AWS CLI:

`aws ec2 describe-instances`

you will get the following response:

```
{
"Reservations": [
{
"Groups": [],
"Instances": [
{
"AmiLaunchIndex": 0,
```

##### AWS SDKs
API calls to AWS can also be performed by running code with programming languages. You can do this by using AWS software development kits (SDKs). SDKs are open source and maintained by AWS for the most popular programming languages, such as C++, Go, Java, JavaScript, .NET, Node.js, PHP, Python, and Ruby.

Developers commonly use AWS SDKs to integrate their application source code with AWS services. For example, consider an application with a front end that runs in Python. Every time the application receives a cat photo, it uploads the file to a storage service. This action can be achieved in the source code by using the AWS SDK for Python. Here is an example of code you can implement to work with AWS resources using the Python AWS SDK.

```
import boto3
ec2 = boto3.client('ec2')
response = ec2.describe_instances()
print(response)
```

##### Resouces
- https://docs.aws.amazon.com/awsconsolehelpdocs/latest/gsg/getting-started.html
- https://aws.amazon.com/cli/
- https://aws.amazon.com/tools/


#### Security and the AWS Shared Responsability Model
...
...
###### Customers
- Customer Data
- Platform, applications, identity and access management
- Operating Systems, Network and firewall configuration
- Client-side data encryption
- Server-side encryption
- Networking traffic protection
###### AWS
- Software
- Compute
- Storage
- Database
- Networking
- Hardware/AWS Global Infrastructure
- Regions, AZs, Edge locations

##### Resources
- https://aws.amazon.com/compliance/shared-responsibility-model/


#### Protect the AWS Root User
...
...

##### Resouces
- https://docs.aws.amazon.com/IAM/latest/UserGuide/id_credentials_mfa_enable_physical.html
- https://docs.aws.amazon.com/IAM/latest/UserGuide/id_credentials_mfa_enable_u2f.html
- https://docs.aws.amazon.com/IAM/latest/UserGuide/id_credentials_mfa_enable_virtual.html
- https://aws.amazon.com/iam/features/mfa/
- 


#### AWS Identity And Access Management
...
...

##### Resouces
- https://docs.aws.amazon.com/en_us/IAM/latest/UserGuide/introduction.html
- https://docs.aws.amazon.com/en_us/IAM/latest/UserGuide/id.html
- https://docs.aws.amazon.com/en_us/IAM/latest/UserGuide/access.html


#### Role-Based Access in AWS
Throughout these last few lessons, you have learned about some IAM best practices. This section summarizes some of the most important IAM best practices  that you must be familiar with before building solutions in AWS. 

Choose the + sign to read more about each best practice.

- Lock down the AWS root user
The root user is an all-powerful and all-knowing identity in your AWS account. If a malicious user were to gain control of root-user credentials, they would be able to access every resource in your account, including personal and billing information. To lock down the root user, you can do the following:

  - Don’t share the credentials associated with the root user
  - Consider deleting the root user access keys
  - Enable MFA on the root account

- Follow the principle of least privilege
Least privilege is a standard security principle that advises you to grant only the necessary permissions to do a particular job and nothing more. To implement least privilege for access control, start with the minimum set of permissions in an IAM policy and then grant additional permissions as necessary for a user, group, or role.

- User IAM appropriately
IAM is used to secure access to your AWS account and resources. It simply provides a way to create and manage users, groups, and roles to access resources in a single AWS account. IAM is not used for website authentication and authorization, such as providing users of a website with sign-in and sign-up functionality. IAM also does not support security controls for protecting operating systems and networks.

- Use IAM roles when possible
Maintaining roles is more efficient than maintaining users. When you assume a role, IAM dynamically provides temporary credentials that expire after a defined period of time, between 15 minutes and 36 hours. Users, on the other hand, have long-term credentials in the form of user name and password combinations or a set of access keys.

User access keys only expire when you or the account admin rotates the keys. User login credentials expire if you applied a password policy to your account that forces users to rotate their passwords.

- Consider using an identity provider
If you decide to make your cat photo application into a business and begin to have more than a handful of people working on it, consider managing employee identity information through an identity provider (IdP). Using an IdP, whether it's an AWS service such as AWS Single Sign-On or a third-party identity provider, provides a single source of truth for all identities in your organization.

You no longer have to create separate IAM users in AWS. You can instead use IAM roles to provide permissions to identities that are federated from your IdP. For example, you have an employee, Martha, who has access to multiple AWS accounts. Instead of creating and managing multiple IAM users named Martha in each of those AWS accounts, you could manage Martha in your company’s IdP. If Martha moves in the company or leaves the company, Martha can be updated in the IdP, rather than in every AWS account in the company.

- Consider AWS Single Sign-on
If you have an organization that spans many employees and multiple AWS accounts, you might want your employees to sign in with a single credential.

AWS SSO is an IdP that lets your users sign in to a user portal with a single set of credentials. It then provides users access to their assigned accounts and applications in a central location.

Similar to IAM. AWS SSO offers a directory where you can create users, organize them in groups, set permissions across the groups, and grant access to AWS resources. However, AWS SSO has some advantages over IAM. For example, if you’re using a third-party IdP, you can sync your users and groups to AWS SSO. This removes the burden of having to re-create users that already exist elsewhere, and it enables you to manage the users from your IdP. More importantly, AWS SSO separates the duties between your IdP and AWS, ensuring that your cloud access management is not inside or dependent on your IdP.



##### Resouces
- https://docs.aws.amazon.com/IAM/latest/UserGuide/best-practices.html
- https://aws.amazon.com/blogs/security/how-to-create-and-manage-users-within-aws-sso/


### Module 2 - AWS Compute
#### Compute as a Service
The first building block you need to host an application is a server. Servers usually can handle Hypertext Transfer Protocol (HTTP) requests and send responses to clients following the client-server model, although any API-based communication also falls under this model. A client is a person or computer that sends a request. A server handling the requests is a computer, or collection of computers, connected to the internet serving websites to internet users.

Servers power your application by providing CPU, memory, and networking capacity to process users’ requests and transform them into responses. For context, common HTTP servers include:
- Windows options, such as Internet Information Services (IIS)
- Linux options, such as Apache HTTP Web Server, Nginx, and Apache Tomcat

To run an HTTP server on AWS, you must find a service that provides compute power in the AWS Management Console. You can log in to the console and view the complete list of AWS compute services.

###### Choose the right compute options
If you’re responsible for setting up servers on AWS to run your infrastructure, you have many compute options. You need to know which service to use for which use case. At a fundamental level, three types of compute options are available – virtual machines (VMs), container services, and serverless.

If you have prior infrastructure knowledge, a virtual machine is often be the easiest compute option to understand. This is because a virtual machine emulates a physical server and allows you to install an HTTP server to run your applications. To run virtual machines, you install a hypervisor on a host machine. The hypervisor provisions the resources to create and run your VMs.

In AWS, virtual machines are called Amazon Elastic Compute Cloud, or Amazon EC2. Behind the scenes, AWS operates and manages the host machines and the hypervisor layer. AWS also installs the virtual machine operating system, called the guest operating system.

Some AWS compute services use Amazon EC2 or use virtualization concepts under the hood. You should understand this service before advancing to container services and serverless compute.

##### Resouces
- https://docs.aws.amazon.com/whitepapers/latest/aws-overview/compute-services.html
- https://aws.amazon.com/products/compute/
- https://aws.amazon.com/blogs/compute/

#### Amazon Elastic Compute Cloud
When launching an EC2 instance, the first setting you configure is which operating system you want by selecting an Amazon Machine Image (AMI).

###### Amazon Machine Image
In the traditional infrastructure world, the process of spinning up a server consists of installing an operating system from installation disks, installation drives, or installation wizards over the network. In the AWS Cloud, the operating system installation is not your responsibility. Instead, it's built into the AMI that you choose.

In addition, when you use an AMI, you can select storage mappings, the architecture type (such as 32-bit, 64-bit, or 64-bit ARM), and additional software installed.

###### Relationship between AMIs and EC2 instances
EC2 instances are live instantiations of what is defined in an AMI, much like a cake is a live instantiation of a cake recipe. If you are familiar with software development, you can also see this kind of relationship between a class and an object.


##### Resources
- https://aws.amazon.com/ec2/
- https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/AMIs.html
- https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/creating-an-ami-ebs.html
- https://docs.aws.amazon.com/imagebuilder/latest/userguide/what-is-image-builder.html


#### Amazon EC2 Instance Lifecycle
##### Instance families
| Instance Family | Description | Use Cases |
|:----------------|:------------|:----------|
|General purpose  | Provides a balance of compute, memory, and networking resources, and can be used for a variety of workloads. | Scale out workloads, such as web servers, containerized microservices, caching fleets, distributed data stores, and development environments |
| Compute optimized | Ideal for compute-bound applications that benefit from high-performance processors. | High-performance web servers, scientific modeling, batch processing, distributed analytics, high-performance computing (HPC), machine/deep learning, ad serving, highly scalable multiplayer gaming |
| Memory optimized | Designed to deliver fast performance for workloads that process large datasets in memory. | Memory-intensive applications, such as high-performance databases, distributed web-scale in-memory caches, mid-size in-memory databases, real-time big-data analytics, and other enterprise applications |
| Accelerated computing | Use hardware accelerators or co-processors to perform functions such as floating-point number calculations, graphics processing, or data pattern matching more efficiently than is possible with conventional CPUs. | 3D visualizations, graphics-intensive remote workstations, 3D rendering, application streaming, video encoding, and other server-side graphics workloads |
| Storage optimized | Designed for workloads that require high, sequential read and write access to large datasets on local storage. They are optimized to deliver tens of thousands of low-latency random I/O operations per second (IOPS) to applications that replicate their data across different instances. | NoSQL databases, such as Cassandra, MongoDB, and Redis, in-memory databases, scale-out transactional databases, data warehousing, Elasticsearch, and analytics |













































































