FROM ubuntu:latest

LABEL maintainer="Amir Aghaee"

ENV DEBIAN_FRONTEND=noninteractive

RUN apt-get update \
    && apt-get install -y gnupg tzdata \
    && echo "UTC" > /etc/timezone \
    && dpkg-reconfigure -f noninteractive tzdata

RUN apt-get update \
    && apt-get install -y curl zip unzip net-tools \
    nginx php7.4-fpm php7.4-cli supervisor \
    php7.4-pgsql php7.4-sqlite3 php7.4-gd \
    php7.4-curl php7.4-memcached \
    php7.4-imap php7.4-mysql php7.4-mbstring \
    php7.4-xml php7.4-zip php7.4-bcmath php7.4-soap \
    && apt-get -y autoremove \
    && apt-get clean \
	&& echo "daemon off;" \
    && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*
	
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

RUN ln -sf /dev/stdout /var/log/nginx/access.log \
    && ln -sf  /dev/stderr /var/log/nginx/error.log

ADD nginx.default /etc/nginx/sites-available/default
ADD supervisord.conf /etc/supervisor/conf.d/supervisord.conf
ADD start-container.sh /usr/bin/start-container
RUN chmod +x /usr/bin/start-container

ENTRYPOINT ["start-container"]
