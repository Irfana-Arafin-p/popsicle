FROM php:8.3-fpm

# Install NGINX and other dependencies
RUN apt-get update && apt-get install -y \
    nginx \
    supervisor \
    && apt-get clean

# Copy NGINX config
COPY ./docker/nginx/default.conf /etc/nginx/conf.d/default.conf

# Configure supervisord to run php-fpm and nginx together
COPY ./docker/supervisord.conf /etc/supervisor/conf.d/supervisord.conf

# Set working directory
WORKDIR /var/www/html

# Expose port
EXPOSE 80

CMD ["/usr/bin/supervisord"]

