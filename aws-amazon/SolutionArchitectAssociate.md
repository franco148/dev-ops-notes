
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

##### EC2 Instance lifecycle
![Alt text](https://res.cloudinary.com/hy4kyit2a/f_auto,fl_lossy,q_70/learn/modules/aws-compute/review-the-amazon-ec2-instance-lifecycle-and-pricing/images/ac1abde05e0c7798246dc6309aede7ee_unit-4-pic-1-instance-lifecycle.png "EC2 Instance Lifecycle")

1. When you launch an instance, it enters the **pending** state. When an instance is pending, billing has not started. At this stage, the instance is preparing to enter the running state. Pending is where AWS performs all actions needed to set up an instance, such as copying the AMI content to the root device and allocating the necessary networking components.
2. When your instance is **running**, it's ready to use. This is also the stage where billing begins. As soon as an instance is running, you can take other actions on the instance, such as reboot, terminate, stop, and stop-hibernate.
3. When you reboot an instance, it’s different than performing a stop action and then a start action. **Rebooting** an instance is equivalent to rebooting an operating system. The instance remains on the same host computer, and maintains its public and private IP address, in addition to any data on its instance store.
4. It typically takes a few minutes for the reboot to complete. When you stop and start an instance, your instance may be placed on a new underlying physical server. Therefore, you lose any data on the instance store that were on the previous host computer. When you stop an instance, the instance gets a new public IP address but maintains the same private IP address. 

##### Pricing
###### Pay as you go with On-Demand Instances
With On-Demand Instances, you pay for compute capacity with no long-term commitments. Billing begins whenever the instance is running, and billing stops when the instance is in a stopped or terminated state. The price per second for a running On-Demand Instance is fixed.

For applications that require servers to be running all the time, you are less likely to benefit from the On-Demand pricing model, simply because there is no situation where you will need to turn servers off. For example, you might want the web server hosting the front end of your corporate directory application to be running 24/7 so that users can access the website at any time. Even if no users are connected to your website, you don’t want to shut down the servers supporting the site in case of potential user activity.

In the case when servers cannot be stopped, consider using a Reserved Instance to save on costs.

###### Reserve capacity with Reserved Instances (RIs)
RIs provide you with a significant discount compared to On-Demand Instance pricing. RIs provide a discounted hourly rate and an optional capacity reservation for EC2 instances. You can choose between three payment options – All Upfront, Partial Upfront, or No Upfront. You can select either a 1-year or 3-year term for each of these options.

Depending on which option you choose, you are discounted differently.

- All Upfront offers a higher discount than Partial Upfront instances.
- Partial Upfront instances offer a higher discount than No Upfront.
- No Upfront offers a higher discount than On-Demand.

On-Demand and No Upfront are similar, since both do not require any upfront payment. However, there is a major difference. When you choose an On-Demand Instance, you stop paying for the instance when you stop or terminate the instance. When you stop an RI, you still pay for it because you committed to a 1-year or 3-year term.

Reserved Instances are associated with an instance type and an Availability Zone depending on how you reserve it. The discount applied by a Reserved Instance purchase is not directly associated with a specific instance ID, but with an instance type.

###### Save on costs with Spot Instances
Another way to pay for EC2 instances is by using Spot Instances. Amazon EC2 Spot Instances allow you to take advantage of unused EC2 capacity in the AWS Cloud. They are available at up to a 90% discount compared to On-Demand prices.

With Spot Instances, you set a limit on how much you would like to pay for the instance hour. This is compared against the current Spot price that AWS determines. If the amount you pay is more than the current Spot price and there is capacity, then you will receive an instance. While they are very promising from the billing perspective, you must account for some architectural considerations to use them effectively.

One consideration is that your Spot Instance might be interrupted. For example, if AWS determines that capacity is no longer available for a particular Spot Instance or if the Spot price exceeds how much you are willing to pay, AWS will give you a 2-minute warning before it interrupts your instance. That means any application or workload that runs on a Spot Instance must be able to be interrupted.

Because of this unique consideration, inherently fault-tolerant workloads are typically good candidates to use with Spot Instances. These include big data, containerized workloads, continuous integration/continuous delivery (CI/CD), web servers, high-performance computing (HPC), image and media rendering, and other test and development workloads.

##### Resources
- https://aws.amazon.com/ec2/
- https://docs.aws.amazon.com/vpc/latest/userguide/default-vpc.html
- https://d1.awsstatic.com/whitepapers/architecture/AWS-Reliability-Pillar.pdf
- https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-instance-lifecycle.html
- https://aws.amazon.com/ec2/pricing/
- https://aws.amazon.com/ec2/pricing/on-demand/
- https://aws.amazon.com/ec2/spot/pricing/
- https://aws.amazon.com/ec2/pricing/reserved-instances/pricing/


#### Container Services
...
...
##### Manage containers with Amazon Elastic Container Service (Amazon ECS)
To run and manage your containers, you need to install the Amazon ECS container agent on your EC2 instances. This agent is open source and responsible for communicating to the Amazon ECS service about cluster management details. You can run the agent on both Linux and Windows AMIs. An instance with the container agent installed is often called a container instance.

To prepare your application to run on Amazon ECS, you create a task definition. The task definition is a text file, in JSON format, that describes one or more containers. A task definition is similar to a blueprint that describes the resources you need to run a container, such as CPU, memory, ports, images, storage, and networking information.

Here is a simple task definition that you can use for your corporate directory application. In this example, this runs on the Nginx web server.

```json
{
"family": "webserver",
"containerDefinitions": [ {
"name": "web",
"image": "nginx",
"memory": "100",
"cpu": "99"
} ],
"requiresCompatibilities": [ "FARGATE" ],
"networkMode": "awsvpc",
"memory": "512",
"cpu": "256"
}
```

##### Use Kubernetes with Amazon Elastic Kubernetes Service (Amazon EKS)
If you already use Kubernetes, you can use Amazon EKS to orchestrate the workloads in the AWS Cloud. Amazon EKS is conceptually similar to Amazon ECS, but with the following differences:

- An EC2 instance with the ECS agent installed and configured is called a container instance. In Amazon EKS, it is called a worker node.
- An ECS container is called a task. In Amazon EKS, it is called a pod.
- While Amazon ECS runs on AWS native technology, Amazon EKS runs on top of Kubernetes.

If you have containers running on Kubernetes and want an advanced orchestration solution that can provide simplicity, high availability, and fine-grained control over your infrastructure, Amazon EKS could be the tool for you.

##### Resources
- https://aws.amazon.com/containers/services/
- https://www.docker.com/resources/what-container
- https://aws.amazon.com/ecs/
- https://github.com/aws/amazon-ecs-agent
- https://docs.aws.amazon.com/AmazonECS/latest/developerguide/ECS_instances.html
- https://www.coursera.org/learn/containerized-apps-on-aws


#### AWS Lambda
##### Remove the undifferentiated heavy lifting
If you run your code on Amazon EC2, AWS is responsible for the physical hardware, and you are responsible for the logical controls, such as guest operating system, security and patching, networking, security, and scaling.

If you run your code in containers on Amazon ECS and Amazon EKS, AWS is responsible for more of the container management, such as deploying containers across EC2 instances and managing the container cluster. However, when running ECS and EKS on EC2, you are still responsible for maintaining the underlying EC2 instances.

If you want to deploy your workloads and applications without having to manage any EC2 instances, you can do that on AWS with serverless compute.

##### Go serverless

Every definition of serverless mentions the following four aspects:

- No servers to provision or manage
- Scales with usage
- You never pay for idle resources
- Availability and fault tolerance are built-in

With serverless, you can spend time on the things that differentiate your application, rather than spend time on ensuring availability, scaling, and managing servers.

AWS has several serverless compute options, including AWS Fargate and AWS Lambda.

##### Explore serverless containers with AWS Fargate
Amazon ECS and Amazon EKS enable you to run your containers in the following two modes:

- Amazon EC2 mode
- AWS Fargate mode

Fargate abstracts the EC2 instance so that you’re not required to manage it. However, with Fargate, you can use all the same ECS primitives, APIs, and AWS integrations. It natively integrates with AWS Identity and Access Management (IAM) and Amazon Virtual Private Cloud (VPC). Having native integration with Amazon VPC allows you to launch Fargate containers inside your network and control connectivity to your applications.

##### Run code on AWS Lambda

If you want to deploy your workloads and applications without having to manage any EC2 instances or containers, you can use AWS Lambda.

AWS Lambda requires zero administration from the user. You upload your source code, and Lambda takes care of everything required to run and scale your code with high availability. There are no servers to manage, bringing you continuous scaling with subsecond metering and consistent performance.

###### How AWS Lambda works

A Lambda function has three primary components – trigger, code, and configuration. 

![Alt text](https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcSHq5eHzGR_x4BBbkWtvi_B0uryGz82EwXHmg&usqp=CAU "How AWS Lambda works")

The code is source code that describes what the Lambda function should run. It can be authored in three ways.

- You create the code from scratch.
- You use a blueprint that AWS provides.
- You use some code from the AWS Serverless Application Repository, a resource that contains sample applications, such as “hello world” code, Amazon Alexa Skill sample code, image resizing code, video encoding, and more.

Triggers describe when a Lambda function should run. A trigger integrates your Lambda function with other AWS services, enabling you to run your Lambda function in response to certain API calls that occur in your AWS account. This increases your ability to respond to events in your console without having to perform manual actions. All you need is the what, how, and when of a Lambda function to have functional compute capacity that runs only when you need it to.

##### Billing granularity
AWS Lambda lets you run code without provisioning or managing servers, and you pay only for what you use. You are charged for the number of times your code is triggered (requests) and for the time your code executes, rounded up to the nearest 1 ms (duration).

AWS rounds up duration to the nearest millisecond with no minimum execution time. With this pricing, it can be cost effective to run functions whose execution time is very low, such as functions with durations under 100 ms or low latency APIs. Read more here: https://aws.amazon.com/blogs/aws/new-for-aws-lambda-1ms-billing-granularity-adds-cost-savings/

##### Source Code Example
You can find a tutorial on creating the AWS Lambda function as well as the code used in the AWS Lambda demo here: https://aws.amazon.com/blogs/compute/resize-images-on-the-fly-with-amazon-s3-aws-lambda-and-amazon-api-gateway/

##### Sources
- https://aws.amazon.com/serverless/#:~:text=Serverless%20is%20the%20native%20architecture,services%20without%20thinking%20about%20servers.
- https://www.coursera.org/learn/building-modern-python-applications-on-aws
- https://aws.amazon.com/serverless/resources/?serverless.sort-by=item.additionalFields.createdDate&serverless.sort-order=desc
- https://aws.amazon.com/lambda/serverless-architectures-learn-more/
- https://aws.amazon.com/blogs/compute/best-practices-for-organizing-larger-serverless-applications/
- https://docs.aws.amazon.com/lambda/latest/dg/lambda-functions.html
- https://aws.amazon.com/blogs/architecture/ten-things-serverless-architects-should-know/
- https://alienattack.workshop.aws/


### Module 3: AWS Networking
#### Networking
Networking is how you connect computers around the world and allow them to communicate with one another. In this course, you’ve already seen a few examples of networking. One is the AWS Global Infrastructure. AWS built a network of resources using data centers, Availability Zones, and Regions. 

##### CIDR notation

192.168.1.30 is a single IP address. If you want to express IP addresses between the range of 192.168.1.0 and 192.168.1.255, how can you do that?

One way is to use Classless Inter-Domain Routing (CIDR) notation. CIDR notation is a compressed way of specifying a range of IP addresses. Specifying a range determines how many IP addresses are available to you.

CIDR notation is shown here.

![Alt text](https://miro.medium.com/v2/resize:fit:4800/format:webp/1*usoMZSgY4BXs2_W5Z1QRIA.png "CIDR Notation")

The higher the number after the /, the smaller the number of IP addresses in your network. For example, a range of 192.168.1.0/24 is smaller than 192.168.1.0/16.

When working with networks in the AWS Cloud, you choose your network size by using CIDR notation. In AWS, the smallest IP range you can have is /28, which provides 16 IP addresses. The largest IP range you can have is a /16, which provides 65,536 IP addresses.

##### Resources
- https://web.stanford.edu/class/cs101/network-1-introduction.html
- https://en.wikipedia.org/wiki/Classless_Inter-Domain_Routing
- https://cidr.xyz/

#### Amazon Virtual Private Cloud
##### Amazon VPC
A virtual private cloud (VPC) is an isolated network that you create in the AWS Cloud, similar to a traditional network in a data center. When you create a VPC, you must choose three main factors:

- Name of the VPC.
- Region where the VPC will live. Each VPC spans multiple Availability Zones within the selected Region.
- IP range for the VPC in CIDR notation. This determines the size of your network. Each VPC can have up to four /16 IP ranges.

Using this information, AWS will provision a network and IP addresses for that network.

![Alt text](https://explore.skillbuilder.aws/files/a/w/aws_prod1_docebosaas_com/1676433600/f7zcEGMk8mUF7mcoGgfQTQ/tincan/d03722b85f9d2b3a05e4c74bd586ea9b1f52f81a/assets/8kXmOfxfIKxFvLC1_KKtsB2WCJm3nf8cP.png "Amazon VPC")

##### Create a subnet

After you create your VPC, you must create subnets inside the network. Think of subnets as smaller networks inside your base network – or virtual local area networks (VLANs) in a traditional, on-premises network. In an on-premises network, the typical use case for subnets is to isolate or optimize network traffic. In AWS, subnets are used to provide high availability and connectivity options for your resources.

When you create a subnet, you must specify the following:

- VPC you want your subnet to live in. In this case: VPC (10.0.0.0/16)
- Availability Zone you want your subnet to live in. In this case: AZ1
- CIDR block for your subnet, which must be a subset of the VPC CIDR block. In this case: 10.0.0.0/24

When you launch an EC2 instance, you launch it inside a subnet, which will be located inside the Availability Zone you choose.

![Alt text](https://explore.skillbuilder.aws/files/a/w/aws_prod1_docebosaas_com/1676433600/f7zcEGMk8mUF7mcoGgfQTQ/tincan/d03722b85f9d2b3a05e4c74bd586ea9b1f52f81a/assets/vZpR01LhiiYP4wmh_aU-cuzRVrh2oRrmu.png "Create a subnet")

##### High availability with a VPC

When you create your subnets, keep high availability in mind. To maintain redundancy and fault tolerance, create at least two subnets configured in two Availability Zones.

As you learned earlier, remember that “everything fails all of the time.” With the example network, if one of the AZs fails, you will still have your resources available in another AZ as backup.

![Alt text](https://explore.skillbuilder.aws/files/a/w/aws_prod1_docebosaas_com/1676433600/f7zcEGMk8mUF7mcoGgfQTQ/tincan/d03722b85f9d2b3a05e4c74bd586ea9b1f52f81a/assets/wPxuV_0JWkhj9dQV_InIjhnQ0x-d4xLbK.png "High availability with a VPC")

##### Reserved IPs

For AWS to configure your VPC appropriately, AWS reserves five IP addresses in each subnet. These IP addresses are used for routing, Domain Name System (DNS), and network management.

For example, consider a VPC with the IP range 10.0.0.0/22. The VPC includes 1,024 total IP addresses. This is divided into four equal-sized subnets, each with a /24 IP range with 256 IP addresses. Out of each of those IP ranges, there are only 251 IP addresses that can be used because AWS reserves five.

![Alt text](https://explore.skillbuilder.aws/files/a/w/aws_prod1_docebosaas_com/1676433600/f7zcEGMk8mUF7mcoGgfQTQ/tincan/d03722b85f9d2b3a05e4c74bd586ea9b1f52f81a/assets/rMW_Z-uCrzlXDX6P_Vtr6qzn_A_IyobZs.jpg "Reserved IPs")

The five reserved IP addresses can impact how you design your network. A common starting place for those who are new to the cloud is to create a VPC with an IP range of /16 and create subnets with an IP range of /24. This provides a large amount of IP addresses to work with at both the VPC and subnet levels.

##### Gateways

###### Internet gateway
To enable internet connectivity for your VPC, you must create an internet gateway. Think of the gateway as similar to a modem. Just as a modem connects your computer to the internet, the internet gateway connects your VPC to the internet. Unlike your modem at home, which sometimes goes down or offline, an internet gateway is highly available and scalable. After you create an internet gateway, you attach it to your VPC.

###### Virtual private gateway
A virtual private gateway connects your AWS VPC to another private network. Once you create and attach a virtual private gateway to a VPC, the gateway acts as anchor on the AWS side of the connection. On the other side of the connection, you will need to connect a customer gateway to the other private network. A customer gateway device is a physical device or software application on your side of the connection. Once you have both gateways, you can then establish an encrypted VPN connection between the two sides.

##### Resources
- https://docs.aws.amazon.com/vpc/latest/userguide/VPC_Scenario2.html
- https://docs.aws.amazon.com/vpc/latest/userguide/VPC_Route_Tables.html#CustomRouteTables
- https://docs.aws.amazon.com/vpn/latest/s2svpn/how_it_works.html#CustomerGateway
- https://docs.aws.amazon.com/vpc/latest/userguide/what-is-amazon-vpc.html
- https://docs.aws.amazon.com/vpc/latest/userguide/VPC_Subnets.html

#### Amazon VPC Routing

##### Main route table

When you create a VPC, AWS creates a route table called the main route table. A route table contains a set of rules, called routes, that are used to determine where network traffic is directed. AWS assumes that when you create a new VPC with subnets, you want traffic to flow between them. Therefore, the default configuration of the main route table is to allow traffic between all subnets in the local network. Below is an example of a main route table.

The destination and target are two main parts of this route table.

- The destination is a range of IP addresses where you want your traffic to go. In the example of sending a letter, you need a destination to route the letter to the appropriate place. The same is true for routing traffic. In this case, the destination is the VPC network's IP range.
- The target is the connection through which to send the traffic. In this case, the traffic is routed through the local VPC network.

![Alt text](https://explore.skillbuilder.aws/files/a/w/aws_prod1_docebosaas_com/1676433600/f7zcEGMk8mUF7mcoGgfQTQ/tincan/d03722b85f9d2b3a05e4c74bd586ea9b1f52f81a/assets/vIZTs-87LdFIeKG9_-X2_R4cjJxpD1O-V.jpg "Main route table")

##### Custom route tables

While the main route table is used implicitly by subnets that do not have an explicit route table association, you might want to provide different routes on a per-subnet basis, for traffic to access resources outside of the  VPC. For example, your application might consist of a front end and a database. You can create separate subnets for the resources and provide different routes for each of them.

If you associate a custom route table with a subnet, the subnet will use it instead of the main route table. Each custom route table you create will have the local route already inside it, allowing communication to flow between all resources and subnets inside the VPC. The local route cannot be deleted.

![Alt text](https://explore.skillbuilder.aws/files/a/w/aws_prod1_docebosaas_com/1676433600/f7zcEGMk8mUF7mcoGgfQTQ/tincan/d03722b85f9d2b3a05e4c74bd586ea9b1f52f81a/assets/TOFyTY8NnEvCzqi3_NrsH76kCPC3B5ySy.jpg "Custom route tables")

#### Amazon VPC Security

##### Secure subnets with network access control lists

Think of a network access control list (network ACL) as a firewall at the subnet level. A network ACL enables you to control what kind of traffic is allowed to enter or leave your subnet. You can configure this by setting up rules that define what you want to filter. Here’s an example.

**Inbound**
| Rule# | Type | Protocol | Port Range | Source | Allow/Deny |
|:------|:-----|:---------|:-----------|:-------|:-----------|
| 100   | All IPv4 Traffic | All | All | 0.0.0.0/0 | ALLOW |
| *   | All IPv4 Traffic | All | All | 0.0.0.0/0 | DENY |

**Outbound**
| Rule# | Type | Protocol | Port Range | Source | Allow/Deny |
|:------|:-----|:---------|:-----------|:-------|:-----------|
| 100   | All IPv4 Traffic | All | All | 0.0.0.0/0 | ALLOW |
| *   | All IPv4 Traffic | All | All | 0.0.0.0/0 | DENY |

The default network ACL, shown in the preceding table, allows all traffic in and out of the subnet. To allow data to flow freely to the subnet, this is a good starting place.

However, you might want to restrict data at the subnet level. For example, if you have a web application, you might restrict your network to allow HTTPS traffic and remote desktop protocol (RDP) traffic to your web servers.

**Inbound**
| Rule# | Source IP | Protocol | Port | Allow/Deny | Comments |
|:------|:-----|:---------|:-----------|:-------|:-----------|
| 100   | All IPv4 Traffic | TCP | 443 | ALLOW | Allows inbound HTTPS traffic from anywhere |
| 130   | 192.0.2.0/24 | TCP | 3389 | ALLOW | Allows inbound RDP traffic to the web servers from your home network’s public IP address range (over the internet gateway) |
| *   | All IPv4 Traffic | All | All | DENY | Denies all inbound traffic not already handled by a preceding rule (not modifiable) |

**Outbound**
| Rule# | Source IP | Protocol | Port | Allow/Deny | Comments |
|:------|:-----|:---------|:-----------|:-------|:-----------|
| 120   | 0.0.0.0/0 | TCP | 1025-65535 | ALLOW | Allows outbound responses to clients on the internet (serving people visiting the web servers in the subnet) |
| *   | 0.0.0.0/0 | All | All | DENY | Denies all outbound traffic not already handled by a preceding rule (not modifiable) |

Notice that in the preceding network ACL example, you allow inbound 443 and outbound range 1025–65535. That’s because HTTP uses port 443 to initiate a connection and will respond to an ephemeral port. Network ACLs are considered stateless, so you need to include both the inbound and outbound ports used for the protocol. If you don’t include the outbound range, your server would respond but the traffic would never leave the subnet.

Since network ACLs are configured by default to allow incoming and outgoing traffic, you don’t need to change their initial settings unless you need additional security layers.

##### Secure EC2 instances with security groups

The next layer of security is for your EC2 Instances. Here, you can create a firewall called a security group. The default configuration of a security group blocks all inbound traffic and allows all outbound traffic.

![Alt text](https://explore.skillbuilder.aws/files/a/w/aws_prod1_docebosaas_com/1676433600/f7zcEGMk8mUF7mcoGgfQTQ/tincan/d03722b85f9d2b3a05e4c74bd586ea9b1f52f81a/assets/SGo2r3D-rFt_5A57_LHSo8q3H-_Wuu73H.jpg "Secure EC2 instances with security groups")

You might be wondering, “Wouldn’t this block all EC2 instances from receiving the response of any customer requests?” Well, security groups are stateful. That means that they will remember if a connection is originally initiated by the EC2 instance or from the outside, and temporarily allow traffic to respond without modifying the inbound rules.

If you want your EC2 instance to accept traffic from the internet, you must open up inbound ports. If you have a web server, you might need to accept HTTP and HTTPS requests to allow that type of traffic into your security group. You can create an inbound rule that will allow port 80 (HTTP) and port 443 (HTTPS), as shown.

**Inbound rules**
| Type | Protocol | Port Range | Source |
|:-----|:---------|:-----------|:-------|
| HTTP (80) | TCP (6) | 80 | 0.0.0.0/0 |
| HTTP (80) | TCP (6) | 80 | ::/0 |
| HTTPS (443) |	TCP (6) | 443 | 0.0.0.0/0 |
| HTTPS (443) | TCP (6) | 443 | ::/0 |

You learned in a previous unit that subnets can be used to segregate traffic between computers in your network. Security groups can be used in the same way. A common design pattern is to organize resources into different groups and create security groups for each to control network communication between them.

![Alt text](https://explore.skillbuilder.aws/files/a/w/aws_prod1_docebosaas_com/1676433600/f7zcEGMk8mUF7mcoGgfQTQ/tincan/d03722b85f9d2b3a05e4c74bd586ea9b1f52f81a/assets/FgEhatXf6qnJQ1X1_scxJIDNUzFAqjZbL.jpg "Security group settings")

This example defines three tiers and isolates each tier with defined security group rules. In this case, internet traffic to the Web Tier is allowed over HTTPS, Web Tier to Application Tier traffic is allowed over HTTP, and Application tier to Database tier traffic is allowed over MySQL. This is different from traditional on-premises environments, in which you isolate groups of resources via a VLAN configuration. In AWS, security groups allow you to achieve the same isolation without tying it to your network.

##### Resources
- https://docs.aws.amazon.com/vpc/latest/userguide/VPC_Route_Tables.html
- https://docs.aws.amazon.com/vpc/latest/userguide/route-table-options.html
- https://docs.aws.amazon.com/vpc/latest/userguide/WorkWithRouteTables.html
- https://docs.aws.amazon.com/vpc/latest/userguide/vpc-network-acls.html
- https://docs.aws.amazon.com/vpc/latest/userguide/VPC_SecurityGroups.html
- https://aws.amazon.com/premiumsupport/knowledge-center/connect-http-https-ec2/









































































































































