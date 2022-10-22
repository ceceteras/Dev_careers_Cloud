# Task 2 
Create 2 Virtual Machines, Linux and Windows respectively with SSH and RDP priviledges utilizing any Cloud provider of choice. Using nginx on both servers, deploy a simple web app.

## Steps taken for the Linux VM
### Creating Linux VM
Using AWS Cloud Provider, navigate to the management console and create an Ubuntu VM having the following configurations
- t2 micro (free tier)
- Open connection for TCP ports which should be exposed on port 22 (ssh) and port 80 (http)
- Create a key pair

### Installing NGINX
SSH into the VM and run the following commads
```
sudo apt update
sudo apt install nginx
```

Confirm nginx is running with the below command
```
sudo service nginx status
```
You can also load your ip address to see it
```
http://your-ip-address:80
```


### Overwrite NGINX default configuration to display your web app
Nginx has a default server block serving documents out of a directory at `/var/www/html`.
- Create a directory structure within `/var/www `for your web app
```
sudo mkdir /var/www/your-app-name
```

- Assign ownership of the directory with the $USER environment variable, which will reference your current system user

```
sudo chown -R $USER:$USER /var/www/your-app-name
```

- Create an index.html file in this directory and place contents in it.

- Open a new configuration file in Nginx’s sites-available directory using a nano text editor
```
sudo nano /etc/nginx/sites-available/your-app-name
```

and paste the below into it

```
#/etc/nginx/sites-available/your-app-name

server {
    listen 80;
    server_name your-app-name http://54.234.24.23/;
    root /var/www/your-app-name;

    index index.html index.htm;

    #location / {
    #    try_files $uri $uri/ =404;
    #}

}
```

- Activate your configuration by linking to the config file from Nginx’s sites-enabled directory:
```
sudo ln -s /etc/nginx/sites-available/your-app-name /etc/nginx/sites-enabled/
```
Test the configuration syntax with the below command
```
sudo nginx -t
```
It should return a successful message if there are no errors

- Disable the default Nginx host currently configured to listen on port 80
```
sudo unlink /etc/nginx/sites-enabled/default
```

Reload Nginx for the changes to be applied
```
sudo systemctl reload nginx
```

In your web browser, open your website ip address on port 80 and your changes should appear


## Steps taken for the Windows VM
### Creating Windows VM

Using AWS Cloud Provider, navigate to the management console and create a windows vm having the following configurations
- t2 micro (free tier)
- Open connection for TCP ports which should be exposed on port 3389 (rdp) and port 80 (http)
- Create a key pair

### Installing NGINX
To connect to the Windows VM using RDP Client, follow the below steps
- Download the remote desktop file shown on the RDP Client page
- Get the password by uploading the key pair you created which would be decrypted
- Open the remote desktop file you downloaded and paste the password

Once you are connected to the VM, navigate to the web browser and download Nginx 

Extract the downloaded file, move the extracted file to your programs folder in C:/ drive, open the folder and double tap the nginx.exe file to run nginx.

Verified the installation was successful by running localhost in the browser.

### Configuring NGINX
Nginx needs to be configured internally to microsoft's native web server (IIS) to allow the instance IP listen for request on the internet.

- Create a new folder in C: drive which would be used later. Inside the folder, create an index.html file holding contents of your choice
  
- Using server manager from the serch bar, select add roles and features, select your server and when you get to roles, enable IIS. Proceed to install.

- Open IIS, navigate to default website under sites and change the physical path to a new path in your C: drive (the one you previously created)

- Stop and restart nginx, the web page should be visible from the ip address


Another process to go about this would be to use nginx as a reverse proxy by making edits in the nginx.conf file.

