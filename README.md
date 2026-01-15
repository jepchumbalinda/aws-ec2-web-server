# aws-ec2-web-server
AWS EC2 web server deployment with automated User Data scripting to provision Nginx/Apache on a Free Tier instance.
# Project Overview
- Launched a t2.micro EC2 instance on Amazon Linux/Ubuntu.
- Configured security groups to allow SSH (port 22) and HTTP (port 80).
- Installed and configured Nginx/Apache web server.
- Deployed a custom static webpage accessible via the public IP.

# Technologies Used
- AWS EC2
- Amazon Linux / Ubuntu
- Nginx or Apache (httpd/apache2)
- VS Studio Code SSH

# Screenshots

  

# Setup Instructions
Step 1: Launch an EC2 Instance
1. In the AWS Management Console, go to EC2 → Launch Instance.
2. Configure:
   - Name: MyLinux Server
   - AMI: Amazon Linux 2023 or Ubuntu Server 22.04 LTS
   - Instance Type: t2.micro 
   - Key Pair: lilokey.pem
   - Security Group: Allow
     - SSH (port 22) – from My IP or Anywhere (for testing)
     - HTTP (port 80) – from Anywhere (0.0.0.0/0)
3. Launch the instance.

# Step 2: Connect to the Instance 
ssh -i your-key.pem ec2-user@<public-ip>   Amazon Linux

ssh -i your-key.pem ubuntu@<public-ip>     Ubuntu

