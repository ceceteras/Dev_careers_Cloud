# Task 2 for Cloud Computing Track (DevCareers)

Task 2 - Create a Linux and Windows Server with SSH and RDP privilegs. 

LINUX SERVER - 

Create a account with AWS cloud provider which provides a free tier account for a year. 
Navigate the management console to the compute section on the AWS Dashboard and go the EC2 page
On the EC2 Dashboard, click on Launch Instance.

A page will display neccessary information about the EC2 service  where you can customize and configure the machine you will like to use, 
Give your instance a name
Select Ubuntu under the instance type
Create a Key pair, this will help you securly connect to your instance. NB: Remember to download your Keypair because without it, you will not be able to connect to your instance.
select a vpc and also a subnet(create them if you dont already have them) 
Create a security group to allow ssh traffic 
Allow HTTPS traffic from internet
Select other options concerning disk capacity, storage that are currently available for your free tier subscription.

Then Launch, wait for a couple seconds for your instance status to change to running.

Uisng Ec2 Instance Connect to connect to the server 

INSTALLING NGINX
To install Nginx, type the following commands:
 sudo apt-get update, then
 sudo apt-get install nginx

To verify installation, 
 nginx -v to display the software version.

To test if Nginx is running or not, Open a web browser and enter
 http://127.0.0.1 

After installing Nginx, Nginx has a default server block directory '/var/www/html'

To configure nginx server block for your application, create a new directory by 
 sudo mkdir -p /var/www/appname.com/html

To configure ownership and permission
 sudo chown –R $USER:$USER /var/www/appname.com
 sudo chmod –R 755 /var/www/appname.com
Create an index.html file for the server block using nano text editor (you can use your preferred editor)
 sudo nano /var/www/appname.com/html/index.html

In the text editor, enter the followung HTML code:
<html>
   <head>
      <title>Welcome to appname.com!</title>
   </head>
   <body>
      <h1>This message confirms that your Nginx server block is working. Great work!</h1>
   </body>
</html>
Press CTRL+o to write changes, then CTRL+x to exit.

Creating Nginx Server Block Configuration 
To open the configuration file for editing, enter:
 sudo nano /etc/nginx/sites-available/appname.com
and enter the following code: 

server {
         listen 80;

         root /var/www/appname.com/html;
         index index.html index.htm index.nginx.debian.html;

         server_name appname.com www.appname.com;
            location / {
            try_files $uri $uri/ =404;
          }
}

To create a symbolic link for nginx to read on startup, type
 sudo ln –s /etc/nginx/sites-available/test_domain.com /etc/nginx/sites-enabled
Then restart Nginx server using sudo systemctl restart nginx

Test configuration using sudo nginx -t
 'The systme should display configuration file syntax is ok and configuration file test is successful. 

Modification of hosts file
Display the system's IP address with the command:
 hostname -i 

open /etc/hosts for editing 
 sudo nano /etc/hosts
 then enter 127.0.1.1 appname.com www.appname.com.
save using CTRL+o and CTRL+x to exit

Check appname.com in web browser 
open a brower window and navigate to appname.com 

You should see the message you entered earlier.



STEPS FOR WINDOWS VM
WINDOWS SERVER - 

Create a account with AWS cloud provider which provides a free tier account for a year. 
Navigate the management console to the compute section on the AWS Dashboard and go the EC2 page
On the EC2 Dashboard, click on Launch Instance.

A page will display neccessary information about the EC2 service  where you can customize and configure the machine you will like to use, 
Give your instance a name
Select Windows under the instance type
Create a Key pair, this will help you securly connect to your instance. NB: Remember to download your Keypair because without it, you will not be able to connect to your instance.
 
Create a security group to allow RDP traffic 
Allow HTTPS traffic from internet
Select other options concerning disk capacity, storage that are currently available for your free tier subscription.

Then Launch, wait for a couple seconds for your instance status to change to running.

To coonect to your windows server using the RDP client, 
Download the remote desktop file indicated on the RDP Client Page.
Upload the downloaded keypair for decryption to be able to obtain the password.
After connecting to the instance, download nginx from your web browser
Extract the downloaded file into C:/ drive and double tap on the nginx.exe file to run.

Configuring NGINX
Nginx needs to be configured internally to microsoft's native web server (IIS) to allow the instance IP listen for request on the internet.

Create a new folder in C: drive which would be used later. Inside the folder, create an index.html file with contents inside.

Using server manager from the serch bar, select add roles and features, select your server and when you get to roles, enable IIS. Proceed to install.

Open IIS, navigate to default website under sites and change the physical path to a new path in your C: drive (the one you previously created)

Stop and restart nginx, the web page should be visible from the ip address.

