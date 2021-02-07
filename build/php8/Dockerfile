FROM    php:8.0.2-fpm
LABEL   maintainer="Siddhant Baviskar <@siddhantfriends>"

RUN     docker-php-ext-install bcmath
RUN     cd ~ && curl -sS https://getcomposer.org/installer -o composer-setup.php \
        && php composer-setup.php --install-dir=/usr/local/bin --filename=composer
