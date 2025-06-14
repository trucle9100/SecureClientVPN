# 🔒 Secure Client VPN to EC2: AWS Private Access Lab  
*Configure a secure, certificate-based VPN tunnel to private EC2 instances using AWS Client VPN*  

[![AWS](https://img.shields.io/badge/AWS-FF9900?logo=amazonaws&logoColor=white)](https://aws.amazon.com) 
[![Terraform](https://img.shields.io/badge/Infrastructure-As__Code-7B42BC?logo=terraform)](https://terraform.io)  
[![License](https://img.shields.io/badge/License-MIT-blue)](LICENSE)

---

## 📌 Lab Objectives  
✅ **Secure Access**: Certificate-based VPN authentication  
✅ **Private Networking**: Isolate EC2 instances in private subnets  
✅ **High Availability**: Multi-AZ VPN endpoint deployment  
✅ **Cost Control**: Automated cleanup scripts  

---

## 🛠️ Technologies Used  
- **AWS Services**: Client VPN, VPC, EC2, ACM, IAM  
- **Security**: TLS certificates, Security Groups, Least-Privilege Access  
- **Automation**: AWS CLI, CloudFormation (optional)  

---

## 🏗️ Architecture  
![AWS Client VPN Architecture](diagram/SimpleClientDiagram.drawio.png)  
*Data Flow*:  
`Client Device → VPN Endpoint (192.168.0.0/22) → Private EC2 (10.0.3.0/24)`  

---

## 📋 Step-by-Step Guide  
### **1. VPC Setup**  
- **Public Subnets**: `10.0.1.0/24`, `10.0.2.0/24` (multi-AZ)  
- **Private Subnet**: `10.0.3.0/24`  

### **2. Certificate Setup**  
- ACM public certificate for `vpn.yourdomain.com` (DNS validation)  

### **3. VPN Endpoint**  
- **Client CIDR**: `192.168.0.0/22`  
- **Authentication**: Certificate-based (ACM)  

### **4. Testing**  
```bash
# Connect via VPN (OpenVPN config)
sudo openvpn --config client-config.ovpn

# SSH to private EC2
ssh -i key.pem ec2-user@10.0.3.10
```

---

## 📸 Screenshots  
| Component | Visual |  
|-----------|--------|  
| **VPN Endpoint** | ![Endpoint](screenshots/vpn-endpoint.png) |  
| **Connected Client** | ![VPN Connected](screenshots/vpn-connected.png) |  
| **Security Group** | ![Security Group](screenshots/sg-rules.png) |  

---

## 🚀 Quick Deployment  
### **1. Clone the Repository**  
```bash
git clone https://github.com/your-repo/aws-client-vpn-lab.git
cd aws-client-vpn-lab
```
