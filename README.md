# EC2 Web Server on Custom VPC

**Live IP:** http://[YOUR-EC2-PUBLIC-IP](http://13.235.244.86/) (Stop/Start changes IP)  
**Region:** AWS ap-south-1 (Mumbai)

---

## About This Project

An Apache web server deployed on Amazon EC2 (t2.micro) 
inside a custom VPC with public subnet, internet gateway, 
and security group configuration.

---

## Screenshots

### Live Website
![Website](screenshots/website.png)

### EC2 Instance Running
![EC2](screenshots/ec2-instance.png)

### VPC Configuration
![VPC](screenshots/vpc.png)

### Security Group Rules
![Security Group](screenshots/security-group.png)

---

## Architecture
Internet → IGW → VPC (10.0.0.0/16) →
Public Subnet (10.0.1.0/24) →
Security Group → EC2 t2.micro → Apache

---

## What I Built

- Custom VPC with CIDR 10.0.0.0/16
- Public subnet in ap-south-1a
- Internet Gateway attached to VPC
- Route table with 0.0.0.0/0 → IGW
- Security Group: HTTP open, SSH restricted to My IP
- EC2 t2.micro with Amazon Linux 2023
- Apache web server installed via User Data script
- Webpage accessible via EC2 public IP

---

## Services Used

| Service | Purpose |
|---|---|
| Amazon EC2 | Virtual server (t2.micro) |
| Amazon VPC | Custom isolated network |
| Subnet | Public network segment |
| Internet Gateway | Internet access for VPC |
| Route Table | Traffic routing rules |
| Security Group | Firewall — port 80 and 22 |
| IAM | EC2 access control |

---

## What I Learned

- VPC creation and CIDR block planning
- Subnet and Internet Gateway configuration
- Route table setup for internet access
- Security Group rules and least privilege
- EC2 launch with custom networking
- User Data script for automated server setup
- Apache web server installation on Linux

---

## About Me

**Swapnil Thik** — Network Engineer transitioning to Cloud  
AWS Certified Cloud Practitioner (2026) | Fortinet NSE3 (2025)  
[LinkedIn](https://linkedin.com/in/swapnil-thik) | 
[GitHub](https://github.com/Swapnil9067)

