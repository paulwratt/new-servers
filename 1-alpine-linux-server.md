# Alpine Linux
Built with **_musl_** and **_BusyBox_** by default a full server distro is 400-500 Mb. 
(there are **_glibc_** builds too, but they are much large, in the 1-3 Gb range). 
Version 3.12 is the latest at time of writing.

## nginx
 - `apk add nginx nginx-mod-http-fancyindex`
 - (< 3.9) `addgroup -g 82 -S www-data`
 - (< 3.9) `adduser -u 82 -D -S -G www-data www-data`

## php7
 - (part of package repository since Alpine Linux 3.4)
 - `apk php7-fpm php7-gd php7-mysql php7-mbstring php7-mcrypt php7-sqlite3 \`
 - `php7-json php7-intl php7-curl php7-bz2 php7-zip php7-soap \`
 - `php-oauth php-imagick php-gmagick php-redis php-uploadprogress php-geoip`

## php5
 - (see [seperate file](./2-php5.6-build.md) needs to be built, v5.6.40)

## build-requirements
 - (taken from **_php5.5-fpm-alpine-docker_**)
 - `export BUILD_DEPS='autoconf file g++ gcc libc-dev make pkgconf re2c'`
 - `apk add --no-cache --virtual .build-deps $BUILD_DEPS`
 - ``
 
