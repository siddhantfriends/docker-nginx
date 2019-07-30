FROM    php:5.6-fpm
LABEL   maintainer="Siddhant Baviskar <@siddhantfriends>"

RUN     pecl install xdebug-2.5.5 \
        && docker-php-ext-enable xdebug \
        && echo "xdebug.remote_enable=1" >> /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini \
        && echo "xdebug.remote_host=host.docker.internal" >> /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini
RUN     apt-get update && apt-get install -y libmcrypt-dev
RUN     docker-php-ext-install mcrypt
RUN     cd ~ && curl -sS https://getcomposer.org/installer -o composer-setup.php \
        && php composer-setup.php --install-dir=/usr/local/bin --filename=composer
