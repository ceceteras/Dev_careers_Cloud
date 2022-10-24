IP Address for Windows Machine : 35.171.26.96

**Setting Up Process**

Click on Launch Instance

Search for EC2 and click on launch instance.

Then, select Windows Operating system.

Under configure security groups, add rules, Add HTTP and a custom TCP with port 80 (replace with any port you want to server your site on) and select source to be anywhere.

Select “Create new key pair”. Give keypair a name and download it. Its a “.pem” which we will later use to login into the server.

Finally launch instance.

**SSH into the server**

Go to EC2 instances list and you will find your newly created instance. 

Its instance state should be “Running” or kindly refresh if you don't see it running.

Click on the instance id and select RDP client, and click on get password(Upload the downloaded private key) 

In my case, I used windows.pem as the private key

Then click on decrypt password

Copy the Username and Password,Username: Adminsrator

Head to your Command Prompt, and type mstsc

Input your IP address(or DNS name), username (which is Administrator) and password (the one you copied) and click on quick connect.

Accept the certificate The Accept Certificate Prompt click on Yes

After Accepting, a Default Windows Homepage will show.

**Downloading and Installing Nginx**

Open Microsoft edge and head to https://nginx.org/en/download to download Nginx for windows

Download and save Nginx file in your directory
start nginx.exe (Installs Nginx)

After downloading, Move the directory into your Program file directory located in your C drive.

**Search for Server manager**

Then click on the start menu and search for IIS and Run as Administrator.

Click Default Website and right click, Edit the dafault web site and unmount the current physical path it currently serves html from.

<img width="251" alt="Remote Desktop" src="https://user-images.githubusercontent.com/97586970/197505963-5e7660c7-8bd5-4a4b-88d1-194dc92bb2ac.png">

This is what you will see after loading your IP Address.

Head over to the html directory inside the Nginx dirctory and modify the index.html file to your own preffered html 
code.

**Pushing files to the server**

<!DOCTYPE html>
<html>
<head>
  <title>Sophie Task 2!</title>
<style>
html { color-scheme: light dark; }
body { width: 35em; margin: 0 auto;
font-family: Tahoma, Verdana, Arial, sans-serif; }
</style>
</head>
<body>
<h1>Sophie TASK TWO !</h1>
<h2>TASK 2 no be beans o!</h2>
<p>If you can see this, a lot of screen time went into this.</p>

<p><em>Sophie Shittu</em></p>
<p><em>Cloud Engineering</em></p>
<p><em>Thank you @Cece for giving me this! E choke</em></p>
</body>
</html>

Save it and locate the nginx.exe file inside the Nginx directory, right click on it and Run as an Administrator.

By now you should be able to access the webserver from the machine's IP address.
