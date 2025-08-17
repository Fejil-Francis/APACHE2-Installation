# 🌐 Apache2 Installation & Website Hosting Guide

## 📖 What is Apache2?
Apache2 (Apache HTTP Server) is a **free, open-source web server** developed by the **Apache Software Foundation**.  
It is used to serve websites, web applications, and files over the internet or local networks.

### 💡 Uses of Apache2
- **Host Websites** – Serve HTML, CSS, JavaScript, and images to users.
- **Run Web Applications** – Deliver dynamic content with languages like PHP or Python.
- **Local Development** – Test websites on your own computer before going live.
- **Serve Files** – Share files for download.
- **Reverse Proxy & Load Balancing** – Distribute requests across multiple servers.
- **Multiple Websites** – Host several domains on a single server using virtual hosts.

---

## 🛠 Installation & Setup Commands

## Install Apache2
```bash
sudo apt-get install -y apache2
```
## Enable Apache2 to Start on Boot
```bash
sudo systemctl enable apache2
```
## Start Apache2 Service
```bash
sudo systemctl start apache2
```
## Check Apache2 Status
 ```bash
sudo systemctl status apache2
```
<img width="751" height="316" alt="status" src="https://github.com/user-attachments/assets/b65f239a-e45b-4349-ad09-f2f3c1e5b068" />

## Copy your website files to the Apache default directory:
 ```bash
cd /var/www/html
```
## Find Your IP Address,look for the inet value (e.g., 192.168.1.10).
```bash
ifconfig eth0
```
## For hosting the website, open a web browser and enter your IP address. If your files are in /var/www/html/, they will be served automatically, and your web server will be hosted.
## When the IP address is entered in the browser, a page similar to the one shown below will appear.

<img width="567" height="232" alt="indexof" src="https://github.com/user-attachments/assets/9f922003-ba3a-46da-922c-799d8903e0e4" />

## When the i.txt file is opened,
<img width="528" height="300" alt="helloindex" src="https://github.com/user-attachments/assets/1b13ebb8-9ee6-4a78-bcc3-08f79d348ba8" />
