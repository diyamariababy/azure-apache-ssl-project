# Secure Website Hosting on Azure VM with Apache and Let's Encrypt SSL

This project demonstrates how to securely host a website using an **Azure Virtual Machine (VM)** running **Apache2** and secured with an **SSL certificate** from Let's Encrypt using **Certbot**. The domain used in this project is `azuredevopsk.xyz`.

---

## Project Overview

- **Cloud Provider**: Microsoft Azure  
- **Web Server**: Apache2 on Ubuntu 22.04 VM  
- **SSL**: Let's Encrypt (Certbot)  
- **Domain Name**: `azuredevopsk.xyz` (managed via GoDaddy)  
- **Tools Used**: Azure Portal, Certbot, Apache, Git, Linux CLI  

This project showcases my ability to:
- Deploy and configure infrastructure in Azure
- Install and configure Apache web server
- Secure a website using HTTPS and SSL certificates
- Configure DNS and domain routing
- Use Linux CLI for DevOps tasks

---

## Steps Performed

### 1. Provisioned an Azure VM
- Created an **Ubuntu 22.04 LTS** Virtual Machine via Azure Portal
- Chose **Standard B1s** SKU for basic demo setup
- Enabled **inbound ports 22 (SSH), 80 (HTTP), and 443 (HTTPS)** using Network Security Group (NSG) rules

> Screenshot: ![VM Created](./screenshots/VM%20Created.png)

---

### 2. Installed Apache Web Server
- sudo apt update
- sudo apt install apache2 -y

### Confirmed Apache was running using 
sudo systemctl status apache2

> Screenshot: ![Apache Installation](./screenshots/Apache%20Installation.png)

### 3. Set Up Custom Domain
- Purchased domain azuredevopsk.xyz from GoDaddy<br>
- Updated DNS A record in GoDaddy to point to the VM’s public IP<br>
  A   @     → <VM_Public_IP><br>
  A   www   → <VM_Public_IP><br>
  CNAME www → azuredevopsk.xyz (optional)

> Screenshot: ![Custom Domain](./screenshots/Custom%20Domain.png)

### 4. Installed Certbot & Obtained SSL Certificate
sudo apt install certbot python3-certbot-apache -y

# Requested certificate with Certbot
sudo certbot --apache -d azuredevopsk.xyz -d www.azuredevopsk.xyz

- Chose option to redirect HTTP to HTTPS
- SSL was installed successfully

> Screenshot: ![Certificate Installation](./screenshots/Certificate%20Installation.png)
> Screenshot: ![Certificate](./screenshots/Certificate.png)

### 5. Security Hardening (Optional)
- *Edited SSH configuration:*<br>
  sudo nano /etc/ssh/sshd_config<br>
- *Changed:*<br>
  PermitRootLogin no<br>
  PasswordAuthentication no<br>
- *Then restarted SSH:*<br>
  sudo systemctl restart ssh

### 6. Verified HTTPS Access
- Accessed https://azuredevopsk.xyz in browser
- Saw valid SSL certificate from Let's Encrypt
- Site automatically redirected from HTTP to HTTPS

Screenshot: ![HTTPS Verification](./screenshots/HTTPS%20Verification.png)

### 7. Custom Webpage (Optional)
- can host your own simple HTML:<br>
  echo "<h1>Hello Secure Web World</h1>" | sudo tee /var/www/html/index.html

> Screesnshot: ![Custom Webpage](./screenshots/Custom%20Webpage.png)

### Conclusion
This project allowed me to apply and reinforce real-world Azure and Linux skills, from VM provisioning to SSL configuration. It showcases my ability to deploy and secure infrastructure in the cloud - an essential skill in cloud and DevOps roles.