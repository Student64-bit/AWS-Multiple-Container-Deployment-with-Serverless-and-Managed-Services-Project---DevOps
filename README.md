# AWS Multiple Container Deployment with Serverless and Managed Services Project - DevOps

## Overview

The primary goal of this project is to gain hands-on experience with AWS ECS by automating the deployment of Docker containers across different applications. Instead of manually configuring EC2 instances, I have chosen to utilize AWS Fargate, a managed service that enables serverless operation to meet my objectives.

## AWS Services Used

- **AWS ECS**: Manages the container deployment process.
- **AWS Fargate**: Facilitates serverless deployment and management of applications.
- **AWS Load Balancer**: Provides a single endpoint for the front end across multiple containers, enabling infinite scaling without the need to manage IP addresses.
- **AWS IAM**: Implements best security practices for the project.
- **AWS Security Groups**: Manages access permissions for various AWS services.
- **AWS ECR (Elastic Container Registry)**: Stores the Docker images used in the project.
- **AWS EFS (Elastic File System)**: Works with the Load Balancer to distribute applications.
- **AWS VPC**: Hosts the project infrastructure, providing multiple subnets for high availability.
- **AWS CloudWatch Logs**: Assists in monitoring and troubleshooting the project components.

## Other Services Used

- **Docker**: Builds Docker images locally.
- **Postman**: Tests the application database through CRUD operations.
- **MongoDB**: A NoSQL database chosen for this project due to its simplicity and the low data traffic expected.

## Deployment Steps

### 1. Setting Up Application #1’s Docker Image
I used Docker to build an image from a Dockerfile in my application folder, which included basic dependencies and installations. The image was then pushed to AWS ECR using the AWS CLI. Although Docker Hub was an alternative, I preferred to use ECR to gain experience with AWS services.

<img src="https://i.imgur.com/ofA8dnz.png" height="80%" width="80%" alt="Code commit permissions"/>
<br />
<img src="https://i.imgur.com/Rp18qbI.png" height="80%" width="80%" alt="Code commit permissions"/>
<br />
<img src="https://i.imgur.com/h5ddlOd.png" height="80%" width="80%" alt="Code commit permissions"/>
<br />


### 2. Setting Up the Elastic Container Service (ECS)
With the Docker image stored in ECR, I referenced its URI in the ECS configuration. This setup allows for the automated, serverless scaling of containerized applications managed by AWS Fargate. Developers preferring more control over their containers might opt for manually configured EC2 instances instead.

<img src="https://i.imgur.com/0xvEMRh.png" height="80%" width="80%" alt="Code commit permissions"/>
<br />

### 3. Configuring Tasks and Task Definitions
I configured a task and task definitions within ECS to automate and scale deployment of my application. The Docker image provided the necessary blueprint for the software and dependencies.

<img src="https://i.imgur.com/ZrCMybY.png" height="80%" width="80%" alt="Code commit permissions"/>
<br />

### 4. Initial Application Deployment
After deploying the application, I found that using separate IPs for each instance could complicate scaling. To address this, I used a load balancer in the subsequent application to maintain a static IP, simplifying the management of multiple instances.

<img src="https://i.imgur.com/RShEnHA.png" height="80%" width="80%" alt="Code commit permissions"/>
<br />
<img src="https://i.imgur.com/fg32qIU.png" height="80%" width="80%" alt="Code commit permissions"/>
<br />

### 5. Deploying a Multi-Container Application
The second application included multiple containers interacting with a MongoDB database such as the MongoDB itself and a Web Api. I set different environment variables in the task definition to facilitate the interaction between the containers and the database. Security was not a concern as I planned to clean up all configurations post-deployment.

<img src="https://i.imgur.com/9LN65FR.png" height="80%" width="80%" alt="Code commit permissions"/>
<br />
<img src="https://i.imgur.com/3aXDKbQ.png" height="80%" width="80%" alt="Code commit permissions"/>
<br />
<img src="https://i.imgur.com/xOTqUKT.png" height="80%" width="80%" alt="Code commit permissions"/>
<br />
<img src="https://i.imgur.com/1ywv6re.png" height="80%" width="80%" alt="Code commit permissions"/>
<br />


### 6. Integrating Load Balancer and Elastic File System (EFS)
I used a load balancer in conjunction with EFS to provide a single endpoint for frontend interaction, enhancing scalability by abstracting individual container IPs behind a unified DNS entry.

### 7. Troubleshooting Deployment Issues
I resolved several deployment issues, such as failed health checks and 503 errors, by analyzing AWS CloudWatch Logs and adjusting security group settings accordingly.

<img src="https://i.imgur.com/BX1Wn1T.png" height="80%" width="80%" alt="Code commit permissions"/>
<br />
<img src="https://i.imgur.com/QqHenj3.png" height="80%" width="80%" alt="Code commit permissions"/>
<br />

### 8. Video Demonstration
I created a video demonstrating how to use Postman to interact with the deployed application database. [View the demonstration here](https://youtu.be/3_gZv3k6nDI).

## Credits

While I configured and set up the AWS services, the applications themselves were provided by KodeKloud. I am grateful to [KodeKloud](https://www.youtube.com/@KodeKloud) for the resources used in this Dev.
