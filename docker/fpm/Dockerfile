FROM wordpress:4.7.3-php5.6-fpm
MAINTAINER ok17 <kashimura@fotome.jp>

RUN pecl install xdebug \
    && docker-php-ext-enable xdebug


RUN { \
       echo '[www]'; \
       echo 'php_admin_value[upload_max_filesize] = 64M'; \
       echo 'php_admin_value[post_max_size] = 32M'; \
} > /usr/local/etc/php-fpm.d/www-orig.conf

## setting xdebug
RUN { \
		echo 'xdebug.enable=1'; \
		echo 'xdebug.remote_enable=1'; \
		echo 'xdebug.remote_connect_back=0'; \
	    echo 'xdebug.remote_autostart=1'; \
        echo 'xdebug.idekey=PHPSTORM'; \
        echo 'xdebug.remote_host=10.254.254.254'; \
        echo 'xdebug.profiler_enable=0'; \
        echo 'xdebug.remote_port=9001'; \
} > "$PHP_INI_DIR/conf.d/xdebug.ini"
RUN { \
        echo 'session.save_handler = files'; \
        echo 'session.save_path = /var/lib/php5/sessions'; \
        echo 'session.gc_maxlifetime = 1440'; \
} > "$PHP_INI_DIR/conf.d/session.ini"
