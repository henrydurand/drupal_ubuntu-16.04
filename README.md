sudo su
apt-get update
apt-get upgrade -y
apt-get dist-upgrade -y
apt-get autoremove -y
apt-get install apache2 php php-cli php-fpm php-gd php-ssh2 libapache2-mod-php php-mcrypt php-mysql git unzip zip postfix php-curl php-xml mailutils php-json -y
a2enmod rewrite headers
phpenmod mcrypt

nano /etc/apache2/sites-enabled/000-default.conf

<VirtualHost *:80>
        #ServerName example.com
        #ServerAlias www.example.com
        DocumentRoot /var/www/drupal

        <Directory /var/www/drupal>
                Options -Indexes
                AllowOverride All
                Order allow,deny
                Allow from all
        </Directory>
</VirtualHost>

cd /var/www
wget http://ftp.drupal.org/files/projects/drupal-7.36.zip
unzip drupal-7.36.zip
mv drupal-7.36 drupal
cd drupal
chmod -R 744 .
chown -R www-data:www-data .

service apache2 restart
