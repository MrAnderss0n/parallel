FROM 'dockerhub.ir/php:7.4.19-zts-buster'

RUN apt-get update && apt-get install -y \
	autoconf \
	subversion \
	build-essential \
	bash \
	curl \
	vim \
	git \
	wget \
	unzip \
	net-tools \
	libxml2-dev \
	libfreetype6-dev \
	libcurl4-openssl-dev \
	libc6-dev \
	librabbitmq-dev

RUN docker-php-source extract \
    && docker-php-ext-install pdo_mysql \
    && pecl install redis && docker-php-ext-enable redis \
    && pecl install parallel && docker-php-ext-enable parallel \
    && pecl install amqp && docker-php-ext-enable amqp \
    && docker-php-source delete

RUN php -m

RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/bin --filename=composer

ENTRYPOINT ["docker-php-entrypoint"]
CMD ["php", "-a"]