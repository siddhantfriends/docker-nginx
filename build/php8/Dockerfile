FROM    php:8.0.2-fpm
LABEL   maintainer="Siddhant Baviskar <@siddhantfriends>"

RUN     pecl install xdebug && docker-php-ext-enable xdebug \ 
        && echo "xdebug.mode=develop,debug" >> /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini \
        && echo "xdebug.client_host=host.docker.internal" >> /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini
RUN     docker-php-ext-install bcmath
RUN     cd ~ && curl -sS https://getcomposer.org/installer -o composer-setup.php \
        && php composer-setup.php --install-dir=/usr/local/bin --filename=composer
RUN     mkdir -p /var/lib/php/sessions && chmod a+rwx /var/lib/php/sessions \
        && cp /usr/local/etc/php/php.ini-development /usr/local/etc/php/php.ini \
        && echo "session.save_path = \"/var/lib/php/sessions\"" >> /usr/local/etc/php/php.ini
RUN     apt-get update && apt-get install -y git zip unzip
