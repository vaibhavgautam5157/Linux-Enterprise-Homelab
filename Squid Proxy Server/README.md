# 🦑 Squid Proxy Server – Linux Enterprise Homelab

- **Squid is a type of proxy server that helps manage internet traffic.**
- **It acts as a middleman between your device and the websites you visit, and it is especially good at speeding things up.**
- **Squid stores copies of websites and files that people access frequently. When someone requests the same content again, Squid can provide it faster without downloading it from the internet again.**
- ***It also helps save bandwidth and can block certain websites or control access.***

- **Port number: 3128**
- **config file: squid.config**
- **config file location: /etc/squid/squid.config**

---

## 📌 **Project Overview**

In this project, I configured a **Squid Proxy Server** to control internet access for client machines ***within a private network***. The setup includes installation, configuration of ACLs (Access Control Lists), blocking specific websites, and routing client traffic through the proxy server.

This is a hands-on demonstration of how organizations use proxies to enforce internet usage policies and enhance network security.

---

## 🧩 **Features Implemented**

✔ Installed and configured **Squid Proxy** on CentOS  
✔ Set custom **ACL rules** to restrict access  
✔ Blocked specific websites (e.g., Facebook, YouTube)  
✔ Configured client machine to route traffic through Squid  
✔ Verified proxy functionality using logs and browser testing  
✔ Enabled HTTP port 3128 for communication  
✔ Implemented basic proxy authentication (optional based on setup)


---

## 🚀 **Steps Performed**

- ***logging into server machine***
  
<img width="1275" height="793" alt="1_cheking username and ip" src="https://github.com/user-attachments/assets/f73d6beb-7a78-4faf-a0d3-747023b88428" />

### 1️⃣ Install Squid Proxy  
```
sudo dnf install squid -y
```
<img width="1269" height="796" alt="2_checking and install squid package" src="https://github.com/user-attachments/assets/7b6ccc0b-0a67-4106-80f5-ab02236d49c6" />


### 2️⃣ Start & enable the service
```
sudo systemctl start squid
sudo systemctl enable squid
sudo systemctl status squid
```
<img width="1268" height="802" alt="3_starting squid package" src="https://github.com/user-attachments/assets/9d384a87-5a40-459f-813d-d526983746ef" />


### 3️⃣ Configure ACLs (Access Control Lists)
- Edited /etc/squid/squid.conf to:

  - Allow internal network access

  - Block specific websites

  -  Control who can use the proxy


```
vi /etc/squid/squid.config
```
```
acl localnet src < ip_address >
acl blocksites url_regex " /etc/squid/blocksites "
http_access deny blocksites
http_access allow localne
```
<img width="1275" height="797" alt="5_adding script" src="https://github.com/user-attachments/assets/7bf43566-9726-4de4-9cfc-93d7eb5671ff" />


### 4️⃣ Create blocksite file in /etc/squid/ 
- create another file in /etc/squid/ directory
- add websites want to get blocked
```
vi /etc/squid/blocksites
```
- eq: facebook
```
facebook.com
```
<img width="1274" height="745" alt="6_adding script in blocksite file" src="https://github.com/user-attachments/assets/336704d3-b860-4123-8752-c76d9a66d8d6" />


### 5️⃣ Configure Firewall
```
sudo firewall-cmd --add-port=3128/tcp --permanent
sudo firewall-cmd --reload
```
<img width="1272" height="801" alt="7_configuring firewall" src="https://github.com/user-attachments/assets/93ba21f4-8244-4c11-be49-38fac53fee00" />


### 6️⃣ Configure Client System
- On the client machine:

  - Open browser settings

  - Set Manual Proxy

  - HTTP Proxy: server-ip-address

  - Port: 3128
<img width="1279" height="766" alt="9_cheking ip of client machine" src="https://github.com/user-attachments/assets/052ad99b-4049-407a-98b1-e9131ca3d543" />
<img width="1269" height="784" alt="10_opening setting of browser" src="https://github.com/user-attachments/assets/68172ac0-29c0-4b8a-a478-7b5a9d87ad8b" />
<img width="1270" height="785" alt="11_selecting network setting" src="https://github.com/user-attachments/assets/4f262640-4e7b-476d-b9b1-780e9168a7d3" />
<img width="1274" height="796" alt="12_manual proxy config" src="https://github.com/user-attachments/assets/e66b7079-445d-4252-b726-2770b22a972c" />



### 7️⃣ Test & Validate

- Access unblocked websites → Success

- Try to access blocked websites → **Successfully blocked**

- Verified logs in /var/log/squid/access.log

---
<img width="1278" height="801" alt="13_ checking unblocked sites" src="https://github.com/user-attachments/assets/143c383b-d281-4c91-ab43-d948ca2af165" />
<img width="1286" height="655" alt="14_bloclked site" src="https://github.com/user-attachments/assets/33c4f4ed-5174-47c1-bd1e-29976d575246" />


## 🎯 Learning Outcomes
**This project taught me:**

- How proxy servers work in real enterprise environments

- How to enforce internet policies using ACLs

- How clients route traffic through a proxy

- How to block websites, monitor logs, and control access

- How organizations control browsing for security & productivity


## 📝 Future Enhancements
Add LDAP/AD-based authentication

Implement HTTPS filtering

Configure caching for performance improvement

Deploy Transparent Proxy using iptables
