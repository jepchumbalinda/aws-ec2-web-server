# aws-ec2-web-server

AWS EC2 web server deployment with an automated User Data script that provisions Nginx or Apache on a Free Tier instance. I built it twice to compare setups: Ubuntu with Nginx, and Amazon Linux with Apache.

## What I built
- Launched t2.micro EC2 instances on Ubuntu Server 22.04 LTS and Amazon Linux.
- Configured security groups to allow only SSH (port 22) and HTTP (port 80).
- Installed and started Nginx on Ubuntu and Apache httpd on Amazon Linux, automated with a Bash User Data script.
- Deployed a custom static webpage reachable at each instance's public IP.
- Connected with key-pair SSH from a terminal and from VS Code Remote - SSH.
- Terminated the instances after testing to avoid charges.

## Setup
1. EC2 > Launch instance. Name: MyLinux Server. Type: t2.micro. Key pair: lilokey.pem.
2. AMI: Ubuntu Server 22.04 LTS (Nginx build) or Amazon Linux (Apache build).
3. Security group: allow SSH (22) and HTTP (80).
4. Connect with the key pair (use the instance's public IP) from the AWS instance IP address section.

# My key
chmod 400 lilokey.pem
ssh -i lilokey.pem ubuntu@<public-ip>      # Ubuntu
ssh -i lilokey.pem ec2-user@<public-ip>    # Amazon Linux

Web server installation:

# Ubuntu + Nginx
sudo apt update && sudo apt install nginx -y
sudo systemctl start --nginx
sudo systemctl enable --nginx

# Amazon Linux + Apache
sudo yum install httpd -y
sudo systemctl start --httpd
sudo systemctl enable --httpd

Put the custom page at /var/www/html/index.html and open http://<public-ip>.

## Differences between the two builds
- Apache is apache2 on Ubuntu and httpd on Amazon Linux.
- The default SSH user is ubuntu on Ubuntu and ec2-user on Amazon Linux.
- Package managers differ: apt on Ubuntu, yum on Amazon Linux.

## Security notes
- Only ports 22 and 80 are open on the security group.
- The private key is set to chmod 400; SSH rejects keys other users can read.
- Beyond a demo, I would restrict SSH to my own IP instead of 0.0.0.0/0 and serve over HTTPS instead of plain HTTP.

## Tools I used
AWS EC2, Ubuntu, Amazon Linux, Nginx, Apache, Bash, SSH, VS Code Remote - SSH

