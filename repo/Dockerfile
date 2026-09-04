FROM php:8.3-apache

# PostgreSQL driver
RUN docker-php-ext-install pdo pdo_pgsql

# App code
COPY site/ /var/www/html/

# Render injects a PORT env var at runtime and routes traffic to it —
# rewrite Apache's listen port at container start (see docker-entrypoint.sh).
COPY docker-entrypoint.sh /usr/local/bin/docker-entrypoint.sh
RUN chmod +x /usr/local/bin/docker-entrypoint.sh

EXPOSE 10000
ENTRYPOINT ["docker-entrypoint.sh"]
CMD ["apache2-foreground"]
