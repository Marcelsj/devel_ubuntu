FROM ubuntu:latest

WORKDIR /home

RUN apt-get update && apt-get install

RUN apt-get install nano \
    && apt-get install git -y \
    && apt-get install git-flow \
    && apt-get install curl -y \
    && export DEBIAN_FRONTEND=noninteractive \
    && apt-get -yq install php \
    && apt-get -y install php-cli \
    && apt-get -y install php-mbstring \
    && apt-get -y install zip \
    && curl -sS https://getcomposer.org/installer -o composer-setup.php \
    && php composer-setup.php --install-dir=/usr/local/bin --filename=composer

COPY apache2.conf /etc/apache2/apache2.conf

RUN service apache2 start

EXPOSE 80

CMD apachectl -D FOREGROUND