# Task 2 - Linux Machine Documentation
### IP Address For AWS Linux Machine : [54.210.173.233](http://ec2-54-210-173-233.compute-1.amazonaws.com)

### SetUp Process
- Head to the compute section on the AWS Dashboard and go the EC2 page
- Click on Launch Instance.
- You will be presented with a page where you will have the chance to customize and configure the machine, below are some you can use,
    1. Give your instance a name
    2. Select Ubuntu under the instance type
    3. Select other options concerning disk capacity, storage that are currently available for your free tier subscription.
    4. select a vpc and also a subnet(create them if you dont already have them)
    5.Configure your security group to allow ssh traffic and also http/https traffic
    6. Create a Key pair, this will help you ssh into the server.
    6. Enter a user data to help you with initial configuration, you can make use of the one below,
        ```shell
        sudo apt-get update
        sudo apt-get install nginx
        nginx -v
        sudo systemctl enable nginx
        ```
    7. Launch the Instance.
- Wait for your instance to display a status of running, by now you should be able to view the nginx default page by entering your instance ip address into your preffered browser.
- Copy the IP address and head to your local terminal, enter the following command to ssh into the server with the private key you created the other time.
    ```shell
        ssh -i private-key.pem ubuntu@<ip address>
    ```
- Inside the Server, lets edit the default web page Nginx is serving but displaying an hello world app,
```shell

echo "Hello world from a Linux Machine (Ubuntu)" > /var/www/html/*.html
sudo systemctl restart nginx
```
- By now, you should be able to access the Web page from any browser of your choice


# Task 2 - Linux Machine Documentation

### IP Address for Windows Machine : [18.206.174.74](http://ec2-18-206-174-74.compute-1.amazonaws.com)


### SetUp Process
- Head to the compute section on the AWS Dashboard and go the EC2 page
- Click on Launch Instance.
- You will be presented with a page where you will have the chance to customize and configure the machine, below are some you can use,
    1. Give your instance a name
    2. Select Windows under the instance type
    3. Select other options concerning disk capacity, storage that are currently available for your free tier subscription.
    4. select a vpc and also a subnet(create them if you dont already have them)
    5.Configure your security group to allow rdp traffic and also http/https traffic
    6. Create a Key pair, this will help you rdp into the server.
    7. Launch the Instance.
- Head to Instances and select the instance you just created, at the top right corner you will see a connect button, Click it
- On the connect to instance page, select RDP client, and click on get password(Upload the downloaded private key).
- You can also download the remote desktop file if your RDP client allows you to RDP with an rdp file.
- Copy the Username and Password, and head to your rdp client , On my own end, i'm using remmina(an RDP client for Ubuntu)
- Input your IP address(or DNS name), username (which is Administrator) and password (the one you copied) and click on quick connect.

- You should get a page like below asking you to Accept the certificate
[The Accept Certificate Prompt](/cert.png)
<b>click on Yes</b>

- After Accepting you will get the default windows homepage, like the one below
[Default Windows Homepage](/windows.png)

- Inside your Virtual Machine, Open Microsoft edge and head to https://nginx.org/en/download to download Nginx for windows.

- After downloading, Move the directory into your Program file directory located in your C drive.

Its worthy to Note that , Internet information service is microsofts default web server and we have to activate it 

- Head to Server manager and follow the below steps:
    1. Click on Add roles and features\
    2. on the before you begin page , Click next
    3. Select Role-based or feature-based installation as your installation type.
    4. Select your Server name from the server pool and click next
    5. Under Roles, Click On Next
    6. Under the features, Select IIS Hostable Web Core and click next
    7. Under the Confirmation Page, Click Install to install the IIS web server.
- Click on the start menu and search for IIS and Run as Administrator.
- Click on the arrow in front of the server name, soa s to expose the directory tree
- Locate *Default Website* and right click, Edit the dafault web site and unmount the current physical path it currently serves html from.
- Head over to the html directory inside the Nginx dirctory and modify the index.html file to your own preffered html code.

- Save it and locate the nginx.exe file inside the Nginx directory, right click on it and Run as an Administrator.

- By now you should be able to access your Nginx webserver from the machines IP address.


### Thank you








