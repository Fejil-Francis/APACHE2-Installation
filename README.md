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
## For stopping Apache2 
 ```bash
sudo systemctl stop apache2
```
<img width="751" height="316" alt="status" src="https://github.com/user-attachments/assets/b65f239a-e45b-4349-ad09-f2f3c1e5b068" />

## Copy your website files to the Apache default directory:
 ```bash
cd /var/www/html
```
## Find Your IP Address,look for the inet value (eg: 192.168.1.10).
```bash
ifconfig eth0
```
## For hosting the website, open a web browser and enter your IP address. If your files are in /var/www/html/, they will be served automatically, and your web server will be hosted.
## When the IP address is entered in the browser, a page similar to the one shown below will appear.

<img width="567" height="232" alt="indexof" src="https://github.com/user-attachments/assets/9f922003-ba3a-46da-922c-799d8903e0e4" />

## Once the i.txt file is opened,
<img width="528" height="300" alt="helloindex" src="https://github.com/user-attachments/assets/1b13ebb8-9ee6-4a78-bcc3-08f79d348ba8" />

By default, Apache displays the index.html file when accessing a directory. To view all files in the directory, delete the index.html file. After removing index.html, the remaining files in the directory will be displayed.


--------------------------------------------------

## Hosting files from home directory by using apache2

By default, Apache serves files from /var/www/html.  
In this setup, Apache is reconfigured to serve files from:

/home/username/data

This is useful for lab environments, testing, and development systems.

--------------------------------------------------

Assumptions

• Username: username  
• Folder to host: /home/username/data  
• Apache2 is already installed and running  

Replace `username` with your actual system username.

--------------------------------------------------

Step 1: Set Permissions for Home and Data Folder

Apache must be able to access the home directory and read files inside the
data folder.

Commands:

 ```bash
chmod 711 /home/username
 ```

 ```bash
chmod -R 755 /home/username/data  
 ```
--------------------------------------------------

Step 2: Change Apache Default Document Root

Open the default Apache virtual host configuration file:

 ```bash
sudo nano /etc/apache2/sites-available/000-default.conf
 ```
Locate:

DocumentRoot /var/www/html

Replace it with:

DocumentRoot /home/username/data

Save and exit the file.

--------------------------------------------------

Step 3: Allow Apache Access to the New Directory

Edit Apache’s main configuration file:

 ```bash
sudo nano /etc/apache2/apache2.conf
 ```

Add the following block at the end of the file:

<Directory /home/username/data>
    AllowOverride All
    Require all granted
</Directory>

Save and exit.

--------------------------------------------------

Step 4: Start Apache2

Apply the configuration changes:

 ```bash
sudo systemctl restart apache2
 ```

--------------------------------------------------

Step 6: Verify in Browser

Open a web browser and visit:

http://localhost

If configured correctly, the test page will be displayed.

--------------------------------------------------

Common Issues

• 403 Forbidden error  
  → Check permissions on /home/username and /home/username/data  

• Page not loading  
  → Ensure Apache was restarted after configuration changes  

--------------------------------------------------

Use Cases

• Development and testing labs  
• Hosting files from user-controlled directories  
• Learning Apache configuration and permissions  

--------------------------------------------------


