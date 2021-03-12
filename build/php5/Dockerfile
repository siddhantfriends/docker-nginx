FROM    php:5.6-fpm
LABEL   maintainer="Siddhant Baviskar <@siddhantfriends>"

RUN     pecl install xdebug-2.5.5 \
        && docker-php-ext-enable xdebug \
        && echo "xdebug.remote_enable=1" >> /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini \
        && echo "xdebug.remote_host=host.docker.internal" >> /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini
RUN     apt-get update && apt-get install -y libmcrypt-dev git unzip libpng-dev telnet
RUN     docker-php-ext-install opcache
RUN     apt-get install -y libmemcached-dev \
        && apt-get -y install autoconf make gcc g++ \
        && echo "no --disable-memcached-sasl" | pecl install memcached-2.2.0 \
        && docker-php-ext-enable memcached
RUN     docker-php-ext-install mcrypt pcntl pdo pdo_mysql gd 
RUN     cd ~ && curl -sS https://getcomposer.org/installer -o composer-setup.php \
        && php composer-setup.php --install-dir=/usr/local/bin --filename=composer
RUN     mkdir -p /var/lib/php/sessions && chmod a+rwx /var/lib/php/sessions \
        && cp /usr/local/etc/php/php.ini-development /usr/local/etc/php/php.ini \
        && echo "session.save_path = \"/var/lib/php/sessions\"" >> /usr/local/etc/php/php.ini \
        && echo "always_populate_raw_post_data = -1" >> /usr/local/etc/php/php.ini
