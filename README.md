############ Userdata for Ec2 instance ################


#!/bin/bash
# Update package manager
sudo yum update -y

# Install dependencies (Ruby is required for CodeDeploy)
sudo yum install ruby wget -y

# Change to a safe working directory
cd /home/ec2-user

# Download the latest CodeDeploy agent for Mumbai region
wget https://aws-codedeploy-ap-south-1.s3.ap-south-1.amazonaws.com/latestv2/install

# Make it executable and run the installation
chmod +x ./install
sudo ./install auto

# Enable and start the agent service
sudo systemctl enable codedeploy-agent
sudo systemctl start codedeploy-agent
