#Errors
##Can't Install Any Thing

```shell
$sudo rm /var/lib/apt/lists/lock
sudo rm /var/cache/apt/archives/lock
sudo rm /var/lib/dpkg/lock
```


#INSTALL LAMP

### APACHE2
```shell
sudo apt-get update
sudo apt-get install apache2
```

### mcrypt

```shell
sudo apt-get -y install gcc make autoconf libc-dev pkg-config
sudo apt-get -y install libmcrypt-dev
sudo pecl install mcrypt-1.0.1
sudo bash -c "echo extension=/usr/lib/php/20170718/mcrypt.so > /etc/php/7.2/cli/conf.d/mcrypt.ini"
sudo bash -c "echo extension=/usr/lib/php/20170718/mcrypt.so > /etc/php/7.2/apache2/conf.d/mcrypt.ini"
sudo service apache2 restart
```

##PHP7.2

```shell
sudo apt-get install python-software-properties
sudo add-apt-repository ppa:ondrej/php
sudo apt-get update
sudo apt-get install -y php7.2
sudo apt-cache search php7-*
sudo apt-get install php7.2-mysql php7.2-curl php7.2-json php7.2-cgi php7.2-xsl php7.2-mbstring
```

##MYSQL5.7

```shell
sudo apt update
sudo apt install mysql-server
sudo mysql_secure_installation
sudo mysql
ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'root'; #mysql
FLUSH PRIVILEGES; #mysql
CREATE USER 'phpmyadmin'@'localhost' IDENTIFIED BY 'root';
GRANT ALL PRIVILEGES ON *.* TO 'phpmyadmin'@'localhost' WITH GRANT OPTION;
SELECT user,authentication_string,plugin,host FROM mysql.user; #mysql
sudo service mysql restart
sudo cp /usr/share/phpmyadmin/libraries/sql.lib.php /usr/share/phpmyadmin/libraries/sql.lib.php.bak
sudo gedit /usr/share/phpmyadmin/libraries/sql.lib.php
exit
```


