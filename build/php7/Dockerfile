FROM    php:7.1-fpm
LABEL   maintainer="Siddhant Baviskar <@siddhantfriends>"

RUN     pecl install xdebug && docker-php-ext-enable xdebug \ 
        && echo "xdebug.remote_enable=1" >> /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini \
        && echo "xdebug.remote_host=host.docker.internal" >> /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini
RUN     docker-php-ext-install bcmath pcntl pdo pdo_mysql
RUN     cd ~ && curl -sS https://getcomposer.org/installer -o composer-setup.php \
        && php composer-setup.php --install-dir=/usr/local/bin --filename=composer
RUN     apt-get update && apt-get install -y git unzip
RUN     mkdir -p /var/lib/php/sessions && chmod a+rwx /var/lib/php/sessions \
        && cp /usr/local/etc/php/php.ini-development /usr/local/etc/php/php.ini \
        && echo "session.save_path = \"/var/lib/php/sessions\"" >> /usr/local/etc/php/php.ini
