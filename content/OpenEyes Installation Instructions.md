This document provides the basic instructions for the installation of OpenEyes v6.8.0 directly (bare metal) onto a Linux instance.

While the original instructions require you to install as a non-root user "openeyes", this can also be done as root. Some variables are encapsulated between angular brackets "<>" but I'll include default values below the code blocks.

## Installing Dependencies
#### Apache Web Server
1. Install Apache Webserver
```bash=
sudo apt update -y \
&& sudo apt install apache -y
```
2. Disabling the firewall for the installation process
```bash
sudo ufw disable
```
3. Activate Apache Rewrite Engine and Headers Mods
```bash
sudo a2enmod rewrite \
&& sudo a2enmod headers
```
4. Restart Apache2 service
```bash=
sudo systemctl restart apache2
```
#### PHP
1. Install Php 7.4
```bash=
sudo apt-get update -y \
&& sudo apt -y install software-properties-common \
&& sudo add-apt-repository "ppa:ondrej/php" -y \
&& sudo apt update -y \
&& sudo apt install -y php7.4 \
&& php -v
```
2. Install OpenEyes PHP Dependencies
```bash=
sudo apt install -y \
    php7.4-curl \
    php7.4-mysql \
    php7.4-xml \
    php7.4-gd \
    php7.4-mbstring \
    php7.4-zip \
    php7.4-gd \
    phpunit \
    libnss3 \
    libxss1 \
    libasound2t64 \
    php7.4-soap \
    php7.4-imagick
```
3. Install proper NPM version
```bash=
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.1/install.sh | bash source ~/.bashrc 
nvm install 16.20.2 
nvm use 16.20.2 
--version
```
4. Install NodeJS
```bash=
sudo apt install nodejs unzip
sudo service apache2 restart
```
5. Install MariaDB
```bash=
sudo apt update \
&& sudo apt install -y mariadb-client-core-10.* \
&& sudo apt install mariadb-server \
&& sudo mysql_secure_installation
```
6. Switching to MariaDB to set-up basic components of OpenEyes Database
```bash=
mariadb --host <IP or host> --user root -p
```
From my use case, **(IP or host)** = *"localhost"*
This will open the MariaDB command line:
6.1 Create the user
```sql=
CREATE user openeyes;
```
6.2 Update the password for the user 'openeyes'
```sql=
SET PASSWORD FOR openeyes = PASSWORD('openeyes');
```
6.3 Create the database
```sql=
CREATE database openeyes;
```
6.4 Grant ALL privileges (caution, for development only):
```sql=
GRANT ALL PRIVILEGES ON *.* TO 'openeyes'@'%';
```
6.5 Flush privileges
```sql_more=
FLUSH PRIVILEGES;
```
6.6 Exit MariaDB command line
```sql_more=
EXIT;
``` 
7. Test Database connection
```bash=
mysql --host=localhost --user=openeyes --password=openeyes --database=openeyes --execute="SELECT now()"
```
8. Download sample database
```bash=
wget https://github.com/AppertaFoundation/openeyes-sample-db/raw/refs/heads/release/v6.8.0/sql/sample_db.zip
```

9. Convert database from zip to tar.gz
```bash=
cp sample_db.zip sample_db.sql.gz
```
10. Unzip database
```bash=
gzip -d sample_db.sql.gz
```

11. Import sample database data to OpenEyes Database
```bash=
mysql --host=localhost --user=openeyes --password=openeyes --database openeyes < sample_db
```

12. Import sample database data to OpenEyes Database
```bash=
mysql --host=localhost --user=openeyes --password=openeyes --database=openeyes --execute="SELECT * FROM user LIMIT 1"
```

## Installing OpenEyes
1. Downloading source code
```bash=
sudo git clone https://github.com/AppertaFoundation/openeyes.git /var/www/openeyes
```
2. Update NPM
```bash=
cd /var/www/openeyes/ \
&& npm i
```
3. Run Composer
```bash=
cd /var/www/openeyes \
&& curl -sS https://getcomposer.org/installer -o /tmp/composer-setup.php \
&& sudo php /tmp/composer-setup.php --install-dir=/usr/local/bin --filename=composer --version=2.2.0 \
&& composer install
```
4. Make local user owner of OpenEyes site directory
```bash=
sudo chown -R root:root /var/www/openeyes
```
I used root as I logged in using the root account.
5. Initialize the Eyedraw Module
```bash=
cd /var/www/openeyes/protected \
&& git submodule init \
&& git submodule update
```
6. Update database details
```bash=
sudo mkdir /etc/openeyes
sudo sh -c 'echo "host=localhost 
port=3306
dbname=openeyes
username=openeyes
password=openeyes" >> /etc/openeyes/db.conf'
```
7. Install Node Dependencies for OpenEyes
```bash=
npm install sortablejs
```
8. Copy over YIIC config files
```bash=
sudo mkdir -p /var/www/openeyes/protected/config/local
cd /var/www/openeyes/protected/config
sudo cp local.sample/common.sample.php local/common.php
sudo cp local.sample/console.sample.php local/console.php
sudo cp local.sample/test.php local/test.php
```
9. Update directory permissions
```bash=
sudo chown -R www-data:www-data /var/www/openeyes/protected/config/local
sudo chmod -R 775 /var/www/openeyes/protected/config/local
sudo chmod -R 775 /var/www/openeyes/protected/runtime
```
10. Initiate YIIC Migration
```bash=
cd /var/www/openeyes/protected && php yiic migrate --interactive=0 && php yiic migratemodules --interactive=0 
```
11. Restart Apache Service
```bash=
sudo systemctl reload apache2 \
&& sudo systemctl start mariadb \
&& sudo systemctl enable mariadb \
&& echo "Success"
```
## Configuring Apache Webserver to OpenEyes
1. Create OpenEyes Config file
```bash=
sudo nano /etc/apache2/sites-available/openeyes.conf
```
1.a. Paste the following for the config file:
```apache=
<VirtualHost *:80>
    ServerAdmin webmaster@localhost
    DocumentRoot /var/www/openeyes
    
    <Directory /var/www/openeyes>
        Options FollowSymLinks
        AllowOverride All
        Require all granted
        DirectoryIndex index.php index.html
        
        # Enable URL rewriting
        RewriteEngine On
    </Directory>
    
    # Logging
    ErrorLog ${APACHE_LOG_DIR}/openeyes_error.log
    CustomLog ${APACHE_LOG_DIR}/openeyes_access.log combined
</VirtualHost>
```
2. Enable the Site and Modules
```bash=
sudo a2dissite 000-default.conf
sudo a2ensite openeyes.conf
sudo a2enmod rewrite 
sudo systemctl restart apache2
```
3. Enable the Site and Modules
```bash=
sudo chown -R www-data:www-data /var/www/openeyes
sudo chmod -R 755 /var/www/openeyes
```
4. Check Key Directories
```bash=
sudo mkdir -p /var/www/openeyes/protected/runtime
sudo chmod -R 775 /var/www/openeyes/protected/runtime
```
5. Ensure Apache Webserver is running
```bash=
sudo systemctl status apache2
```
