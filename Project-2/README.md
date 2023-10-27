
# WordPress Website on AWS EC2


# Table of Contents

1. [Prerequisites](#prerequisites)
    - [AWS Account](#aws-account)
    - [Basic Understanding](#basic-understanding)
2. [Setting up an EC2 Instance](#1-setting-up-an-ec2-instance)
3. [Associating an Elastic IP](#2-associating-an-elastic-ip)
4. [Connect to EC2 Instance via SSH](#3-connect-to-ec2-instance-via-ssh)
5. [Install Apache Web Server](#4-install-apache-web-server)
6. [Install PHP and MySQL](#5-install-php-and-mysql)
7. [Configure MySQL](#6-configure-mysql)
8. [Install WordPress](#7-install-wordpress)
9. [Configure WordPress](#8-configure-wordpress)
10. [Adjust Apache to Serve WordPress on Root](#9-adjust-apache-to-serve-wordpress-on-root)
11. [Conclusion](#conclusion)


## Prerequisites

- **AWS Account**: Before you start, you need an AWS account. This gives you access to Amazon's cloud services, including EC2 which is used for this tutorial.

- **Basic Understanding**: Familiarity with AWS EC2, MySQL, and WordPress will make this process smoother, but the guide is designed for all levels.

## Steps:

### 1. Setting up an EC2 Instance:

Creating an EC2 instance is akin to renting a virtual computer on the cloud. 

# Login to AWS Management Console and navigate to the EC2 Dashboard

# Click on 'Launch Instance'

- **Choose OS**: Select Ubuntu as it's widely used and supported.

- **Instance Type**: `t2.micro` is suitable for small projects and is eligible for the AWS Free Tier.

- **Key Pair**: A key pair ensures secure access to your instance.

- **Network Settings**: Enable HTTP and HTTPS traffic to make your site accessible on the web.

### 2. Associating an Elastic IP:

An Elastic IP is a static, public IPv4 address. Associating it with your instance ensures it retains the same IP even after rebooting.

```bash
# Navigate to EC2 Dashboard > Elastic IPs
# Allocate a new IP and associate it with your EC2 instance
```

### 3. Connect to EC2 Instance via SSH:

SSH (Secure Shell) allows secure access to your EC2 instance. Using the key pair you created, you can connect and execute commands on your instance.

```bash
ssh -i /path/to/your-key.pem ubuntu@your-elastic-ip
```

### 4. Install Apache Web Server:

Apache serves your website's files to visitors. It's a popular, open-source web server.

```bash
sudo apt update
sudo apt install apache2
```

### 5. Install PHP and MySQL:

WordPress is written in PHP and uses a MySQL database to store content.

```bash
sudo apt install php mysql-server
```

### 6. Configure MySQL:

Setting up user permissions and creating a database for WordPress are crucial.

```bash
# Access MySQL
mysql -u root -p

# Set up WordPress user and database
ALTER USER 'root'@'localhost' IDENTIFIED WITH 'mysql_native_password' BY 'your-strong-password';
CREATE USER 'wp_user'@'localhost' IDENTIFIED BY 'your-strong-password';
CREATE DATABASE wp;
GRANT ALL PRIVILEGES ON wp.* TO 'wp_user'@'localhost';
```

### 7. Install WordPress:

Downloading and moving the WordPress files to your web server's root directory.

```bash
cd /tmp
wget https://wordpress.org/latest.tar.gz
tar xvf latest.tar.gz
sudo mv wordpress /var/www/html/
```

- **Browser Installation**: Open a browser and navigate to `http://your-elastic-ip/wordpress` to start the WordPress installation.

### 8. Configure WordPress:

WordPress has an intuitive setup wizard. Fill in the required details, and your site will be ready.

### 9. Adjust Apache to Serve WordPress on Root:

This ensures visitors accessing your domain are directly shown the WordPress site without needing to add '/wordpress' at the end.

```bash
sudo nano /etc/apache2/sites-available/000-default.conf
```

- Update the `DocumentRoot` directive to point to `/var/www/html/wordpress` and restart Apache.

## Conclusion:

This guide provides a step-by-step approach to hosting a WordPress website on AWS EC2.
```

