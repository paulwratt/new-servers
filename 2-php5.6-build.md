# PHP v5.6.40
Currently, the last version of PHP5, may get another security update in the future, if needed. (there are still a lot of PHP5 production servers).
I will try to find a cross platform build configuration suitable for production installation, not easy atm.

## php5
 - (suitable to run [PHP Navigator](http://navphp.sourceforge.net/).)
 - EOL 10 Jan 2019, security updates only, **5.6.40**, last version in Alpine Linux 3.4.
 - must be built by hand [from here](https://www.php.net/releases/#5.6.40) after adding **build-requirements**.
 - build options [from php5 docker files](https://hub.docker.com/r/nyanpass/php5.5).
 - `apk add --no-cache --virtual .php-build-deps $BUILD_DEPS \`
 - ` libfcgi-dev libfcgi0ldbl \`
 - `	curl-dev libedit-dev libxml2-dev openssl-dev sqlite-dev \`
 - `	libfreetype6-dev libjpeg62-turbo-dev libmcrypt-dev libpng12-dev`
 - `export PHP_INI_DIR='/usr/local/etc/php5'`
 - `./configure --with-config-file-path="$PHP_INI_DIR" --with-config-file-scan-dir="$PHP_INI_DIR/conf.d" \`
 - `	--disable-cgi --enable-fpm --with-fpm-user=www-data --with-fpm-group=www-data \`
 - ` --enable-ftp --enable-mbstring --enable-mysqlnd --enable-sqlite \`
 - `	--with-curl --with-libedit --with-openssl --with-zlib`
 - or build options [taken from a Ubuntu 16.04 install](https://www.howtoforge.com/tutorial/how-to-install-php-5-6-on-ubuntu-16-04/).
 - `./configure --prefix=/opt/php-5.6.30 --with-pdo-pgsql --with-zlib-dir --with-freetype-dir --enable-mbstring \`
 - ` --with-libxml-dir=/usr --enable-soap --enable-calendar --with-curl --with-mcrypt --with-zlib --with-gd \`
 - ` --with-pgsql --disable-rpath --enable-inline-optimization --with-bz2 --with-zlib \`
 - ` --enable-sockets --enable-sysvsem --enable-sysvshm --enable-pcntl --enable-mbregex --enable-exif \`
 - ` --enable-bcmath --with-mhash --enable-zip --with-pcre-regex \`
 - ` --with-mysql --with-pdo-mysql --with-mysqli \`
 - ` --with-jpeg-dir=/usr --with-png-dir=/usr --enable-gd-native-ttf --with-openssl \`
 - ` --with-fpm-user=www-data --with-fpm-group=www-data --with-libdir=/lib/x86_64-linux-gnu \`
 - ` --enable-ftp --with-imap --with-imap-ssl --with-gettext --with-xmlrpc --with-xsl --with-kerberos --enable-fpm`
 - or make up build configuration [from older Alpine Wiki](https://wiki.alpinelinux.org/wiki/Nginx_with_PHP#Configuration_of_PHP5).

## build-requirements
 - (taken from **_php5.5-fpm-alpine-docker_**)
 - `export BUILD_DEPS='autoconf file g++ gcc libc-dev make pkgconf re2c'`
 - `apk add --no-cache --virtual .build-deps $BUILD_DEPS`
 - ``
 
