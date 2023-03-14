# MY PROJEECT1 DOCUMENTATION

## INSTALLING APACHE AND UPDATING THE FIREWALL

### update a list of packages in package manager
`sudo apt update`
    ![image of apt update](./Images/Image2.PNG)
    ---
 ### run apache2 package installation
`sudo apt install apache2`
    ![image of running apache2](./Images/Apache2.PNG)

    ---
### run apache2 package installation CONTINUE
`sudo apt install apache2`
    ![image of running apache2-1](./Images/Apache2.PNG)

    ---
### verify apache2 package installation
`sudo systemctl status apache2`
    ![image of verifying apache2 package installation](./Images/Apache2-status.PNG)

    ---
### checking apache locally
 `curl http://localhost:80`
 [checking apache locally](http://localhost:80)
![image of checking apache locally](./Images/Apache-view.PNG)

    ---
## checking public address
 `curl http://localhost:80`
 [checking public address](http://localhost:80)
![image of checking public address](./Images/Apache-view.PNG)

    ---
## checking public address continues
 `curl http://localhost:80`
 [checking public address](http://localhost:80)
![image of checking public address](./Images/Apache-view2.PNG)

    ---
## INSTALLING MYSQL

### acquire and install
`sudo apt install mysql-server`
    ![image of install mysql](./Images/installMYSQL.PNG)
    ---
### see mysql log
` sudo mysql`
    ![image of mysql log](./Images/MYSQL.PNG)
    ---
### alter user
` ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'PassWord.1';`
    ![image of ALTER USER with password](./Images/alteruser.PNG)
    ---
### exit mysql
` exit`
    ![image of exit mysql](./Images/exit.PNG)
    ---
### securing mysql
` sudo mysql_secure_installation`
    ![image of secure installation](./Images/exit.PNG)
    ---
## INSTALLING PHP

### install
`sudo apt install php libapache2-mod-php php-mysql`
    ![image of install all three PHP packages](./Images/installPHP.PNG)
    ---
### confirm PHP
` php -v`
    ![image of mysql installed](./Images/confirmPHP.PNG)
    ---
## CREATING VIRTUAL HOST

### mkdir and access 
` sudo mkdir /var/www/projectlamp`
` sudo chown -R $USER:$USER /var/www/projectlamp`
` sudo vi /etc/apache2/sites-available/projectlamp.conf`
<VirtualHost *:80>
    ServerName projectlamp
    ServerAlias www.projectlamp 
    ServerAdmin webmaster@localhost
    DocumentRoot /var/www/projectlamp
    ErrorLog ${APACHE_LOG_DIR}/error.log
    CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>
----
1. Hit the esc button on the keyboard
2. Type :
3. Type wq. w for write and q for quit
4. Hit ENTER to save the file

`sudo ls /etc/apache2/sites-available`
`sudo a2ensite projectlamp`
`sudo a2dissite 000-default`
`sudo apache2ctl configtest`
`sudo systemctl reload apache2`
`sudo echo 'Hello LAMP from hostname' $(curl -s http://169.254.169.254/latest/meta-data/public-hostname) 'with public IP' $(curl -s http://169.254.169.254/latest/meta-data/public-ipv4) > /var/www/projectlamp/index.html`

![image of install all three PHP packages](./Images/mkdir-access.PNG)
    ---
### open website
[Open site with IP Address](http://18.234.126.228:80)
    ![image of website](./Images/website.PNG)
    ---
### open website
[Open site with IP Address](http://18.234.126.228:80)
    ![image of website](./Images/website.PNG)
    ---

## ENABLING PHP

### Directory Index
`sudo vim /etc/apache2/mods-enabled/dir.conf`
<IfModule mod_dir.c>
        #Change this:
        #DirectoryIndex index.html index.cgi index.pl index.php index.xhtml index.htm
        #To this:
        DirectoryIndex index.php index.html index.cgi index.pl index.xhtml index.htm
</IfModule>`

1. Hit the esc button on the keyboard
2. Type :
3. Type wq. w for write and q for quit
4. Hit ENTER to save the file

`sudo systemctl reload apache2`

`vim /var/www/projectlamp/index.php`

<?php
phpinfo();

1. Hit the esc button on the keyboard
2. Type :
3. Type wq. w for write and q for quit
4. Hit ENTER to save the file

` sudo rm /var/www/projectlamp/index.php`
    ![image of mysql log](./Images/directoryind.PNG)
    ---

