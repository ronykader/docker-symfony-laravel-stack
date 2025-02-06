FROM php:apache

# Set environment variables
ENV APACHE_DOCUMENT_ROOT=/var/www/html/public

# Set up Apache document root
RUN sed -ri -e 's!/var/www/html!${APACHE_DOCUMENT_ROOT}!g' /etc/apache2/sites-available/*.conf
RUN sed -ri -e 's!/var/www/!${APACHE_DOCUMENT_ROOT}!g' /etc/apache2/apache2.conf /etc/apache2/conf-available/*.conf

# Install Node.js and npm
RUN apt-get update && apt-get install -y \
    curl \
    && curl -fsSL https://deb.nodesource.com/setup_18.x | bash - \
    && apt-get install -y nodejs

# Install dependencies and required packages
RUN apt-get install -y \
    libicu-dev libzip-dev zip libjpeg-dev libpng-dev libfreetype6-dev git \
    && docker-php-ext-configure intl \
    && docker-php-ext-configure gd '--with-jpeg' '--with-freetype' \
    && docker-php-ext-install intl opcache pdo_mysql zip gd \
    && pecl install xdebug \
    && a2enmod rewrite

# INSTALL APCU
RUN pecl install apcu && docker-php-ext-enable apcu
RUN echo "extension=apcu.so" > /usr/local/etc/php/php.ini
RUN echo "apc.enable_cli=1" > /usr/local/etc/php/php.ini
RUN echo "apc.enable=1" > /usr/local/etc/php/php.ini
# APCU

# Install Composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

# Install Symfony CLI
#RUN curl -sS https://get.symfony.com/cli/installer | bash && mv /root/.symfony/bin/symfony /usr/local/bin/symfony

# Install Laravel CLI
#RUN composer global require laravel/installer

# Add Composer global bin directory to PATH
ENV PATH="/root/.composer/vendor/bin:$PATH"

# Install NVM
RUN curl https://raw.githubusercontent.com/creationix/nvm/master/install.sh | bash

# Set the working directory
WORKDIR /var/www/html

# Expose port 80
EXPOSE 80

# Start Apache
CMD ["apache2-foreground"]
