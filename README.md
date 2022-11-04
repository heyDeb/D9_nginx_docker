# D9_nginx_docker
Now, you can use this with your docker-compose yaml to connect separate DB host and execute the project.

This image is built up on Ubuntu 22.04 and top of it we have nginx web server with PHP 8.1 packages are installed. PHP configuration is already made, and installation of all PHP modules and composer are done to run Drupal 9 based web application.

Example docker-compose.yaml code can be downloaded here : https://github.com/heyDeb/D9_nginx_docker

After cloning the project from github, run the below command. docker-compose up -d

then, run the following command to know the container name and in this case its drupal9_web
: docker ps

docker exec -ti drupal9_web bash
if you are working from windows os git bash, then add a prefix winpty before docker exec command.
cd /var/www/html/waterfallhandbook
composer install
And run the restart of php-fpm service

service php8.1-fpm start

And to install drush and drush launcher: composer require drush/drush
wget -O drush.phar https://github.com/drush-ops/drush-launcher/releases/latest/download/drush.phar
chmod +x drush.phar && mv drush.phar /usr/local/bin/drush
drush st

Hit the URL in your browser if you have localhost, http://localhost:8998/ That's All.
