#!/bin/bash

# Update package manager
sudo apt-get update -y

# Install dependencies (including webrick for Ruby 3+ support on newer Ubuntu)
sudo apt-get install ruby-full ruby-webrick wget unzip -y

# Change to a safe working directory
cd /home/ubuntu

# Download and execute the CodeDeploy agent for Mumbai region
wget https://aws-codedeploy-ap-south-1.s3.ap-south-1.amazonaws.com/latestv2/install
chmod +x ./install
sudo ./install auto

# Enable the service to start on boot and start it immediately
sudo systemctl enable codedeploy-agent
sudo systemctl start codedeploy-agent
