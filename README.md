# Learning-Management-System
CSYE6225 Network Structures &amp; Cloud Computing AWS project

# Webapp

This is a REST API for managing student assignments, built with Node.js, Express, Sequelize ORM and MySQL.

Learning Management System REST API | Node.js, Sequelize ORM, AWS	                
•	Developed cloud based REST API to enable CRUD operations on assignments stored in database. Achieved 99.9% uptime
•	Implemented Terraform-based infrastructure for Node.js application encompassing VPC, Subnets, route tables, Internet Gateway and integration with AWS services including EC2, RDS, Lambda and S3
•	Engineered a robust CI/CD pipeline using GitHub Actions, ensuring seamless integration and deployment 
•	Effectively maintained logs and monitored key metrics on AWS CloudWatch, resulting in a 50% reduction in deployment time
•	Built custom AMIs using Packer and Terraform(Pulumi) to launch EC2 instances, enabling dynamic scaling of a Node.js application based on traffic influx through auto-scaling and load balancing


Features CRUD operations for assignments User authentication with JSON Web Tokens MVC architecture CI/CD pipeline with GitHub Actions Automated tests Logging with CloudWatch AMI creation with Packer Getting Started Prerequisites Node.js MySQL Installation

```npm install Set environment variables in .env file```

DB_NAME=<your_db_name> DB_USER=<your_db_user> DB_PASSWORD=<your_db_password> DB_HOST=localhost

# Start the server
- npm start The API will be running on http://localhost:8080
- Usage The API exposes the following endpoints:
- Heatlh Routed GET /v1/healthz - Get database health

Assignment Routes GET /v1/assignments - Get all assignments POST /v1/assignments - Create a new assignment GET /v1/assignments/:id - Get an assignment by id PUT /v1/assignments/:id - Update an assignment by id DELETE /v1/assignments/:id - Delete an assignment by id Running Tests

npm test CI/CD Pipeline The GitHub Actions workflow performs:
Running tests
Built With Node.js - Runtime environment Express - Web framework Sequelize - ORM MySQL - Database
Logging Logs are sent to CloudWatch using CloudWatch Agent with StatsD protocol.

Infrastructure as Code The infrastructure is defined as code with:
Packer - For building AMIs
This enables a reproducible and version controlled environment.


# iac-pulumi
 
# Infrastructure as Code (IaC) with Pulumi
 
This repository contains Infrastructure as Code (IaC) setup for creating necessary networking infrastructure in AWS using Pulumi. Additionally, it creates resources in Google Cloud Platform (GCP) for a comprehensive setup.
 
## Prerequisites
 
### Install AWS CLI and Pulumi
 
Ensure AWS CLI and Pulumi are installed on your machine. Follow these steps:
 
1. Install the [AWS CLI](https://aws.amazon.com/cli/) and configure profiles for `dev` and `demo`.
 
2. Install [Pulumi](https://www.pulumi.com/docs/get-started/install/).
   
3. Install the AWS Command Line Interface (CLI) on your development machine (laptop):
 
    ```https://aws.amazon.com/cli/```
 
    ```aws version``` to check version
 
   ```bash```
   ```brew install awscli```
 
    ```aws configure --profile dev```
    ```aws configure --profile demo```
 
 
4. install pulumi
 
    ```brew install pulumi```
 
    ```pulumi version``` to check version
 
 
 
5. set the pulumi locally & configure the user account
 
    ```pulumi login --local```
 
       - select -> aws:javascript
 
           - create a stack with proper project name & accessKey
 
    ```pulumi config set aws:accessKey <AccessKey>```
 
    ```pulumi config set --secret  aws:secretKey <your_secret_key>```
 
    ```pulumi config set aws:region <region>```
 
 
 
## Getting Started
 
Follow these steps to set up and execute the code:
 
1. **Modify Configuration:**
   Update `index.js` and `pulumi.dev.yaml`, `pulumi.demo.yaml` with your specific environment variables and configurations.
 
2. **Execute the Code:**
   Run `pulumi up` to deploy the infrastructure. Use `pulumi refresh` to update the code.
 
## Import SSL Certificate into AWS ACM
 
To import an SSL certificate into AWS ACM, use the provided command in the README.
 
## Code Overview
 
The provided code in `index.js` demonstrates:
 
AWS resources creation in `createAWSResources()` function, including:
- Creating a Virtual Private Cloud (VPC) in AWS.
- Setting up Amazon SNS and related AWS resources.
- Creating security groups and subnets.
- Configuration of Amazon RDS (Relational Database Service) instances.
- Auto Scaling configurations for web application instances.
- Setup of AWS Application Load Balancer (ALB).
- Integration of Route53 for DNS record configuration.
 
Additionally, GCP resources are provisioned in `createGCPResources()` function, including:
 
- Google Cloud Storage bucket.
- Google IAM service account and its permissions.
- Lambda function setup to interact with GCP services.
 
Feel free to explore the code for detailed implementation.
 
## Important Notes
 
- Ensure proper permissions and access keys are set before deploying resources.
- Review IAM roles and policies for security and compliance.
- Update and test your configurations in a safe environment before deploying to production.
 
 
## Import SSL Certificate into AWS ACM
To import SSL certificate into AWS ACM, use the following command:
 
```aws acm import-certificate --certificate fileb:/path/to/demo.talentofpainting.info.crt --private-key fileb:/path/to/demo.talentofpainting.info_key.txt --certificate-chain fileb:/path/to/demo.talentofpainting.info.ca-bundle```
