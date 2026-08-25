#!/bin/bash
# Update package manager and repository lists
sudo apt update -y

# Install dependencies (Ruby and wget are required for CodeDeploy)
sudo apt install ruby-full wget -y

# Change to a safe working directory for the default Ubuntu user
cd /home/ubuntu

# Download the latest CodeDeploy agent installer for the Mumbai region
wget https://aws-codedeploy-ap-south-1.s3.ap-south-1.amazonaws.com/latestv2/install

# Make the installer executable and run the installation setup
chmod +x ./install
sudo ./install auto

# Enable the service to start on boot and start it immediately
sudo systemctl enable codedeploy-agent
sudo systemctl start codedeploy-agent
