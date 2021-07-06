FROM ubuntu
RUN apt-get update && ln -fs /usr/share/zoneinfo/America/New_York /etc/localtime && apt-get install -y tzdata && dpkg-reconfigure --frontend noninteractive tzdata && apt-get install -y nginx \
php-fpm \
supervisor 
RUN mv /var/www/html/index.nginx-debian.html /var/www/html/index.php && sed -i '2i <?php echo "Hello"; echo gethostname();?>' /var/www/html/index.php && sed -i '2!d' /var/www/html/index.php && sed -i '21,71!d' /etc/nginx/sites-available/default && sed -i '24s/index\.html/index\.php/' /etc/nginx/sites-available/default && sed -i 's/#location/location/' /etc/nginx/sites-available/default && sed -i 's/#}/}/' /etc/nginx/sites-available/default && sed -i '40s/#//' /etc/nginx/sites-available/default && sed -i '37s/#//' /etc/nginx/sites-available/default && sed -i '49s/#//' /etc/nginx/sites-available/default
COPY supervisord.conf /etc/supervisor/conf.d/supervisord.conf
EXPOSE 80 
CMD ["/usr/bin/supervisord"]
