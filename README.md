# Site Configuration (CentOS)
### Install Git
Install the latest version of Git [from source](https://www.digitalocean.com/community/tutorials/how-to-install-git-on-centos-7).
### Install php
October CMS needs PHP version 7.0 or higher compiled with cURL, PDO, OpenSSL, Mbstring, ZipArchive and GD PHP Library enabled. Don't forget to add appropriate DB library: `php-mysql` for MySQL, `php-pgsql` for PostgreSQL, etc. Like that:
```sh
yum install php-cli php-fpm php-pdo php-common php-curl php-json php-zip php-gd php-xml php-mbstring php-pgsql
```
### Install Database
- Install any database server from the list: MySQL, MariaDB, PostgreSQL or SQLite.
- Create database for October CMS back-end named '\<your-db-name\>'.

##### PostgreSQL config
To allow October CMS to log in  to your PostgreSQL server find `pg_hba.conf` file and add following lines to the beginning of table in the end of the file:
```
local   <your-db-name>      all                                     trust
host    <your-db-name>      all             127.0.0.1/32            trust
host    <your-db-name>      all             ::1/128                 trust
```
### Apache
- Ensure Apache HTTP server (httpd) is installed.
- Add directory for your October CMS in its public folder. For example: `/var/www/myoctober`.
- Configure Apache's directory root to `/var/www/myoctober`:
```DocumentRoot "/var/www/site"
<Directory "/var/www/site">
    AllowOverride All
    Require all granted
</Directory>
```

### Install October CMS
- Download October CMS [install wizard archive](http://octobercms.com/download) and extract it into `/var/www/myoctober`.
- Grant writing permissions (for apache user) on the installation directory and all its subdirectories and files.
- In your web browser navigate to `<server-path>/install.php`.
- Follow the installation instructions.
- Delete the installation files for security reasons: installation directory `install_files/` and installation script `install.php`.

More help [here](https://octobercms.com/docs/setup/installation#wizard-installation)
### Add lsFusion theme
- In your web browser navigate to `<server-path>/backend` and log in as admin.
- Navigate to Settings -> Front-end theme.
- 'Create new blank theme' with name 'lsfusion'. This will create folder `/var/www/myoctober/themes/lsfusion`.
- 'Activate' lsfusion theme.
- Checkout source files from [lsFusion theme GitHub repository](https://github.com/lsfusion/site) into `/var/www/myoctober/themes/lsfusion`.

# Local Configuration on Windows
The easiest way is to install one of Windows distributions that contain Apache, PHP, MySQL and other applications in a single installation file, e.g. [XAMPP](http://www.apachefriends.org/en/xampp.html), [WampServer](http://www.wampserver.com/en/) or [Web.Developer](http://www.devside.net/server/webdeveloper).
WampServer has been successfully tested. Configuration is similar to the described CentOS configuration.
Then you can work with source files in the `lsfusion` theme folder in your editor.
