**How I created an AWS Ubuntu instance**

Ubuntu IP ADDRESS: 44.201.129.143

Firstly, create an AWS Console if you don't already own one

**Launch Instance**

Search for EC2 and click on launch instance

Then, select Ubuntu Operating system.

Under configure security groups, add rules, Add HTTP and a custom TCP with port 80 (replace with any port you want to server your site on) and select source to be anywhere.

Select “Create new key pair”. Give keypair a name and download it. Its a “.pem” which we will later use to login into the server.

Finally launch instance.

**SSH into the server**

Go to EC2 instances list and you will find your newly created instance.

Its instance state should be “Running” or kindly refresh if you don't see it running.

![Instance ](https://user-images.githubusercontent.com/97586970/197512276-041d157a-48e5-40c6-9e6b-719b6d2d44dd.jpeg)

You should see something like this.

Click on the instance id and click connect.

In connect tab, click on connect to open the remote ubuntu server instance from the browser

If you want to connect from your command line or terminal select SSH client tab.

P.S: Copy the key-pair in the appropriate directory i.e cp ~Desktop/task_liuxx.pem ./

Copy the command that looks similar to this ssh -i "task_liuxx.pem" ubuntu@ec2-18-236-174-86.us-west-2.compute.amazonaws.com

Go to command line or terminal and paste this command.

Make sure you have that “.pem” file we downloaded earlier is in that directory from where you are executing this command.

**Installing and configuring Nginx**

sudo apt-get update (to update the system packages).

sudo apt install nginx (Installs Nginx)

sudo systemctl status nginx (To ensure Nginx is working properly)

<img width="172" alt="Ubuntu" src="https://user-images.githubusercontent.com/97586970/197512592-7b9ef018-ceb9-4645-89ee-50ace915bc45.PNG">

**Creating a file under Nginx**

Create a file in /etc/nginx/sites-available/ directory

Name the file as your project’s name. I’ll be naming mine as linux without any extension.

cd /var/www/linux (To access the directory)

Under the var/www/linus directory, ls

You will see the index.html file

Edit the index.html file

I’ll be using nano as the editor. sudo nano linux opens a file named linux in vim editor. Paste the below content into it.

server { listen 80;

listen [::]:80; root /var/www/linux; index index.html index.htm;

server_name linux;
location / {
        try_files $uri $uri/ =404;
} }
It says to listen on port 80. Root directory of the project is var/www/linux.

It will search for files with the name index, index.html and so on.

If it doesn’t find anything it will give you 404. Type Ctrl X to exit out of the vim editor

I used VSCODE Git Bash Terminal

sudo chown -R $USER:$USER /var/www/linux sudo unlink /etc/nginx/sites-enabled/default sudo systemctl restart nginx sudo nginx -t

Running sudo ln -s /etc/nginx/sites-available/sample /etc/nginx/sites-enabled/ will map this configuration file to sites-enabled directory. Now change the permission of directory where your project is going to be and restart the Nginx service.

Create a file named index.html and paste the above content. Its just a sample html file. You can replace your html file, but make sure the name remains index.html to avoid errors.

The above command should run in your local machine’s terminal or command line. It will push the index.html file to the remote server to the location /var/www/linux which has been set as the root directory in nginx config file. All the steps are done. Now click the EC2 instance’s URL, you will see the html content.


