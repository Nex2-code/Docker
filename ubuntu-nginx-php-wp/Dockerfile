FROM ubuntu
RUN apt-get update && ln -fs /usr/share/zoneinfo/America/New_York /etc/localtime && apt-get install -y tzdata && dpkg-reconfigure --frontend noninteractive tzdata && apt-get install -y nginx \
php-fpm \
php-mysql \
php-gd \
php-common \
php-mbstring \
php-curl \
php-cli \
supervisor 
RUN mv /var/www/html/index.nginx-debian.html /var/www/html/index.php && sed -i '2i <?php echo "Hello"; echo gethostname();?>' /var/www/html/index.php && sed -i '2!d' /var/www/html/index.php && rm -rf /etc/nginx/sites-available/default
COPY default.conf /etc/nginx/sites-available/default
COPY supervisord.conf /etc/supervisor/conf.d/supervisord.conf
EXPOSE 80 
CMD ["/usr/bin/supervisord"]
