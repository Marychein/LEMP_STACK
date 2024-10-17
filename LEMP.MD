# This guide documents the installation and configuration process of a LEMP (Linux, Nginx, MySQL, PHP) stack on an EC2 instance running Ubuntu. 

## Step-by-Step Instructions
![LEMP Machine Creation](https://github.com/Marychein/LEMP_STACK/blob/main/LEMP%20machiine%20creation.png)



1. Update the Package Repository
The first step is to ensure that my package repository is up to date: This was achieved using the command:
```bash
sudo apt update
```

2. # Install Nginx server
Install the Nginx web server with:
```bash
sudo apt install nginx
```

Once installed, I checked the status to ensure Nginx is running with the command:
```bash
sudo systemctl status nginx
```bash

3. ## Retrieve Public IP Address
To get my instance's public IP address, I used this command:
```bash
curl -s http://169.254.169.254/latest/meta-data/public-ipv4
```
![Nginx Testing](https://github.com/Marychein/LEMP_STACK/blob/main/nginx%20testing.png)


4. ## Install MySQL
Installed MySQL for database management:
```bash
sudo apt install mysql-server
```



Once MySQL is installed, I logged in to the MySQL shell using this command:
```bash
sudo mysql
```

I set the root password using the following command inside the MySQL shell:
sql
```bash 
ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'PassWord.1';
```
At this point, I had the option to validate my password and check password strength in the mysql server with the command:
Press y|Y for Yes, any other key for No: 
Please enter STRONG: 1 Estimated strength of the password: 100 
Do you wish to continue with the password provided?
(Press y|Y for Yes, any other key for No) : y

Then, secure the MySQL installation:
sudo mysql_secure_installation

5. ## Install PHP
PHP handles the server-side scripting of the stack.

I installed PHP and its required modules with the command:
```bash
sudo apt install php-fpm php-mysql
```

6. ## Create Project Directory
Created a directory to host my web project:
```bash
sudo mkdir /var/www/projectLEMP
```bash
Gave ownership to the ubuntu user:
```bash
sudo chown -R ubuntu:ubuntu /var/www/projectLEMP
```

7. ## Configure Nginx for the Project
Created a configuration file for the project:
```bash
sudo nano /etc/nginx/sites-available/projectLEMP
```
Inside this file, the server block was configured as needed, and then the configuration was enabled:
sudo ln -s /etc/nginx/sites-available/projectLEMP /etc/nginx/sites-enabled

Disabled the default configuration:
sudo unlink /etc/nginx/sites-enabled/default

**Reloaded Nginx to apply the changes:**
```bash
sudo systemctl reload nginx
```
8. ## Test the Nginx Setup
Created a test page to verify Nginx is working:
```bash
sudo echo 'Hello LEMP from hostname' $(TOKEN=`curl -X PUT "http://169.254.169.254/latest/api/token" -H "X-aws-ec2-metadata-token-ttl-seconds: 21600"` && curl -H "X-aws-ec2-metadata-token: $TOKEN" -s http://169.254.169.254/latest/meta-data/public-hostname) 'with public IP' $(TOKEN=`curl -X PUT "http://169.254.169.254/latest/api/token" -H "X-aws-ec2-metadata-token: $TOKEN" -s http://169.254.169.254/latest/meta-data/public-ipv4)` > /var/www/projectLEMP/index.html
```
9. ## Create PHP Test File
To test PHP functionality, a PHP file info was created:
```bash
nano /var/www/projectLEMP/info.php
```

**Write the following inside the info.php file:**
```bash
\php
<?php
phpinfo();
?>
```
![PHP Info](https://github.com/GrailRoyal/LEMP-STACK/blob/141555c34081dcbae06dd3e994a3f28819bb6fd2/php_%20info.png)


10. ## MySQL User Configuration
For further database management, a new MySQL user was created:
```bash
mysql -u user_mary -p
```

11. ## Conclusion
At this point, I have successfully set up the LEMP stack on my EC2 instance. This robust infrastructure allows me to build and manage web applications efficiently. With MySQL for database management, PHP for server-side scripting, and Nginx for serving web pages, I am now equipped to create scalable and high-performance web solutions.

# This guide documents the installation and configuration process of a LEMP (Linux, Nginx, MySQL, PHP) stack on an EC2 instance running Ubuntu. 

## Step-by-Step Instructions

1. Update the Package Repository
The first step is to ensure that my package repository is up to date: This was achieved using the command:
sudo apt update

2. # Install Nginx server
Install the Nginx web server with:
```bash
sudo apt install nginx
```

Once installed, I checked the status to ensure Nginx is running with the command:
```bash
sudo systemctl status nginx
```bash

3. ## Retrieve Public IP Address
To get my instance's public IP address, I used this command:
```bash
curl -s http://169.254.169.254/latest/meta-data/public-ipv4
```

4. ## Install MySQL
Installed MySQL for database management:
```bash
sudo apt install mysql-server
```

Once MySQL is installed, I logged in to the MySQL shell using this command:
```bash
sudo mysql
```

I set the root password using the following command inside the MySQL shell:
sql
```bash 
ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'PassWord.1';
```
At this point, I had the option to validate my password and check password strength in the mysql server with the command:
Press y|Y for Yes, any other key for No: 
Please enter STRONG: 1 Estimated strength of the password: 100 
Do you wish to continue with the password provided?
(Press y|Y for Yes, any other key for No) : y

Then, secure the MySQL installation:
sudo mysql_secure_installation

5. ## Install PHP
PHP handles the server-side scripting of the stack.

I installed PHP and its required modules with the command:
```bash
sudo apt install php-fpm php-mysql
```

6. ## Create Project Directory
Created a directory to host my web project:
```bash
sudo mkdir /var/www/projectLEMP
```bash
Gave ownership to the ubuntu user:
```bash
sudo chown -R ubuntu:ubuntu /var/www/projectLEMP
```

7. ## Configure Nginx for the Project
Created a configuration file for the project:
```bash
sudo nano /etc/nginx/sites-available/projectLEMP
```
Inside this file, the server block was configured as needed, and then the configuration was enabled:
sudo ln -s /etc/nginx/sites-available/projectLEMP /etc/nginx/sites-enabled

Disabled the default configuration:
sudo unlink /etc/nginx/sites-enabled/default

**Reloaded Nginx to apply the changes:**
```bash
sudo systemctl reload nginx
```
8. ## Test the Nginx Setup
Created a test page to verify Nginx is working:
```bash
sudo echo 'Hello LEMP from hostname' $(TOKEN=`curl -X PUT "http://169.254.169.254/latest/api/token" -H "X-aws-ec2-metadata-token-ttl-seconds: 21600"` && curl -H "X-aws-ec2-metadata-token: $TOKEN" -s http://169.254.169.254/latest/meta-data/public-hostname) 'with public IP' $(TOKEN=`curl -X PUT "http://169.254.169.254/latest/api/token" -H "X-aws-ec2-metadata-token: $TOKEN" -s http://169.254.169.254/latest/meta-data/public-ipv4)` > /var/www/projectLEMP/index.html
```
9. ## Create PHP Test File
To test PHP functionality, a PHP file info was created:
```bash
nano /var/www/projectLEMP/info.php
```

**Write the following inside the info.php file:**
```bash
\php
<?php
phpinfo();
?>
```
![LEMP PHP info](https://github.com/Marychein/LEMP_STACK/blob/main/php%20info.png)

10. ## MySQL User Configuration
For further database management, a new MySQL user was created:
```bash
mysql -u user_mary -p
```
![LEMP Stack Testing](https://github.com/Marychein/LEMP_STACK/blob/main/LEMP%20Stack%20testing.png)



11. ## Conclusion
At this point, I have successfully set up the LEMP stack on my EC2 instance. This robust infrastructure allows me to build and manage web applications efficiently. With MySQL for database management, PHP for server-side scripting, and Nginx for serving web pages, I am now equipped to create scalable and high-performance web solutions.


