FROM php:7.4.7-cli
LABEL Name=deployerstudy Version=0.0.1

RUN apt-get update && apt-get install -y unzip

RUN php -r "readfile('https://getcomposer.org/installer');" > composer-setup.php ;\
    php composer-setup.php --filename=composer;\
    php -r "unlink('composer-setup.php');" ;\
    mv composer /usr/local/bin/composer

RUN curl -LO https://deployer.org/deployer.phar && \
    mv deployer.phar /usr/local/bin/dep && \
    chmod +x /usr/local/bin/dep

WORKDIR /var/www/local.deployer
COPY local.deployer .
