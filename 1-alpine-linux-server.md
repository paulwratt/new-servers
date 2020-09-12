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
 - `	curl-dev libedit-dev libxml2-dev openssl-dev sqlite-dev \`
 - `	libfreetype6-dev libjpeg62-turbo-dev libmcrypt-dev libpng12-dev`
 - `export PHP_INI_DIR='/usr/local/etc/php5'`
 - `./configure --with-config-file-path="$PHP_INI_DIR" --with-config-file-scan-dir="$PHP_INI_DIR/conf.d" \`
 - `	--disable-cgi --enable-ftp --enable-mbstring --enable-mysqlnd \`
 - `	--with-curl --with-libedit --with-openssl --with-zlib`

## build-requirements
 - (taken from **_php5.5-fpm-alpine-docker_**)
 - `export BUILD_DEPS='autoconf file g++ gcc libc-dev make pkgconf re2c'`
 - `apk add --no-cache --virtual .build-deps $BUILD_DEPS`
 - ``
 
