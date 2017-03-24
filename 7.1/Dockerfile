FROM php:7.1

RUN apt-get update && apt-get install -y \
		git \
		zip \
		unzip


RUN curl --location --output /usr/local/bin/composer https://getcomposer.org/composer.phar && \
		chmod a+x /usr/local/bin/composer && \
		curl --location --output /usr/local/bin/phpunit https://phar.phpunit.de/phpunit.phar && \
		chmod a+x /usr/local/bin/phpunit && \
		curl --location --output /usr/local/bin/phpcs https://squizlabs.github.io/PHP_CodeSniffer/phpcs.phar && \
		chmod a+x /usr/local/bin/phpcs && \
		curl --location --output /usr/local/bin/dep https://deployer.org/deployer.phar && \
		chmod a+x /usr/local/bin/dep

