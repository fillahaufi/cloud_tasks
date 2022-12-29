FROM wordpress:latest

# Install any additional packages or dependencies needed for WordPress
# RUN apt-get update && apt-get install -y plugin1 plugin2 ...

# Set environment variables for WordPress
ENV WORDPRESS_DB_HOST=db:3306 \
    WORDPRESS_DB_USER=user \
    WORDPRESS_DB_PASSWORD=password \
    WORDPRESS_DB_NAME=db

# Expose the port that WordPress will be running on
EXPOSE 80

# Set the command to start the WordPress server
CMD ["/usr/sbin/apache2ctl", "-D", "FOREGROUND"]

FROM mysql:5.7

# Set environment variables for MySQL
ENV MYSQL_ROOT_PASSWORD=root \
    MYSQL_DATABASE=db \
    MYSQL_USER=user \
    MYSQL_PASSWORD=password

# Set the volume for the MySQL data directory
VOLUME /var/lib/mysql

# Set the command to start the MySQL server
CMD ["mysqld"]

FROM phpmyadmin/phpmyadmin

# Install any additional packages or dependencies needed for phpMyAdmin
# RUN apt-get update && apt-get install -y libfreetype6-dev libjpeg62-turbo-dev ...
RUN apt-get update && apt-get install -y \
    libfreetype6-dev \
    libjpeg62-turbo-dev \
    libpng-dev \
    libicu-dev \
    libzip-dev \
    libsasl2-dev

# Set environment variables for phpMyAdmin
ENV PMA_HOST=db \
    PMA_PORT=3306 \
    PMA_USER=user \
    PMA_PASSWORD=password

# Expose the port that phpMyAdmin will be running on
EXPOSE 80

# Set the command to start the phpMyAdmin server
# CMD ["/usr/local/bin/phpmyadmin-start"]

# Set the network for the containers
# NETWORK wpsite

# Create the volumes for the data directories
VOLUME wp_data
VOLUME db_data