> Press Ctrl + W And Search For (Count($Analyzed_sql_results['Select_expr'] == 1)
Replace It With ((Count($Analyzed_sql_results['Select_expr']) == 1)

##ALLOW HTTACCESS

```shell
sudo a2enmod rewrite
sudo nano /etc/apache2/apache2.conf
```

```rst
<Directory /var/www/>
    Options Indexes FollowSymLinks
    AllowOverride All
    Require all granted
</Directory>
```

```shell
sudo systemctl restart apache2

```
##PHPMYADMIN

```shell
sudo apt-get install phpmyadmin
sudo gedit /etc/apache2/apache2.conf
```
> 
add this to end of the file

> Include /etc/phpmyadmin/apache.conf

> at the end

```shell
sudo service apache2 restart
```

##ADD NEW VIRSUAL HOST

###### ##### #### ###  /etc/apache2/sites-available/work.dev.conf contains following lines

```rst
<VirtualHost *:80>

        ServerName work.com #must .com
        
        DocumentRoot /var/www/html/work/public
        
    ErrorLog ${APACHE_LOG_DIR}/error.log
    
        CustomLog ${APACHE_LOG_DIR}/access.log combined
        
        
    <Directory /var/www/html/work/public>
    
            AllowOverride All
            
            Require all granted
            
        </Directory>
        
</VirtualHost>

```
*add to hosts*

```shell
sudo gedit /etc/hosts

```
127.0.0.1 work.com #url work.com

enable site

```shell
sudo a2ensite work.com
service apache2 reload
```

##GIT


```shell
sudo apt-get install git

```
##zip

```shell
sudo apt-get install zip

```
##COMPOSER

```shell
sudo apt install curl

sudo apt install composer

curl -sS https://getcomposer.org/installer | php

sudo mv composer.phar /usr/local/bin/composer
```

##NODEJS

```shell
sudo apt-get install python-software-properties

curl -sL https://deb.nodesource.com/setup_8.x | sudo -E bash -

sudo apt-get install nodejs
```

##MONGODB

```shell
sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv 2930ADAE8CAF5059EE73BB4B58712A2291FA4AD5

echo "deb [ arch=amd64,arm64 ] https://repo.mongodb.org/apt/ubuntu xenial/mongodb-org/3.6 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-3.6.list

sudo apt-get update

sudo apt-get install -y mongodb-org

sudo service mongod start

sudo service mongodb start

sudo apt-get install php-dev

sudo pecl install memcache

sudo pecl install mongodb

Add mongodb.so to php.ini

sudo apt-get install php-mongodb

```
https://nosqlbooster.com/downloads

##REDIS

```shell
sudo add-apt-repository ppa:chris-lea/redis-server

sudo apt-get update

sudo apt-get install redis-server

sudo service redis-server start
```

#####   Laravel Redis ==>
 
```shell
 composer require predis/predis

``` 
```rst
CACHE_DRIVER=redis

SESSION_DRIVER=redis

CACHE_DRIVER=file

SESSION_DRIVER=file

QUEUE_DRIVER=sync

REDIS_HOST=127.0.0.1

REDIS_PASSWORD=null

REDIS_PORT=6379
```

##REDIS Manager

https://github.com/uglide/RedisDesktopManager/releases

```shell
sudo apt-get install gdebi

```
##BOWER

```shell
sudo npm install bower -g

```
##WINE

* If your system is 64 bit, enable 32 bit architecture!

```shell
sudo dpkg --add-architecture i386
```
```shell
wget -nc https://dl.winehq.org/wine-builds/Release.key

sudo apt-key add Release.key

sudo apt-add-repository 'deb http://dl.winehq.org/wine-builds/ubuntu/ xenial main'

sudo apt-get update

sudo apt-get install --install-recommends winehq-devel

winecfg
```

##RAR

```shell
sudo apt-get install unrar 

```
##Angularjs

```shell
npm config set unsafe-perm true

sudo npm install -g @angular/cli

ng new my-project-name
```

https://github.com/angular/angular-cli/wiki

##Monitor

## gnome-system-monitor

```shell
sudo apt-get install gnome-system-monitor

gnome-system-monitor
```

##Docker
```shell

sudo apt-get update

sudo apt-get install apt-transport-https ca-certificates  curl  software-properties-common

curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -

sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs)  stable"

sudo apt-get update

sudo apt-get install docker-ce

sudo apt install docker-compose

sudo usermod -aG docker engshokry

sudo chmod -R 777 /var/lib/docker/

sudo mkdir /var/lib/docker/tmp    ==> if not create

sudo systemctl start docker

```
##SWITCH PHP

```shell
sudo a2dismod php7.0 && sudo a2enmod php5.6 && sudo service apache2 restart

sudo ln -sfn /usr/bin/php5.6 /etc/alternatives/php
```

##Gdebi

```shell
sudo apt install gdebi

```
##Sendmail

```shell
sudo apt install sendmail
```

which sendmail

```shell
sudo gedit /etc/ssmtp/ssmtp.conf

```
##Config Sendmail

mailhub=smtp.gmail.com:587 ######YES 465 NO 587

rewriteDomain=gmail.com

AuthUser=sms.shokry.mohamed@gmail.com

AuthPass=password

UseSTARTTLS=YES

######FromLineOverride=YES

######UseTLS=YES # YES 465

##Keyboard

```shell
sudo apt-get install gnome-tweaks

```
Then Open Gnome Tweaks (Gnome-Tweaks).

Select Keyboard & Mouse Tab

Click Additional Layout Options Button

Expand Switching To Another Layout

Select Ctrl + Shift Here

See Screenshot Below:

https://i.stack.imgur.com/6eUtV.png

##create Short Icon to Your program

```shell
Installing gnome-panel

 sudo apt-get install --no-install-recommends gnome-panel
```
To create launcher

```shell
sudo gnome-desktop-item-edit /usr/share/applications/ --create-new

```
This will open up a "Create Launcher" window

```rst
Type: Application

Name: PhpStorm

Command: /bin/bash path_to/phpstorm.sh

Comment: Any Comment
```

This will create a launcher file in /usr/share/applications directory. Now double click and open the file.








