# Alpine Linux
Built with **_musl_** and **_BusyBox_** by default a full server distro is 400-500 Mb. 
(there are **_glibc_** builds too, but they are much large, in the 1-3 Gb range). 
Version 3.12 is the latest at time of writing.

## nginx
 - `apk add nginx nginx-mod-http-fancyindex`
 - (< 3.9) `addgroup -g 82 -S www-data`
 - (< 3.9) `adduser -u 82 -D -S -G www-data www-data`

## php7
 - part of package repository since Alpine Linux 3.4
 - `apk php7-fpm php7-gd php7-mysql php7-mbstring php7-mcrypt php7-sqlite3 \`
 - `php7-json php7-intl php7-curl php7-bz2 php7-zip php7-soap \`
 - `php-oauth php-imagick php-gmagick php-redis php-uploadprogress php-geoip`

## php5
 - (suitable to run (PHP Navigator)[http://navphp.sourceforge.net/] )
 - EOL 10 Jan 2019, security updates only, **5.6.40**, last version in Alpine Linux 3.4
 - must be built by hand (from here)[https://www.php.net/releases/#5.6.40] after adding **build-requirements**.
 - `apk add --no-cache --virtual .php-build-deps $BUILD_DEPS \`
 - ` libfcgi-dev libfcgi0ldbl \`
 - `	curl-dev libedit-dev libxml2-dev openssl-dev sqlite-dev \`
 - `	libfreetype6-dev libjpeg62-turbo-dev libmcrypt-dev libpng12-dev`
 - `export PHP_INI_DIR='/usr/local/etc/php5'`
 - `./configure --with-config-file-path="$PHP_INI_DIR" --with-config-file-scan-dir="$PHP_INI_DIR/conf.d" \`
 - `	--disable-cgi --enable-fpm --with-fpm-user=www-data --with-fpm-group=www-data \`
 - ` --enable-ftp --enable-mbstring --enable-mysqlnd --enable-sqlite \`
 - `	--with-curl --with-libedit --with-openssl --with-zlib`
 -  build options (taken from a Ubuntu 16.04 install)[https://www.howtoforge.com/tutorial/how-to-install-php-5-6-on-ubuntu-16-04/]
 - `./configure --prefix=/opt/php-5.6.30 --with-pdo-pgsql --with-zlib-dir --with-freetype-dir --enable-mbstring \`
 - ` --with-libxml-dir=/usr --enable-soap --enable-calendar --with-curl --with-mcrypt --with-zlib --with-gd \`
 - ` --with-pgsql --disable-rpath --enable-inline-optimization --with-bz2 --with-zlib \`
 - ` --enable-sockets --enable-sysvsem --enable-sysvshm --enable-pcntl --enable-mbregex --enable-exif \`
 - ` --enable-bcmath --with-mhash --enable-zip --with-pcre-regex \`
 - ` --with-mysql --with-pdo-mysql --with-mysqli \`
 - ` --with-jpeg-dir=/usr --with-png-dir=/usr --enable-gd-native-ttf --with-openssl \`
 - ` --with-fpm-user=www-data --with-fpm-group=www-data --with-libdir=/lib/x86_64-linux-gnu \`
 - ` --enable-ftp --with-imap --with-imap-ssl --with-gettext --with-xmlrpc --with-xsl --with-kerberos --enable-fpm`

## build-requirements
 - (taken from **_php5.5-fpm-alpine-docker_**)
 - `export BUILD_DEPS='autoconf file g++ gcc libc-dev make pkgconf re2c'`
 - `apk add --no-cache --virtual .build-deps $BUILD_DEPS`
 - ``
 
