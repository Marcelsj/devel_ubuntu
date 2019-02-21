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
    && php composer-setup.php --install-dir=/usr/local/bin --filename=composer \
    && apt-get install php-xml -y \
    && apt-get install php-curl -y \
    && apt-get install php-zip -y

COPY apache2.conf /etc/apache2/apache2.conf

RUN service apache2 start
RUN curl -sS https://get.symfony.com/cli/installer | bash \
    && mv /root/.symfony/bin/symfony /usr/local/bin/symfony
RUN   git config --global user.email "marcel.serra@gmail.com" \
      && git config --global user.name "Marcelsj"


WORKDIR /var/www/html

EXPOSE 80

CMD apachectl -D FOREGROUND