---

# Host a Static Website on AWS

## 📌 Project Overview

This project demonstrates how to host a static HTML web application on AWS using a scalable, secure, and fault-tolerant architecture. The infrastructure leverages AWS services such as EC2, VPC, Load Balancer, Auto Scaling, Route 53, and more.

It covers:

🏗 Building a multi-AZ AWS network infrastructure
⚙ Deploying EC2 instances in private subnets with an Application Load Balancer
🌍 Configuring Route 53 & HTTPS via AWS Certificate Manager
📢 Setting up SNS notifications for Auto Scaling events
📎 GitHub Repository: Host-a-static-website-on-aws

The project includes:

* A detailed reference architecture diagram
* Deployment scripts for setting up the environment on AWS
* Steps to host the website on EC2 instances

---

## 🛠 AWS Architecture

1. **Virtual Private Cloud (VPC)** with public and private subnets across two Availability Zones.
2. **Internet Gateway** for connectivity between the VPC and the internet.
3. **Security Groups** to control inbound and outbound traffic.
4. **Multi-AZ Setup** for high availability and fault tolerance.
5. **Public Subnets** for NAT Gateway and Application Load Balancer.
6. **EC2 Instance Connect Endpoint** for secure access to resources in both public and private subnets.
7. **Private Subnets** hosting EC2 instances for enhanced security.
8. **NAT Gateway** to allow instances in private subnets to access the internet.
9. **EC2 Instances** running the website.
10. **Application Load Balancer** with a target group to distribute web traffic evenly.
11. **Auto Scaling Group** to automatically adjust the number of EC2 instances.
12. **GitHub** for version control and collaboration.
13. **AWS Certificate Manager** for securing communication (SSL/TLS for HTTPS)
14. **Amazon SNS** for Auto Scaling activity alerts.
15. **Route 53** for domain registration and DNS configuration.

---

## 🚀 Deployment Script

The project includes a `bash` script for automating the EC2 instance setup:

```bash
#!/bin/bash
sudo su
yum update -y
yum install -y httpd
cd /var/www/html
yum install -y git
git clone https://github.com/CaptainNii/Host-a-static-website-on-aws.git
cp -R Host-a-static-website-on-aws/. /var/www/html/
rm -rf Host-a-static-website-on-aws
systemctl enable httpd
systemctl start httpd
```

> **Note:** Ensure that the GitHub repository URL in the script is correct before running.

---

## 📂 Repository Structure

```
/ (root)
│── architecture-diagram.png   # Reference architecture
│── setup-script.sh            # EC2 setup script
│── index.html                  # Website entry point
│── README.md                   # Documentation
```

---

## 📧 Notifications

SNS is configured to send alerts about Auto Scaling activities. Ensure that your subscription is active to receive notifications.

---

## 🔐 Security

* All web traffic is secured with **HTTPS** via AWS Certificate Manager.
* Web servers are placed in private subnets, accessible only through the load balancer.

---


