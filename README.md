# 🧠 AUTO-SCALING-WITHOUT-LB

🚀 Hands-on project demonstrating **AWS EC2 Auto Scaling without a Load Balancer** — using **EC2, AMI, Launch Template, and Auto Scaling Group** to achieve **high availability**, **fault tolerance**, and **automated recovery** in the AWS Cloud environment.

---

## 🌐 Overview :-

This project showcases how AWS Auto Scaling can automatically maintain the number of EC2 instances required to handle application traffic — even **without using a Load Balancer**.  

It helps achieve:

- ✅ **Resilience**
- ✅ **Self-healing**
- ✅ **Cost optimization**  
using only core AWS compute and scaling features.


---
## 📝 Prerequisites :-

Before starting, ensure you have:

- An **AWS Account** with necessary permissions
- Basic knowledge of **EC2, AMI, and Auto Scaling**
- **SSH client** (PowerShell, Terminal, or PuTTY)
- A **Key Pair** for EC2 instance access
- Familiarity with **Ubuntu and Nginx**

----
## 🪜 Step-by-Step Implementation

### 1. 💡 Launch EC2 Instance :-

- **Operating System:** Ubuntu  
- Created or selected a **Key Pair** for SSH access  
- Enabled **Auto-assign Public IP**  
- Created a new **Security Group** named `launch-wizard-6`  
- Edited **Inbound Rules:**
  - **Type:** HTTP  
  - **Source:** Anywhere (IPv4)  

---

### 2. 🛠️ Configure EC2 and Deploy Nginx :-

1] Connected to the EC2 instance via PowerShell:
```bash
ssh -i <path_to_keypair> ubuntu@<public_ip>
```

2] Installed and started **Nginx**:
```bash
sudo apt-get update
sudo apt-get install nginx -y
sudo systemctl start nginx
sudo systemctl enable nginx.service
```

3] Replaced the default web page:
```bash
cd /var/www/html
sudo rm index.nginx-debian.html
sudo nano index.html
```

4] Added:
```html
<h1>Welcome to Auto Scaling</h1>
```

5] Verified by visiting:
```
http://<public_ip>
```

---

### 3. 🧩 Create an AMI :-

- Selected the running EC2 instance → **Actions → Image and Templates → Create Image**  
- Named and created the **AMI**  
- Waited until AMI status became **Available**  
- Terminated the original instance  

---

### 4. 📝 Create Launch Template :-

- Created a new **Launch Template**  
- Under **Application and OS Images (Amazon Machine Image)** → Selected **My AMIs**  
- **Instance Type:** t2.micro (or any desired type)  
- Selected the same **Key Pair** and **Security Group (launch-wizard-6)**  

---

### 5. ⚙️ Configure Auto Scaling Group (ASG) :-

- Created an **Auto Scaling Group** linked to the Launch Template  
- Selected **2 or more Subnets** for high availability  
- Skipped **Load Balancer** configuration (selected *No Load Balancer*)  
- Updated **Health Check Grace Period** from `300s` to `30s`  
- Accepted default scaling settings and launched the ASG  

---

### 6. 💡 Testing Auto Scaling :-

- Verified that the Auto Scaling Group automatically launched an instance  
- Manually **terminated one instance** and observed that a new one was created automatically within ~30 seconds  
- Confirmed **fault tolerance** and **auto recovery** functionality successfully  

---

## 🧩 Key Points :-

✅ Demonstrated **EC2 setup and configuration**  
✅ Created and used a **custom AMI** for scaling  
✅ Implemented **Auto Scaling** without a Load Balancer  
✅ Understood **fault tolerance** and **automated recovery** in AWS  
✅ Practiced **real-world scaling and resilience** for cloud systems  

---

## ⚙️ Technologies Used :-

| Technology | Purpose |
|-------------|----------|
| **AWS EC2** | Compute service for instance deployment |
| **Amazon Machine Image (AMI)** | Custom reusable image for new instances |
| **Launch Template** | Defines instance configuration (AMI, type, key, SG) |
| **Auto Scaling Group (ASG)** | Automates instance scaling and recovery |
| **Ubuntu + Nginx** | OS and web server for testing the setup |

---

## 🧱 Architecture Diagram :-

```
User Request → Auto Scaling Group → EC2 Instances (Ubuntu + Nginx)
```

## 💡 **Core Concept:** :-

When an instance fails or is terminated, the Auto Scaling Group immediately launches a replacement instance using the predefined Launch Template — ensuring uptime and stability without manual intervention.

## 📊 Benefits of This Setup :-

✅ High Availability without LB

✅ Automated Recovery of failed instances

✅ Cost Optimization by scaling based on demand

✅ Hands-on learning of AWS Auto Scaling features

---

## 💡 Notes & Tips

🔹Always use tags for resources to easily identify them

🔹Adjust scaling policies according to traffic needs

🔹Test fault tolerance by terminating instances manually

🔹Consider ALB integration for real-world production scenarios

## 🚀 Future Enhancements :-

🔹 **Integrate an Application Load Balancer (ALB)** for traffic distribution across multiple instances  

🔹 **Add CloudWatch Monitoring** to visualize scaling metrics (CPU, Memory, Network)  

🔹 **Use SNS Notifications** to receive alerts on scaling events  

🔹 **Implement Lifecycle Hooks** for custom actions during instance launch/terminate  

🔹 **Automate Deployment** using Infrastructure as Code (Terraform or CloudFormation)

---

## 📸 Example Screenshots

| Screenshot | Description |
|------------|-------------|
| EC2 Instance setup and Auto Creation |
| Launch Template configuration |
| Auto Scaling Group overview |
| AMI |

💡 **Tip:** Place all your screenshots inside a `Images` folder in your repo for clean structure.

---

## 🧭 Author :-
**Prasad**  
☁️ Cloud & DevOps Learner | AWS Practitioner  

---

✨ *A simple, scalable, and self-healing AWS project — perfect for learners exploring Auto Scaling without Load Balancers!* ☁️

## 📩 Connect With Me :
If you’d like to collaborate, discuss projects, or just say hello — feel free to reach out!  

### 🔗 Social & Professional Links:
- 🌐 [Portfolio Website](https://prasad-bhoite19.github.io/prasad-portfolio/)  
- 💼 [LinkedIn](http://linkedin.com/in/prasad-bhoite-a38a64223)  
- 🐙 [GitHub](https://github.com/Prasad-bhoite19)  
- ✉️ [Email](prasadsb2002@gmail.com)  

💬 Always open for opportunities in **Cloud, DevOps, and Full-Stack Projects**
