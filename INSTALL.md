Steps to setting up a GNU/Linux webserver and to deploy websites:

1. Decide on which VPS provider you will choose to host your web server.

2. Once your VPS is created, acquire the ipv4 because, we will use it to connect to it.

3. Open your local machine and connect to the vps as root using ssh root@server_address.

4. Once connected, make sure to run apt update and upgrade before installing any packages.

5. Now we will use Nginx as our web server, run the command $sudo apt install nginx.

6. Create a new user where all of our tasks will be done in. Run the command $adduser username. Fill in the following criteria and set up a password.

7. We want to make sure that the new user can perform sudo tasks. So run the command $usermod -aG sudo username.

8. For better security, generate an ssh key on your local machine using $ssh-keygen -b 4096.

9. Now you will copy the public key to the server using $ssh-cpy-id user@server_address. You will now be able to log in without using a password. Then you redo that process but 
with the root user this time.

10. With the public-key now inserted in the new user, you should disable PasswordAuthentication so, only you and other 
users who have the key can access the VPS. Use command $sudo nano /etc/ssh/sshd_config then scroll down to PasswordAuthentication and change yes to no.

11. Reload the sshd sevice by running the command $sudo systemctl reload sshd.

12. Now you wanna provide the website contents. For that download your website with all of its html,css,js scripts. We will be setting it up the repository in the /var/www/html directory of the VPS then create an automated task which will keep your website up to date if any changes are made. So return into to your VPS using ssh.

13. We will be using github as our repository, so install the git package before moving on to the next steps by using the commaand $sudo apt install git

14. Before deploying the website, make sure that there are two copies of your home page or which ever page that will be loaded first when going on your website. One copy with the original name and another named index.html so the web server can detect the index file and set it up.

15. Now change directory using $cd /var/www/html and using the command $git pull to retrieve your repository.

16. Once you have your repository, copy the contents of the of your websites folder and paste it on the /var/www/html directory. Use this command $sudo cp -a /var/www/html/-RepositoryFolder/-WebsiteFolder/. /var/www/html this will copy your websites files to the html directory. You can now load your VPS on a browser and you will be able to see your website.

17. Now we will be moving onto the automated task. Will starting by creating the script as the root user because once we move to crontab it will usually ask for a password if you are using your other user. So run the command $nano yourScript_name.sh

18. In the script you will enter these following commands: 
#! /bin/bash

$cd /var/www/html/Repository_Name
$sudo git pull
$cd /var/www/html
$sudo rm *

19. After inputting all of your commands in the script, we will be using crontab to automate it so that every sunday it will run the script.

20. So run the command $crontab -e as root and input the following line: 0 6 * * 0 /root/file.sh  .So this command basically will run your bash script every sunday at 6:00 am.

21. So those are all the steps needed to fully setup a GNU/Linux webserver and deploy websites online. Plus automating keeping the website up to date.




 
