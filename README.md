CI/CD Docker Tool Stack:
GitHub
I created and store our sample Nodejs application code here.
AWS EC2 Instance
I created an EC2 instance and install Jenkins and other dependencies in it.
Java
For Jenkins Server. I used version 11.
AWS CLI
I used it to manage AWS ECS Task and ECS Service.
Nodejs and Npm
For my Nodejs application.
Docker
I used it to build Docker images of Nodejs application and push/pull them to/from AWS ECR.
Jenkins
Created our CI/CD Docker pipeline to build, test and deploy our Nodejs application on AWS ECS using Jenkins.
AWS ECR
I used AWS ECR to store Docker images Nodejs application.
AWS ECS
I used it to host Nodejs application.

I created DockerFile for my Nodejs application, you can see in this repo.

I created an Ecr Repository.

I created an Ecs Cluster and configure name to the container as nodejs-container, use the 3000 port in the port mappings. I used to Application Load Balancer and listining 3000 port.

I created an EC2 Instance with Ubuntu 18.04 AMI and open its Port 22 for my home ip and Port 8080 for 0.0.0.0/0 in its Security Group. Port 8080 is where GitHub Webhook trying to connect to on Jenkins Server.

I installed Java, JSON Processor jq, Nodejs/NPM, Jenkins, Docker and aws-cli on my EC2 Instance.

I installed plugins for my Jenkins:
Docker Pipeline:This plugin allows building, testing, and using Docker images from Jenkins Pipeline.
Amazon ECR:This plugin provides integration with ECR
CloudBees AWS Credentials:Allows storing Amazon IAM credentials, keys within the Jenkins Credentials API.
Aws Steps:This plugin adds Jenkins pipeline steps to interact with the AWS API.

I added my aws credential for CloudBees AWS Credentials plugin on my Jenkins. And added my github token credentials.

I created jenkins job pipeline and checked GitHub project for my github repository url and checkend GitHub hook trigger for GitScm polling under the Build Trigger tab. I selected Pipeline script from the SCM URL and select the credential i created for GitHub.

I added Webhooks for integrate GitHub and Jenkins. Than i configured with my ec2 public ip because this ip using my jenkins url. I selected just push event.

And ready to build and deploy.
