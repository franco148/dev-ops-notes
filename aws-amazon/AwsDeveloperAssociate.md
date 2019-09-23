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


































