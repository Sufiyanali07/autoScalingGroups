# Auto Scaling Group Setup Guide

This guide provides step-by-step instructions to set up an Auto Scaling Group (ASG) with a launch template, enable dynamic scaling based on CPU utilization, and monitor instance activity.

## Launch Template Configuration

1. **Create a Launch Template:**
   - Open the AWS Management Console and navigate to EC2.
   - Click on "Launch Templates" and then "Create launch template".
   - Choose an Amazon Machine Image (AMI).
   - Select the EC2 key pair for SSH access.
   - Configure security group to allow all traffic.
   - Enable detailed monitoring.

## Auto Scaling Group Configuration

2. **Create an Auto Scaling Group:**
   - In the AWS Management Console, navigate to the Auto Scaling Groups section.
   - Click on "Create Auto Scaling Group".
   - Choose the launch template created earlier.
   - Configure the desired capacity, minimum and maximum size of the ASG.
   - Set up dynamic scaling policy based on CPU utilization.

## Increasing Load and Monitoring

3. **SSH to EC2 Instance and Install Stress:**
   - Connect to your EC2 instance using SSH.
   - Install stress using the following command:
     ```
     sudo yum install stress -y
     ```
   - Run stress command to increase CPU load:
     ```
     stress --cpu 2
     ```

4. **Check CPU Utilization:**
   - Monitor CPU utilization on the EC2 instance for 10 minutes or more.

5. **Check Auto Scaling Activity:**
   - Navigate to the Auto Scaling Group in the AWS Management Console.
   - Go to the "Activity" tab to monitor scaling activities.
   - You should observe a new instance being created based on increased CPU utilization.

## Termination

6. **Delete Auto Scaling Group:**
   - In the Auto Scaling Group section of the AWS Management Console, select the ASG you created.
   - Click on "Actions" and then "Delete Auto Scaling Group".
   - Confirm deletion to terminate instances associated with the ASG.

## Important Note
Do not terminate the EC2 instances manually. Deleting the Auto Scaling Group will handle termination based on the scaling policies configured.

