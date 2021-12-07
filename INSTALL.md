Steps to installing a web server on  VPS:

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

12. Now you wanna provide the website contents. For that download your website with all of its html,css,js scripts. Go to the directory where it is stored 
with the $cd command. Make sure the files are in a zip folder. Then you want to run the command $sudo scp file.zip root@server_address:/var/www/html . It will prompt you
for the root password so make sure you have it.

13.Log back in to your VPS connection as the user you created, and change directory to $cd /var/www/html. You will a default html file and your zip folder. Delete the default file with
$sudo rm filename.html.

14. Next we're going to want to unzip the folder. In order to unzip the folder, you have to use $sudo apt install unzip to download the unzip package. Once installed run the command
$sudo unzip Folder.zip

15. Use the $ls command to double check that all files have been unzipped. You can remove the folder if you want to so it does not take more storage using the $sudo rm -R Foler.zip command.

16. Now if you try to search for your website on a browser with the ipv4, you will shown  an Error. You have to rename your main html file to index.html file in order to detect it. But if ever you have
multiple pages and your new index.html file is the home page. Make sure to add it back into the /var/www/html directory. Use the same command $sudo scp filename user@server_address:/var/www/html
 
