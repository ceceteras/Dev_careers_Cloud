
# Documentation For Linux and Windows Virtual Machine running Unix Server.

## This can be created with an account from a cloud service, using either:
a. Aws account(free tier)

b. Microsoft Azure (available for few months)

c. GCP account 


## Linux_Machine 

1. Launching your EC2 instance

2. Name your EC2 instance

3. Choose an AMI

4. Configure a key pair

5. Configure the network settings
  You use this pane to configure networking settings.
  The virtual private cloud (VPC) indicates which VPC you want to launch the instance into.
 

6. Ensure the instance is running.
7. Note: Refresh if needed.
        ◦ Instance State: Running
        ◦ Status Checks: 2/2 checks passed

Using the Public ip address  you should be able to access the Web page from any browser of your choice


### Access the Machine with the IP Address  http://54.172.180.154/
![Screenshot from 2022-10-22 07-58-04](https://user-images.githubusercontent.com/44731076/197325298-22ec7e13-7445-4779-8ddf-d2f8fad6f9f4.png)



## Windows Instance
To set up the windows instance, 
1. click on create instance
2. Give your instance a name
3. Select Windows under the instance type
4. Select other options concerning disk capacity, storage that are currently available for your free tier subscription.
   select a vpc and also a subnet(create them if you dont already have them) 5.Configure your security group to allow rdp traffic and also http/https   traffic
   Create a Key pair,  You use the Rdp to enable a connection to the windows server.
5. Launch the Instance.
6. on the instance select the windows instance, click connect 
7. Choose connect through Rdp 
8. this will ensure you upload the downloaded key.
9. Copy the Username and Password, and head to your rdp client ,using remmina(an RDP client for Ubuntu)
10.Input your IP address(or DNS name), username (which is Administrator) and password (the one you copied) and click on quick connect.
11. A prompt appear asking to Accept the certificate
12. Then your Windows Virtual Machine comes up.
 As descriped in the image below: 
 
 
 ![Screenshot from 2022-10-21 23-21-07](https://user-images.githubusercontent.com/44731076/197333242-d6597589-6379-44aa-aab1-9c87e4548d6e.png)

![Screenshot from 2022-10-21 23-34-13](https://user-images.githubusercontent.com/44731076/197333290-b7756f12-ae79-4c2a-9ca9-c32513af269b.png)

![Screenshot from 2022-10-22 10-29-40](https://user-images.githubusercontent.com/44731076/197333344-b13a762c-e3c2-40b9-a0da-a6202546e6a5.png)
