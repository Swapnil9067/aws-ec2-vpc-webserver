# VPC Architecture

**VPC Name:** my-custom-vpc  
**Region:** AWS ap-south-1 (Mumbai)

---

## Network Design

| Component | Name | Value |
|---|---|---|
| VPC | my-custom-vpc | 10.0.0.0/16 |
| Public Subnet | my-public-subnet | 10.0.1.0/24 |
| Availability Zone | — | ap-south-1a |
| Internet Gateway | my-igw | Attached to VPC |
| Route Table | — | 0.0.0.0/0 → my-igw |
| Security Group | web-server-sg | Port 80 + Port 22 |
| EC2 Instance | my-web-server | t3.micro, Amazon Linux 2023 |

---

## Architecture Diagram

```
Internet (Users)
      |
      | HTTP port 80
      v
Internet Gateway (my-igw)
      |
      v
VPC: 10.0.0.0/16 (my-custom-vpc)
      |
      v
Route Table: 0.0.0.0/0 → my-igw
      |
      v
Public Subnet: 10.0.1.0/24 (ap-south-1a)
      |
      v
Security Group (web-server-sg)
  - Inbound: Port 80 open to all
  - Inbound: Port 22 restricted to My IP
      |
      v
EC2 Instance (my-web-server)
  - Type: t3.micro
  - OS: Amazon Linux 2023
  - Web Server: Apache (httpd)
      |
      v
index.html served on Public IP
```

---

## CIDR Block Explanation

| CIDR | Range | Hosts |
|---|---|---|
| 10.0.0.0/16 | VPC — full network | 65,536 IPs |
| 10.0.1.0/24 | Public subnet | 256 IPs |

**Why /16 for VPC?**
Gives room to add more subnets in future
(private subnet, database subnet etc.)

**Why /24 for subnet?**
256 IPs is more than enough for a small project.
In real production you plan subnets carefully for growth.

---

## Why Custom VPC Instead of Default VPC?

| | Default VPC | Custom VPC |
|---|---|---|
| Created by | AWS automatically | You manually |
| Understanding needed | None | Full networking knowledge |
| Interview value | Low | High |
| Control | Limited | Full control |
| Best practice | Dev/test only | Production standard |

Using a custom VPC demonstrates understanding of:
- CIDR block planning
- Subnet design and segmentation
- Internet Gateway attachment
- Route table configuration
- Network isolation concepts

---

## Key Networking Concepts Used

- **VPC** — Isolated virtual network inside AWS
- **CIDR** — IP address range notation (10.0.0.0/16)
- **Subnet** — Segment of VPC IP range in one AZ
- **Internet Gateway** — Allows VPC to communicate with internet
- **Route Table** — Rules deciding where network traffic goes
- **Security Group** — Stateful firewall at EC2 instance level
- **Public Subnet** — Subnet with route to Internet Gateway

---

*Part of AWS EC2 + VPC Cloud Portfolio Project by Swapnil Thik*  
*AWS Certified Cloud Practitioner (2026) | Fortinet NSE3 (2025)*
