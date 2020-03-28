FROM php:7.3.3-apache
WORKDIR /var/www/html/
RUN apt-get update && apt-get upgrade -y
RUN rm /etc/apt/preferences.d/no-debian-php
RUN apt-get install php-mysql php7.0-mysql -y
RUN phpenmod pdo_mysql
RUN docker-php-ext-install mysqli
RUN docker-php-ext-install pdo
RUN apt-get install php7.0-pgsql libapache2-mod-php7.0 libpq-dev -y
RUN docker-php-ext-install pgsql
RUN docker-php-ext-install pdo_pgsql
RUN docker-php-ext-install pdo_mysql
RUN apt-get install php7.0-zip -y
RUN apt-get install php7.0-mbstring -y
RUN apt-get install php7.0-dom -y
RUN apt-get install php7.0 -y
RUN apt-get install composer -y
RUN apt-get install vim -y

#RUN composer create-project --prefer-dist laravel/laravel ProyectoNuevo

#RUN composer update 
#RUN /ProyectoNuevo/php artisan key:generate
#RUN /ProyectoNuevo/php artisan optimize
#RUN chmod -R 777 /ProyectoNuevo/storage /ProyectoNuevo/bootstrap/cache

RUN a2enmod rewrite
RUN cp /etc/apache2/sites-available/000-default.conf /etc/apache2/sites-available/laravel.conf
COPY ./sites/laravel_project.conf /etc/apache2/sites-available/
 
RUN a2ensite laravel_project.conf
RUN a2dissite 000-default.conf
RUN chmod -R 777 /var/www/html


RUN apt-get update -y
EXPOSE  80
EXPOSE  8080
EXPOSE  8180
