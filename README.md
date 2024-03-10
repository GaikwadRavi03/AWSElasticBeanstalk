# Node.js Application Deployment to Elastic Beanstalk using CloudFormation

## Prerequisites

Before beginning, ensure you have the following prerequisites set up:

- Set up a VPC network.
- An AWS account with access of Elastic Beanstalk, EC2, Load Balancer, IAM etc.
- Sample nodejs application zip file uplaod in into s3 bucket bucket
- An IAM role with the necessary permissions for Elastic Beanstalk to deploy your application
- Make sure you've S3 bucket created and required code ZIP available.

## Instructions

Follow these steps at a time of deploy application using CloudFormation:

Upload the CloudFormation template and the application source bundle to an S3 bucket.

Create a new CloudFormation stack using the template, specifying the values in  parameters:
   - AwsVpcID: VPC ID of your existing VPC.
   - AwsEC2SubnetID: Subnet ID that in which avaliability you want to launch that EC2 instances.
   - ProjectEnvironment: The environment of your Elastic Beanstalk project (e.g., dev, qa, stage, uat, prod).
   - EC2InstanceType: Instance type for your EC2 instances.
   - S3BucketName: The name of the S3 bucket where you upload your nodejs code.
   - S3BucketObjectKeyName: The name of the S3 object key name.
   - LBSubnetID: ID of the subnet to create application Load Balancer.
   - LBVisibility: The visibility of LB which is public or private
   - AppPlatformType: The type of solution stack to use for the Elastic Beanstalk application.
   
Create cloudfromation.

## Scaling Policies
CloudFormation scaling policies for the Auto Scaling Group:

- Upper threshold: 80% CPU utilization
- Breach duration: 5 minutes
- Upper breach scale increment: 1 instance
- Lower threshold: 30% CPU utilization
- Lower breach scale increment: -1 instance