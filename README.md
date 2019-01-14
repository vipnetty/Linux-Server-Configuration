CONTENTS OF THIS FILE
---------------------
Installation of a Linux server and prepare it to host your web applications. 
You will secure your server from a number of attack vectors, install and configure a database server, and deploy one of your existing web applications onto it.


1. Information of grader
contents of private RSA file is in LightsailDefaultKey-ap-southeast-1.pem
IP address of server : 13.229.112.66
Username for grader : "grader"
Server login password for grader : "11111
Pasword for sudo access " ""
Port : 2200
URL : http://ec2-13-229-112-66.ap-southeast-1.compute.amazonaws.com

2. Steps to login for grader
Open up a terminal window and type ssh -v grader@13.229.112.66 -p 2220
When prompted for the password for the ssh key grader_rsa type 11111
The password when using sudo is ''(empty)
Obtain access to virtual server

3. Set up amazon lightsail account using steps from "Get started on Lightsail(https://classroom.udacity.com/nanodegrees/nd004/parts/b2de4bd4-ef07-45b1-9f49-0e51e8f1336e/modules/56cf3482-b006-455c-8acd-26b37b6458d2/lessons/046c35ef-5bd2-4b56-83ba-a8143876165e/concepts/c4cbd3f2-9adb-45d4-8eaf-b5fc89cc606e)" in project prep. https://classroom.udacity.com/nanodegrees/nd004/parts/00413454014/modules/357367901175462/lessons/3573679011239847/concepts/c4cbd3f2-9adb-45d4-8eaf-b5fc89cc606e.

4. Download the default private key from the Account page

5. move private key to .ssh folder.and Log into server.
   command :
   >> mv ~/Downloads/LightsailDefaultKey-ap-southeast-1.pem ~/.ssh/
   >> chmod 600 ~/.ssh/LightsailDefaultKey-ap-southeast-1.pem
   >> ssh -i ~/.ssh/LightsailDefaultKey-ap-southeast-1.pem ubuntu@13.229.112.66
   >> Update and upgrade all packages

6. Update all packages
   command :
   >> sudo apt-get update
   >> sudo apt-get upgrade

7. Change the SSH port from 22 to 2200 and reconfigure authetications
   command :
   >> sudo nano /etc/ssh/sshd_config
   Then change Port 22 to Port 2200

8. Conigure Amazon Lightsail Firewall
   Click on "Networking" tab. 
   Under Firewall section click "add another" .
   Choose "Custom" as application, "TCP" as protocol and "2200" as range

9. Configure Uncomplicated Firewall (UFW)
   Check UFW status to make sure its inactive : sudo ufw status
   Deny all incoming by default : sudo ufw default deny incoming
   Allow outgoing by default : sudo ufw default allow outgoing
   Allow SSH on port 2200 : sudo ufw allow 2200/tcp

10. Create a new user called grader
   command :
   >> sudo adduser grader
   When prompted enter the following user details for grader
   Enter new UNIX password: 11111
   Retype new UNIX password: 11111
   passwd: password updated successfully
   Changing the user information for grader
   Enter the new value, or press ENTER for the default
	   Full Name []: 
	   Room Number []: 
	   Work Phone []: 
	   Home Phone []: 
	   Other []: 
   Is the information correct? [Y/n] Y
   Change the ssh-config file so that grader has the permission to use sudo.
   - sudo visudo
   The file opens in nano and you insert the line grader ALL=(ALL:ALL) ALL
   under "#User privilege specification" underneath root ALL=(ALL:ALL) ALL .
   Then save file by hitting Ctrl + x and selecting Yes.
   Create ssh login keys for grader
   On local machine generate SSH key pair by running command : ssh-keygen


   The virtual machine swich superuser to grader su - grader where password is 11111 
   Create .ssh directory mkdir .ssh
   Create empty file to store key nano .ssh/authorized_keys
   
   Continue.