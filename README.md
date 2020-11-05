# AWS Developer Associate Training
*Training for AWS Certified Developer - Associate Certification*  

---
**Shared Responsibility Model**  
https://aws.amazon.com/compliance/shared-responsibility-model/
---

*AWS responsibility “Security of the Cloud”*  
*Customer responsibility “Security in the Cloud*

**Inherited Controls** – Controls which a customer fully inherits from AWS.

- Physical and Environmental controls

**Shared Controls** – Controls which apply to both the infrastructure layer and customer layers, but in completely separate contexts or perspectives. In a shared control, AWS provides the requirements for the infrastructure and the customer must provide their own control implementation within their use of AWS services. Examples include:

- Patch Management – AWS is responsible for patching and fixing flaws within the infrastructure, but customers are responsible for patching their guest OS and applications.

- Configuration Management – AWS maintains the configuration of its infrastructure devices, but a customer is responsible for configuring their own guest operating systems, databases, and applications.

- Awareness & Training - AWS trains AWS employees, but a customer must train their own employees.

**Customer Specific** – Controls which are solely the responsibility of the customer based on the application they are deploying within AWS services. Examples include:

- Service and Communications Protection or Zone Security which may require a customer to route or zone data within specific security environments.  

---
**Security, Identity, & Compliance**
---

IAM - Identity and Access Management
> AWS Identity and Access Management (IAM) is a web service for securely controlling access to AWS services. With IAM, you can centrally manage users, security credentials such as access keys, and permissions that control which AWS resources users and applications can access.

- Centralised control of your AWS account
- Shared Access to your AWS account
- Granular Permissions
- Identity Federation (including Active Directory, Facebook, LinkedIn, etc)
- Multifactor Authentication
- Provides temporary access for users/devices and services as necessary
- Allows you to set up your own password rotation policy
- Integrates with many different AWS services
- Supports PCI DSS Compliance

**Critical Terms:**
- **Users** - End Users (think people)
- **Groups** - A collection of users under one set of permissions (e.g Marketing Team, DB Team)
- **Roles** - You can create roles and can then assign them to AWS resources (defines a set of permissions, e.g S3 bucket access)
- **Policies** - A document that defines one (or more) permissions (they can be attached to a user, a group or a role - they can all share the same policy)

```
aws configure --profile [username]
aws iam list-users
aws iam list-groups
```

Cognito
> Amazon Cognito handles user authentication and authorization for your web and mobile apps. With user pools, you can easily and securely add sign-up and sign-in functionality to your apps. With identity pools (federated identities), your apps can get temporary credentials that grant users access to specific AWS resources, whether the users are anonymous or are signed in.

```
aws cognito-identity create-identity-pool ---identity-pool-name
```

---
**Storage**
---

S3 - Simple Storage Service
> Use Amazon S3 to store and retrieve any amount of data at any time using the same highly scalable, reliable, fast, inexpensive data storage infrastructure that Amazon uses to run its own global network of websites.

```
aws s3 ls
aws s3 mb s3://{YOUR-BUCKET-NAME}
aws s3 cp /xxx.jpg s3://{YOUR-BUCKET-NAME}

S3API
aws s3api list-buckets
aws s3api create-bucket --bucket {YOUR-BUCKET-NAME} --region eu-west-2 --create-bucket-configuration LocationConstraint=eu-west-2
aws s3api delete-bucket --bucket {YOUR-BUCKET-NAME}
aws s3api get-bucket-location --bucket {YOUR-BUCKET-NAME}
aws s3api list-objects --bucket {YOUR-BUCKET-NAME}
```

- Access control lists (ACLs), bucket policies, access point policies

---
**Compute**
---

EC2 - Elastic Compute Cloud
> Amazon Elastic Compute Cloud (Amazon EC2) is a web service that provides resizable computing capacity—literally, servers in Amazon's data centers—that you use to build and host your software systems.

```
aws ec2 describe-instances
```

---

Lambda
> With AWS Lambda, you can run code without provisioning or managing servers. You pay only for the compute time that you consume—there’s no charge when your code isn’t running. You can run code for virtually any type of application or backend service—all with zero administration. Just upload your code and Lambda takes care of everything required to run and scale your code with high availability. You can set up your code to automatically trigger from other AWS services or call it directly from any web or mobile app.

```
aws lambda ls
aws lambda get-function --function-name {FUNCTION-NAME}
aws lambda update-function-configuration --function-name {FUNCTION-NAME} --description "xxx"
```

- Versioning/Weighting/Aliases

---

Serverless Application Model
> The AWS Serverless Application Model (AWS SAM) is an open-source framework that enables you to build serverless applications on AWS. It provides you with a template specification to define your serverless application, and a command line interface (CLI) tool.


---
**Networking & Content Delivery**
---
API Gateway
> Amazon API Gateway enables you to create and deploy your own REST and WebSocket APIs at any scale. You can create robust, secure, and scalable APIs that access AWS or other web services, as well as data that’s stored in the AWS Cloud. You can create APIs to use in your own client applications, or you can make your APIs available to third-party app developers.


---
**Front-End Web & Mobile**
---
Amplify
> AWS Amplify enables developers to develop and deploy cloud-powered mobile and web apps. The Amplify Framework is a comprehensive set of SDKs, libraries, tools, and documentation for client app development. The Amplify Console provides a continuous delivery and hosting service for web applications.

```
aws amplify ls
```

---
**Management & Governance**
---
CloudFormation
> AWS CloudFormation enables you to create and provision AWS infrastructure deployments predictably and repeatedly. It helps you leverage AWS products such as Amazon EC2, Amazon Elastic Block Store, Amazon SNS, Elastic Load Balancing, and Auto Scaling to build highly reliable, highly scalable, cost-effective applications in the cloud without worrying about creating and configuring the underlying AWS infrastructure. AWS CloudFormation enables you to use a template file to create and delete a collection of resources together as a single unit (a stack).

---
**Cloud Development Kit**  
[Notes](https://github.com/eggheadio/eggheadio-course-notes/tree/master/build-an-app-with-the-AWS-cloud-development-kit)
---
> The AWS Cloud Development Kit (AWS CDK) is a software development framework for defining your cloud infrastructure in code and provisioning it through AWS CloudFormation.

- Constructs

```
cdk --version
cdk init sample-app --language=typescript
cdk diff
cdk deploy
cdk bootstrap
```




