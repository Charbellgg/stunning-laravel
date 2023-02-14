## Introduction

This project consists of a step-by-step tutorial on how to deploy your laravel website using command line on Ubuntu. Using command line is useful when the server does not have a graphical user interface. Hence, this tutorial is really beneficial, especially for aspiring web developers.

## Commands used for the project

<b>sudo</b> Allows the user to have admin priviliges <br>
<b>apt-get</b> Allows the user to interact with advanced libraries and donwload them

## Checkpoint 1:
1.Go to GitHub and fork the repository. <br>
2.Ssh to your server using the ssh -i keyName username@dns.<br>
The i argument is used to take the keyName, the username is so that the website knows who is logging in, the dns is the website's address
3.Use: sudo apt-get install, to install all these libraries,“apache2”, “mysql-server”, “php-mysql”, “php”, “libapache2-mod-php”,
“php-mcrypt”, “php-pear”, “curl”, “php-curl”, “php-cli”, “git”.<br>
4.Execute the following command “a2enmod rewrite”.<br>
5.Restart apache2 using: sudo systemctl restart apache2.<br>

## Checkpoint 2:

1.Go to the html folder inside www folder which is inside var folder using one command, find the folder using: cd../../var/www/html<br>
2.Check that you're inside the directory using pwd<br>
3.Clone the repository using: git clone repositoryLink, the repositoryLink can be found on your github.<br>

## Checkpoint 3:

1. Download the composer using this command: curl -sS https://getcomposer.org/installer | sudo php -- --install-dir=/usr/local/bin — filename=composer<br>
2. Run "sudo composer install" inside your repository<br>

## Checkpoint 4:

1.Double check that you're in your repository using pwd.<br>
2.Create a file called .env which is a copy of .env.example using: cp .env.example .env<br>
3.Enter the .env file using the sudo vim .env command, then press "i" inside the file to insert. You can now change the value of APP_NAME to the value of your choice, do not include spaces.<br>
4.Save your changes using the esc key, then ":x", to save and exit the file.<br>
5.Execute the following command “sudo php artisan key:generate" to generate a value for the key inside the .env file.<br>

## Checkpoint 5:

1.Check if apache2 is installed using the "which apache2" command, if it's installed, find it's location using: find / -name "apache2.conf".<br>
2.Go to that directory using cd.<br>
3.When you list the files using "ls", you should find apache2.conf. Use "sudo vim apache2.conf" and add the following lines to it by pressing "i" when you enter the file: <Directory /var/www/html/stunning-laravel/public>. Don't forget to save using ":x".
Options Indexes FollowSymLinks
AllowOverride all
Require all granted
</Directory><br>
4.Go to the sites-enabled folder which is located inside apache2. Write the following lines to the folder below “<VirtualHost *:80>” and remove all similar lines from the file. 
ServerAdmin webmaster@localhost
DocumentRoot /var/www/html/stunning-laravel/public/<br>
5.Restart apache2 by using: sudo systemctl restart apache2.<br>

## Checkpoint 6:

1.Go to your repository using "cd../../var/www/html/repoName".<br>
2.Execute this command: “sudo chgrp -R www-data storage bootstrap/cache”. What this will do is let this file become avaiable.<br>
3.Execute this command: “sudo chmod -R ug+rwx storage bootstrap/cache”. What this will do is grant the user access to the read, write and execute actions inside this file.<br>


## Congrats! You have just deployed your laravel website on Ubuntu!
