# Security Group Rules

**Security Group Name:** web-server-sg  
**VPC:** my-custom-vpc  
**Region:** ap-south-1 (Mumbai)

---

## Inbound Rules

| Type | Protocol | Port | Source | Reason |
|---|---|---|---|---|
| SSH | TCP | 22 | My IP only | Secure admin access — restricted to my IP |
| HTTP | TCP | 80 | 0.0.0.0/0 | Public website access for all users |

## Outbound Rules

| Type | Protocol | Port | Destination |
|---|---|---|---|
| All traffic | All | All | 0.0.0.0/0 (default) |

---

## Why These Rules?

### Port 80 — HTTP — Open to Everyone
The web server needs to serve pages to anyone who visits.
Allowing 0.0.0.0/0 on port 80 means any browser can load the site.

### Port 22 — SSH — My IP Only
SSH gives direct command-line access to the server.
Opening port 22 to everyone (0.0.0.0/0) is a major security risk
as bots constantly scan for open SSH ports.
Restricting to My IP follows the **principle of least privilege** —
only I can access the server remotely.

### Why HTTPS (443) is Not Included?
This project uses HTTP only. HTTPS requires an SSL certificate
which would need Route 53 or a domain name. That is a future
enhancement — adding CloudFront + ACM certificate.

---

## Security Concepts Applied

- **Principle of Least Privilege** — only ports that are needed are open
- **Defense in Depth** — Security Group acts as a stateful firewall at instance level
- **Restrict Admin Access** — SSH limited to trusted IP only
- **Stateful Firewall** — Security Groups automatically allow return traffic

---

*Part of AWS EC2 + VPC Cloud Portfolio Project by Swapnil Thik*
