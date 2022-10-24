## How to provision Virtual Machines, Install and Run Nginx

#### Public Ip Address:
Linux: *[18.191.214.95](http://18.191.214.95)*
Windows: *[3.145.101.211](http://3.145.101.211)

#### DNS Address:
Linux: *[ec2-18-191-214-95.us-east-2.compute.amazonaws.com](http://ec2-18-191-214-95.us-east-2.compute.amazonaws.com)*
Windows: *[ec2-3-145-101-211.us-east-2.compute.amazonaws.com](http://ec2-3-145-101-211.us-east-2.compute.amazonaws.com)*

#### Cloud Service Provider:
[Amazon Web Services (AWS)](https://aws.amazon.com)

### Provision a Server
The first step to take is to sign up on AWS. Once you have an account, you can login to the web console and go to the **Amazon Elastic Compute Cloud (Amazon EC2)** service.

![EC2 Dashboard](img/Screenshot%20(9).png)

The above is a screenshot of my Amazon EC2 Dashboard with two running instances. Here you can click on **Launch instances** to provision a new virtual machine. You get to name your VM, choose what Application and OS Images (Amazon Machine Image) you get to run, choose or create a new key pair which would be used to access the server later on, and choose or create a new security group to restrict inbound traffic to your server. Once created, you can view all instances in your EC2 dashboad.

### Connecting to your Windows VM
To connect to your Windows VM, ensure your **Security group** has a rule that allows RDP connection. This allows you to connect to your instance using a **Remote Desktop Connection** which can be downloaded as a desktop application if you haven't done so previously. Connect using the provided Username and Password (created from decrypting your private key you had added or created in previous steps).

![Connect using RDP](img/Screenshot%20(10).png)

Give your server some time to start up and you should be seeing a Windows machine at this point just like the image below:

![AWS Microsoft Windows VM](img/Screenshot%20(7).png)

### Download Nginx
At this point, you will be able to use the internet explorer and open the Nginx [Download](http://nginx.org/en/download.html) link for Windows.
Download any of the **mainline version** as recommended by Nginx, or the latest stable version. Extract the downloaded folder then move the entire folder that came with the built-in download copy into the **Program Files**.  Select and double-click the Nginx.exe file to install and run Nginx locally. Type localhost or `http://localhost` on  Microsoft Edge, the browser as used in the below image. If you see a screen saying the Nginx web server is successfully installed and working, it means there were no problems with your Nginx installation in Windows.
![Welcome to Nginx](img/Screenshot%20(3).png)

To run Nginx, you have to use Internet Information Services (IIS), which is a Microsoft web server that serves requested HTML pages or files. You can enable it in “Turn Windows Features On or Off” in the Control Panel. Check the required fields for **Web Management Tools** and **IIS Management Console**.


### Connecting to your Linux VM
First select your Linux EC2 instance and click on connect. You can SSH to connect locally using the terminal or the browser based SSH connection.
I created an Amazon Linux instance which runs an Amazon Linuz 2 OS with an ID like **centos rhel fedora** OS. It is important to note what Linux version your instance is running on in order to use the right commands. You can get the version by typing `cat /etc/os-release`. Upon a successful connection to this new instance, the first thing to do is an update. Run this using `sudo yum upate` command.

Follow the instructions to install Nginx based on your OS release, then start Nginx using `sudo service nginx start`. You can test to ensure that Nginx has been installed successfully by running `curl localhost:80`. This should show the default HTML page for Nginx confirming successful installation.

You can edit the default Nginx HTML page found in `/usr/share/nginx/html/index.html. Or start building an application and configure Nginx to serve your application.