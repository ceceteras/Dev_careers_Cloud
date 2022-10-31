# Task 2 for Cloud Computing Track (DevCareers)
readme.md 

Task 2 - Create a Linux and Windows Server with SSH and RDP privilegs. 

# LINUX SERVER - 184.73.14.199

1. Create a account with AWS cloud provider which provides a free tier account for a year. 
2. Navigate the management console to the compute section on the AWS Dashboard and go the EC2 page,
 on the EC2  Dashboard click on Launch Instance.
 A page will display neccessary information about the EC2 service  where you can customize and configure the machine you will like to use. 
3. Give your instance a name, Select Ubuntu under the instance type
4. Create a Key pair, this will help you securly connect to your instance. 
 NB: Remember to download your keypair because without it, you will not be able to connect to your instance.
5. select a vpc and also a subnet(create them if you dont already have them) 
6. Create a security group to allow ssh traffic and allow HTTPS traffic from internet
7. Select other options concerning disk capacity, storage that are currently available for your free tier subscription.
8. Then Launch, wait for a couple seconds for your instance status to change to running.
9. Connect to connect to the server 

# INSTALLING NGINX
1. To install Nginx, type the following commands:
 sudo apt-get update, then
 sudo apt-get install nginx

2. To verify installation, 
 nginx -v to display the software version.

3. To test if Nginx is running or not, Open a web browser and enter
 http://127.0.0.1 

4. After installing Nginx, Nginx has a default server block directory '/var/www/html'

5. To configure nginx server block for your application, create a new directory by 
 sudo mkdir -p /var/www/appname.com/html

6. To configure ownership and permission
 sudo chown –R $USER:$USER /var/www/appname.com
 sudo chmod –R 755 /var/www/appname.com
7. Create an index.html file for the server block using nano text editor (you can use your preferred editor)
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

8. Creating Nginx Server Block Configuration 
   To open the configuration file for editing, enter:
    sudo nano /etc/nginx/sites-available/appname.com and enter the following code: 

   server {
         listen 80;

         root /var/www/appname.com/html;
         index index.html index.htm index.nginx.debian.html;

         server_name appname.com www.appname.com;
            location / {
            try_files $uri $uri/ =404;
          }
   }

9. To create a symbolic link for nginx to read on startup, type
      sudo ln –s /etc/nginx/sites-available/test_domain.com /etc/nginx/sites-enabled
   Then restart Nginx server using 
    sudo systemctl restart nginx

   Test configuration using sudo nginx -t
   'The system should display configuration file syntax is ok and configuration file test is successful'. 

10. Modification of hosts file
   Display the system's IP address with the command:
    hostname -i 

11.  Open /etc/hosts for editing 
    sudo nano /etc/hosts
      then enter 127.0.1.1 appname.com www.appname.com.
      save using CTRL+o and CTRL+x to exit

12. Check appname.com in web browser 
   open a brower window and navigate to appname.com 

You should see the message you entered earlier.



# STEPS FOR WINDOWS VM
# WINDOWS SERVER - 35.173.247.189

1. Create a account with AWS cloud provider which provides a free tier account for a year. 
2. Navigate the management console to the compute section on the AWS Dashboard and go the EC2 page,
 on the EC2  Dashboard click on Launch Instance.
 A page will display neccessary information about the EC2 service  where you can customize and configure the machine you will like to use. 
3. Give your instance a name, Select Windows under the instance type
4. Create a Key pair, this will help you securly connect to your instance. 
 NB: Remember to download your keypair because without it, you will not be able to connect to your instance.
5. Create a security group to allow RDP traffic 

6. Select other options concerning disk capacity, storage that are currently available for your free tier subscription and click Launch, wait for a couple seconds for your instance status to change to running.

# To connect to your Windows server using the RDP client, 
1. Download the remote desktop file indicated on the RDP Client Page.
2. Upload the downloaded keypair for decryption to be able to obtain the password.
3. After connecting to the instance, download nginx from your web browser
4. Extract the downloaded file into C:/ drive and double tap on the nginx.exe file to run.

# Configuring NGINX
 Nginx needs to be configured internally to microsoft's native web server (IIS) to allow the instance IP listen for request on the internet.

1. Create a new folder in C: drive which would be used later. Inside the folder, create an index.html file with contents inside.

2. Using server manager from the serch bar, select add roles and features, select your server and when you get to roles, enable IIS. Proceed to install.

3. Open IIS, navigate to default website under sites and change the physical path to a new path in your C: drive (the one you previously created)

4. Stop and restart nginx, the web page should be visible from the ip address.

