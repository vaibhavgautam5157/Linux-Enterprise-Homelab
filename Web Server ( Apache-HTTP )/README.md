# 🖥️ Apache HTTP Web Server Setup on CentOS  
_A Hands-on Linux Enterprise Homelab Project_

This project demonstrates the complete setup and configuration of an **Apache HTTP Web Server** on a CentOS-based Linux system.  
It includes installation, service management, firewall configuration, custom webpage deployment, troubleshooting, and verification.

This homelab project helps build practical Linux system administration skills relevant for **DevOps, SysAdmin, and Cloud roles**.

---

## 📌 Project Objectives
- Install and configure the Apache HTTP (`httpd`) server
- Start, enable, and manage the httpd service
- Deploy a custom webpage in `/var/www/html`
- Disable firewalld (for testing purposes)
- Verify the web server through a browser
- Fix the issue of default “HTTP Server Test Page”
- Document the setup with screenshots

---

## 🏗️ Tech Stack Used
- **CentOS / RHEL**
- **Apache HTTP Server (httpd)**
- **Linux commands & systemctl**
- **SELinux & Firewalld** (basic handling)
- **Browser for final validation**

---

## 📂 Project Structure

---

## 🚀 Steps Performed

### **1️⃣ Install Apache HTTP Server**

sudo dnf install httpd -y


### 2️⃣ Start & Enable the Service

sudo systemctl start httpd
sudo systemctl enable httpd


### 3️⃣ Check Service Status

sudo systemctl status httpd


### 4️⃣ Create Custom Webpage ( /var/wwww/html )

vi index.html


### 5️⃣ Disable Firewalld for Testing 

sudo systemctl stop firewalld
sudo systemctl disable firewalld


### 6️⃣ Fix Default Test Page Issue

sudo systemctl restart httpd


### 7️⃣ Final Verification
Open browser →

http://server-ip

You will now see your custom webpage.

---

## 🖼️ Screenshots

All screenshots of installation, configuration, troubleshooting, and final output are available in the
/Screenshots folder of this project.



## 🔍 What I Learned

- How Apache HTTPD works internally

- How Linux serves static web content

- Managing services using systemctl

- Understanding default Apache configuration files

- Fixing common issues like the Apache test page

- Hosting a webpage on a Linux server
