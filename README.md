# 🌩️ Rutika Kale Cloud Engineering Portfolio

This repository contains my personal portfolio website, showcasing my skills as a Cloud Engineering Specialist. This is my first simple project deployed on an AWS EC2 instance.

## 🎯 Project Goal

#### The main goal of this project was to:

* Deploy a static HTML website on an AWS EC2 instance.

* Manage and configure the web server using Nginx.

## 🛠️ Technologies Used

* **HTML5 & CSS3 :** For the website structure and styling.

* **AWS EC2 :** Cloud computing service to host the website.

* **Nginx :** A high-performance web server used to serve the HTML content.

## 🚀 Deployment Steps on AWS EC2

This section outlines the simplified steps I followed to deploy the portfolio on an AWS EC2 instance using Nginx .

**✅ Assumptions**

* An AWS EC2 instance is already launched and running (e.g., Amazon Linux 2 or Ubuntu).

* You have an SSH key to connect to your instance.

* Your EC2 Security Group allows HTTP (port 80) traffic.

1. **Connect to Your EC2 Instance via SSH:**
```bash
    ssh -i /path/to/your-key.pem ec2-user@YOUR_EC2_PUBLIC_IP
    # (Replace 'ec2-user' with 'ubuntu' if using Ubuntu AMI)
```
2. **For Amazon Linux 2:**
```bash
        sudo yum update -y
        sudo yum install nginx -y
```

*   **For Ubuntu:**
```bash
        sudo apt update -y
        sudo apt install nginx -y
```
3.  **Start and Enable Nginx:**
 ```bash
    sudo systemctl start nginx      # Start the Nginx service
    sudo systemctl enable nginx     # Enable Nginx to start on boot
 ```

4.  **Stop Apache (if installed and running):**
If Apache is running, it will conflict with Nginx on port 80.
   *   **For Amazon Linux 2 (if `httpd` is present):**
        ```bash
        sudo systemctl stop httpd
        sudo systemctl disable httpd
        ```
  *   **For Ubuntu (if `apache2` is present):**
        ```bash
        sudo systemctl stop apache2
        sudo systemctl disable apache2
        ```

5.  **Navigate to Nginx Web Root and Deploy `index.html`:** 
The default Nginx web root is typically:

    * /usr/share/nginx/html/ (Amazon Linux 2)

    * /var/www/html/ (Ubuntu)

 *   First, remove the default Nginx index file:
 ```bash
        sudo rm /usr/share/nginx/html/index.html # Or /var/www/html/index.nginx-debian.html for Ubuntu
```
*   Second, Transfer your index.html file from your local machine:
 ```bash
        # From your LOCAL machine:
        scp -i /path/to/your-key.pem index.html ec2-user@YOUR_EC2_PUBLIC_IP:/usr/share/nginx/html/
        # (Adjust path to /var/www/html/ for Ubuntu if needed)
```
*   Third, Ensure correct file permissions:
```bash
        sudo chmod 644 /usr/share/nginx/html/index.html
```

6. **Verify Nginx Configuration (Optional):**
 ```bash
    sudo nginx -t
```
This command checks for syntax errors in your Nginx configuration.

7.  **Restart Nginx to Apply Changes:**
 ```bash
    sudo systemctl restart nginx
 ```

## ✅ Final Success!

![](./Screenshot%20(54).png)

