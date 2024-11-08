FROM nimmis/apache-php5

COPY apache_default /etc/apache2/sites-enabled/000-default.conf
COPY envvars /etc/apache2/envvars
COPY ./run /usr/local/bin/run
# COPY my.cnf /etc/mysql/conf.d/my.cnf

RUN chmod +x /usr/local/bin/run
RUN a2enmod rewrite
RUN usermod -aG staff www-data
RUN useradd -d /var/www/soxbox -u 1000 -G www-data,staff -M soxbox

# Configure /app folder with sample app
RUN mkdir -p /app && ln -s /app /var/www/soxbox
RUN mkdir -p /var/www/Cache && chown soxbox:staff /var/www/Cache
RUN mkdir -p /import && chown soxbox:staff /import && ln -s /import /var/www/import

VOLUME ["/app"]

# EXPOSE 80 3306
CMD ["/usr/local/bin/run"]
