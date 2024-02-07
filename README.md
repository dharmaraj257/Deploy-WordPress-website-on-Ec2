
# Deploy WordPress website on Ec2

Using Ec2 Aws service deploy the WordPress website on the apache2 server. for the website configure the database using MySQL and store the data.

#### Step 1: Launch the Ec2 instance

1. Give a name to Ec2 Instance WordPress.

2. Select OS Ubuntu 22.04 and Instance type t2.micro

3. Create and download the key pair.

4. Select Vpc create a Security group and add ports, SSH 22, HTTP 80, and HTTPS 443 allowing them to anywhere.

5. Click Launch Instance


#### Step 2: Connect with EC2 instance and Install Server 

1. Select the instance and click connect Instance

2. update the EC2 Instance
    
    sudo apt-get update

3. Install the apache2 server.

    sudo apt-get install apace2 -y
4. Install the library

    sudo apt-get install php libapache2-mod-php php-mysql -y

5. Check server is running or not and copy and paste your instance public IP in the browser.

    service apache2 status


#### Step 3: Create a database that we use in WordPress

1. Install mysql server.

    sudo apt-get install mysql-server -y
2.log in Mysql Using the command

    sudo mysql -u root

3. Create a user.

    CREATE USER 'wp_user'@localhost IDENTIFIED BY 'Home@123';


![Capture](https://github.com/dharmaraj257/Hosting-a-Word-press-website-on-AWS/assets/100831265/4062ffb2-a77b-47a7-9e79-c4ac183e2af2)

4. Create database 
    
    CREATE DATABASE wp;

![2](https://github.com/dharmaraj257/Hosting-a-Word-press-website-on-AWS/assets/100831265/bddcb9e5-1ce4-40f8-a920-afcaf28a4702)


5. Give all privileges to the created user and exit.

    GRANT ALL ON wp.* TO 'wp_user'@localhost;

![3](https://github.com/dharmaraj257/Hosting-a-Word-press-website-on-AWS/assets/100831265/8f82fe61-f87c-403c-b5cc-520a501db10c)

#### Step 4: Download WordPress
1. Visit This link and Copy the link address of the download WordPress

2. Goto temp folder and download the WordPress
``` 
cd /tmp/
wget https://wordpress.org/latest.zip
```
3. Unzip the WordPress folder 

    sudo unzip latest.zip

4. Move wordpress folder to Download.

        sudo mv wordpress/ /var/www/html/

#### Step 5: Install the WordPress 

1. access the website using IP address/wordpress Click Let go 
and enter the details of WordPress and submit


![4](https://github.com/dharmaraj257/Hosting-a-Word-press-website-on-AWS/assets/100831265/b556df62-ada8-4498-992b-eda156a8bef9)


2. Write a wp-confg.php file copy code and paste it into the WordPress folder.

```
cd /var/www/html/WordPress/
sudo vi wp-config.php
```

3. Then Click Run Installation fill in the information and click Install WordPress.

4. Log in to WordPress, now you can see the WordPress page(ip/wordpress) but  it will not show using Instance ip.

Step 6. Set indirect instance ip 

1. Go sites available folder in apache2

        cd /etc/apache2/sites-available/

2. edit 000-default.conf file and add URL 
    
        sudo vi 000-default.conf
 3. Add DocumentRoot and restart the apache2 server 

    /var/www/html/wordpress
    sudo service apache2 restart

#### Output:

![5](https://github.com/dharmaraj257/Hosting-a-Word-press-website-on-AWS/assets/100831265/1def745c-06c8-4a23-9cdd-d31b1e8d58fb)








