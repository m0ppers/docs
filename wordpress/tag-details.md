<!-- THIS FILE IS GENERATED VIA '.template-helpers/generate-tag-details.pl' -->

# Tags of `wordpress`

-	[`wordpress:4.5.3-apache`](#wordpress453-apache)
-	[`wordpress:4.5-apache`](#wordpress45-apache)
-	[`wordpress:4-apache`](#wordpress4-apache)
-	[`wordpress:apache`](#wordpressapache)
-	[`wordpress:4.5.3`](#wordpress453)
-	[`wordpress:4.5`](#wordpress45)
-	[`wordpress:4`](#wordpress4)
-	[`wordpress:latest`](#wordpresslatest)
-	[`wordpress:4.5.3-fpm`](#wordpress453-fpm)
-	[`wordpress:4.5-fpm`](#wordpress45-fpm)
-	[`wordpress:4-fpm`](#wordpress4-fpm)
-	[`wordpress:fpm`](#wordpressfpm)

## `wordpress:4.5.3-apache`

```console
$ docker pull wordpress@sha256:7bb9549fb6d80c230bec2da6bd181be8f30e5199687e53e5ad5744a3144eae1b
```

-	Platforms:
	-	linux; amd64

### `wordpress:4.5.3-apache` - linux; amd64

-	Docker Version: 1.10.3
-	Manifest MIME: `application/vnd.docker.distribution.manifest.v2+json`
-	Total Size: **177.2 MB (177161413 bytes)**  
	(compressed transfer size, not on-disk size)
-	Image ID: `sha256:e3f325718719293c09079bbbb1a2b9bf9053172bc594b5f3acf8d370efe8afae`
-	Entrypoint: `["\/entrypoint.sh"]`
-	Default Command: `["apache2-foreground"]`

```dockerfile
# Thu, 09 Jun 2016 21:28:42 GMT
ADD file:76679eeb94129df23c99013487d6b6bd779d2107bf07d194a524fdbb6a961530 in /
# Thu, 09 Jun 2016 21:28:43 GMT
CMD ["/bin/bash"]
# Fri, 10 Jun 2016 02:34:30 GMT
ENV PHPIZE_DEPS=autoconf 		file 		g++ 		gcc 		libc-dev 		make 		pkg-config 		re2c
# Fri, 10 Jun 2016 02:35:57 GMT
RUN apt-get update && apt-get install -y 		$PHPIZE_DEPS 		ca-certificates 		curl 		libedit2 		libsqlite3-0 		libxml2 	--no-install-recommends && rm -r /var/lib/apt/lists/*
# Fri, 10 Jun 2016 02:35:58 GMT
ENV PHP_INI_DIR=/usr/local/etc/php
# Fri, 10 Jun 2016 02:35:59 GMT
RUN mkdir -p $PHP_INI_DIR/conf.d
# Fri, 10 Jun 2016 02:43:42 GMT
RUN apt-get update && apt-get install -y apache2-bin apache2.2-common --no-install-recommends && rm -rf /var/lib/apt/lists/*
# Thu, 07 Jul 2016 19:23:45 GMT
ENV APACHE_CONFDIR=/etc/apache2
# Thu, 07 Jul 2016 19:23:46 GMT
ENV APACHE_ENVVARS=/etc/apache2/envvars
# Thu, 07 Jul 2016 19:23:48 GMT
RUN set -ex 	&& . "$APACHE_ENVVARS" 	&& for dir in 		"$APACHE_LOCK_DIR" 		"$APACHE_RUN_DIR" 		"$APACHE_LOG_DIR" 		/var/www/html 	; do 		rm -rvf "$dir" 		&& mkdir -p "$dir" 		&& chown -R "$APACHE_RUN_USER:$APACHE_RUN_GROUP" "$dir"; 	done
# Thu, 07 Jul 2016 19:23:49 GMT
RUN a2dismod mpm_event && a2enmod mpm_prefork
# Thu, 07 Jul 2016 19:23:51 GMT
RUN set -ex 	&& . "$APACHE_ENVVARS" 	&& ln -sfT /dev/stderr "$APACHE_LOG_DIR/error.log" 	&& ln -sfT /dev/stdout "$APACHE_LOG_DIR/access.log" 	&& ln -sfT /dev/stdout "$APACHE_LOG_DIR/other_vhosts_access.log"
# Fri, 08 Jul 2016 22:14:00 GMT
RUN { 		echo '<FilesMatch \.php$>'; 		echo '\tSetHandler application/x-httpd-php'; 		echo '</FilesMatch>'; 		echo; 		echo 'DirectoryIndex disabled'; 		echo 'DirectoryIndex index.php index.html'; 		echo; 		echo '<Directory /var/www/>'; 		echo '\tOptions -Indexes'; 		echo '\tAllowOverride All'; 		echo '</Directory>'; 	} | tee "$APACHE_CONFDIR/conf-available/docker-php.conf" 	&& a2enconf docker-php
# Fri, 08 Jul 2016 22:14:01 GMT
ENV PHP_EXTRA_BUILD_DEPS=apache2-dev
# Fri, 08 Jul 2016 22:14:01 GMT
ENV PHP_EXTRA_CONFIGURE_ARGS=--with-apxs2
# Fri, 08 Jul 2016 22:19:29 GMT
ENV GPG_KEYS=0BD78B5F97500D450838F95DFE857D9A90D90EC1 6E4F6AB321FDC07F2C332E3AC2BF0BC433CFC8B3
# Fri, 08 Jul 2016 22:19:30 GMT
ENV PHP_VERSION=5.6.23
# Fri, 08 Jul 2016 22:19:30 GMT
ENV PHP_FILENAME=php-5.6.23.tar.xz
# Fri, 08 Jul 2016 22:19:30 GMT
ENV PHP_SHA256=39141e9a617af172aedbbacee7a63eb15502850f7cea20d759a9cffa7cfb0a1a
# Fri, 08 Jul 2016 22:24:42 GMT
RUN set -xe 	&& buildDeps=" 		$PHP_EXTRA_BUILD_DEPS 		libcurl4-openssl-dev 		libedit-dev 		libsqlite3-dev 		libssl-dev 		libxml2-dev 		xz-utils 	" 	&& apt-get update && apt-get install -y $buildDeps --no-install-recommends && rm -rf /var/lib/apt/lists/* 	&& curl -fSL "http://php.net/get/$PHP_FILENAME/from/this/mirror" -o "$PHP_FILENAME" 	&& echo "$PHP_SHA256 *$PHP_FILENAME" | sha256sum -c - 	&& curl -fSL "http://php.net/get/$PHP_FILENAME.asc/from/this/mirror" -o "$PHP_FILENAME.asc" 	&& export GNUPGHOME="$(mktemp -d)" 	&& for key in $GPG_KEYS; do 		gpg --keyserver ha.pool.sks-keyservers.net --recv-keys "$key"; 	done 	&& gpg --batch --verify "$PHP_FILENAME.asc" "$PHP_FILENAME" 	&& rm -r "$GNUPGHOME" "$PHP_FILENAME.asc" 	&& mkdir -p /usr/src/php 	&& tar -xf "$PHP_FILENAME" -C /usr/src/php --strip-components=1 	&& rm "$PHP_FILENAME" 	&& cd /usr/src/php 	&& ./configure 		--with-config-file-path="$PHP_INI_DIR" 		--with-config-file-scan-dir="$PHP_INI_DIR/conf.d" 		$PHP_EXTRA_CONFIGURE_ARGS 		--disable-cgi 		--enable-mysqlnd 		--enable-mbstring 		--with-curl 		--with-libedit 		--with-openssl 		--with-zlib 	&& make -j"$(nproc)" 	&& make install 	&& { find /usr/local/bin /usr/local/sbin -type f -executable -exec strip --strip-all '{}' + || true; } 	&& make clean 	&& apt-get purge -y --auto-remove -o APT::AutoRemove::RecommendsImportant=false -o APT::AutoRemove::SuggestsImportant=false $buildDeps
# Fri, 08 Jul 2016 22:24:43 GMT
COPY multi:a8819301efc7ce6569bcf183723931153c5b968224bce96498ddbabe72ce7eaa in /usr/local/bin/
# Fri, 08 Jul 2016 22:24:44 GMT
COPY file:3014772111b66da3129ca8caeafdd1dcfa9a3bf518f015ae9acc3c7b9b1b44c9 in /usr/local/bin/
# Fri, 08 Jul 2016 22:24:44 GMT
WORKDIR /var/www/html
# Fri, 08 Jul 2016 22:24:45 GMT
EXPOSE 80/tcp
# Fri, 08 Jul 2016 22:24:45 GMT
CMD ["apache2-foreground"]
# Fri, 08 Jul 2016 23:10:56 GMT
RUN a2enmod rewrite expires
# Fri, 08 Jul 2016 23:12:37 GMT
RUN apt-get update && apt-get install -y libpng12-dev libjpeg-dev && rm -rf /var/lib/apt/lists/* 	&& docker-php-ext-configure gd --with-png-dir=/usr --with-jpeg-dir=/usr 	&& docker-php-ext-install gd mysqli opcache
# Fri, 08 Jul 2016 23:12:39 GMT
RUN { 		echo 'opcache.memory_consumption=128'; 		echo 'opcache.interned_strings_buffer=8'; 		echo 'opcache.max_accelerated_files=4000'; 		echo 'opcache.revalidate_freq=60'; 		echo 'opcache.fast_shutdown=1'; 		echo 'opcache.enable_cli=1'; 	} > /usr/local/etc/php/conf.d/opcache-recommended.ini
# Fri, 08 Jul 2016 23:12:40 GMT
VOLUME [/var/www/html]
# Fri, 08 Jul 2016 23:12:40 GMT
ENV WORDPRESS_VERSION=4.5.3
# Fri, 08 Jul 2016 23:12:41 GMT
ENV WORDPRESS_SHA1=835b68748dae5a9d31c059313cd0150f03a49269
# Fri, 08 Jul 2016 23:12:44 GMT
RUN curl -o wordpress.tar.gz -SL https://wordpress.org/wordpress-${WORDPRESS_VERSION}.tar.gz 	&& echo "$WORDPRESS_SHA1 *wordpress.tar.gz" | sha1sum -c - 	&& tar -xzf wordpress.tar.gz -C /usr/src/ 	&& rm wordpress.tar.gz 	&& chown -R www-data:www-data /usr/src/wordpress
# Fri, 08 Jul 2016 23:12:45 GMT
COPY file:28ccaf78edbf6e7811305e5409bbaa660f9992cad70c071c67cd040bfcb9057e in /entrypoint.sh
# Fri, 08 Jul 2016 23:12:46 GMT
ENTRYPOINT &{["/entrypoint.sh"]}
# Fri, 08 Jul 2016 23:12:46 GMT
CMD ["apache2-foreground"]
```

-	Layers:
	-	`sha256:5c90d4a2d1a8dfffd05ff2dd659923f0ca2d843b5e45d030e17abbcd06a11b5b`  
		Last Modified: Thu, 09 Jun 2016 21:30:47 GMT  
		Size: 51.4 MB (51352535 bytes)
	-	`sha256:357b76a4983822c380125e911928d20bf853d3a4ca869181c757d855408a9c90`  
		Last Modified: Tue, 14 Jun 2016 21:44:40 GMT  
		Size: 77.3 MB (77343405 bytes)
	-	`sha256:0e87614c69f0ba521d6a89ea9b82a5712ff209dfa89e14b1fef8be2056d5680d`  
		Last Modified: Tue, 14 Jun 2016 21:44:12 GMT  
		Size: 180.0 B
	-	`sha256:a3a94d3df9be4137d53c70f13e1bf0e40d300e41c9773a3b5b26d68d75f31797`  
		Last Modified: Tue, 14 Jun 2016 21:44:14 GMT  
		Size: 2.9 MB (2874106 bytes)
	-	`sha256:ac140e12d947b453d23e00fd4099540ef06a9cfec9ac8d0183641b8d301e0f4f`  
		Last Modified: Thu, 07 Jul 2016 19:41:39 GMT  
		Size: 277.0 B
	-	`sha256:e08ee42cd95f62a54fcd329593aa277c5a62fb2fb6bfc8a3103556b23f7a9cd8`  
		Last Modified: Thu, 07 Jul 2016 19:41:39 GMT  
		Size: 430.0 B
	-	`sha256:d4cac1e00ff618b3862877517bb6b85ad52560be5ea79d076c2f670ed7471f34`  
		Last Modified: Thu, 07 Jul 2016 19:41:36 GMT  
		Size: 224.0 B
	-	`sha256:f2749ebafcf639d790352065364892fb26e952ee2c90f41a94b9af3e2a06b6fc`  
		Last Modified: Fri, 08 Jul 2016 22:31:48 GMT  
		Size: 474.0 B
	-	`sha256:b83b18211b0e6523d464cf2237852f82bbc2f6477a2b8a6e27b88a9cdd7c884c`  
		Last Modified: Fri, 08 Jul 2016 22:36:55 GMT  
		Size: 33.5 MB (33498380 bytes)
	-	`sha256:eff2616aae67a23b0fa5482b3a3771e05a0875eae9d3a02c20ced93b155098ab`  
		Last Modified: Fri, 08 Jul 2016 22:36:40 GMT  
		Size: 1.8 KB (1756 bytes)
	-	`sha256:76333cc4945328a2d994e3b590629e2fd2bfa8f9e82f395816da523fc11ac31f`  
		Last Modified: Fri, 08 Jul 2016 22:36:37 GMT  
		Size: 584.0 B
	-	`sha256:81895367a65f4cdf8f2454d668080dd83c43dadc2f69f6a01ebfe0426be7e13f`  
		Last Modified: Fri, 08 Jul 2016 23:12:54 GMT  
		Size: 326.0 B
	-	`sha256:dceeb874afb26f6b1cd50f1b5b5afdcce69f3b09a61ef2bccbf80a5c7f198d76`  
		Last Modified: Fri, 08 Jul 2016 23:12:56 GMT  
		Size: 4.5 MB (4473999 bytes)
	-	`sha256:b7b129bc1e78347a1544b8c03108d3c67e7e679fe76c85ae852915b6a15059a6`  
		Last Modified: Fri, 08 Jul 2016 23:12:54 GMT  
		Size: 333.0 B
	-	`sha256:65a991c10dcb57bdd0f3a93991780e0309d70fe2a876472e20648ca31372903d`  
		Last Modified: Fri, 08 Jul 2016 23:12:56 GMT  
		Size: 7.6 MB (7611911 bytes)
	-	`sha256:adff62f88fa960539b49ecb3ac3b1a29a92ff6421ded81455f5b545a1c772b21`  
		Last Modified: Fri, 08 Jul 2016 23:12:55 GMT  
		Size: 2.5 KB (2493 bytes)

## `wordpress:4.5-apache`

```console
$ docker pull wordpress@sha256:7bb9549fb6d80c230bec2da6bd181be8f30e5199687e53e5ad5744a3144eae1b
```

-	Platforms:
	-	linux; amd64

### `wordpress:4.5-apache` - linux; amd64

-	Docker Version: 1.10.3
-	Manifest MIME: `application/vnd.docker.distribution.manifest.v2+json`
-	Total Size: **177.2 MB (177161413 bytes)**  
	(compressed transfer size, not on-disk size)
-	Image ID: `sha256:e3f325718719293c09079bbbb1a2b9bf9053172bc594b5f3acf8d370efe8afae`
-	Entrypoint: `["\/entrypoint.sh"]`
-	Default Command: `["apache2-foreground"]`

```dockerfile
# Thu, 09 Jun 2016 21:28:42 GMT
ADD file:76679eeb94129df23c99013487d6b6bd779d2107bf07d194a524fdbb6a961530 in /
# Thu, 09 Jun 2016 21:28:43 GMT
CMD ["/bin/bash"]
# Fri, 10 Jun 2016 02:34:30 GMT
ENV PHPIZE_DEPS=autoconf 		file 		g++ 		gcc 		libc-dev 		make 		pkg-config 		re2c
# Fri, 10 Jun 2016 02:35:57 GMT
RUN apt-get update && apt-get install -y 		$PHPIZE_DEPS 		ca-certificates 		curl 		libedit2 		libsqlite3-0 		libxml2 	--no-install-recommends && rm -r /var/lib/apt/lists/*
# Fri, 10 Jun 2016 02:35:58 GMT
ENV PHP_INI_DIR=/usr/local/etc/php
# Fri, 10 Jun 2016 02:35:59 GMT
RUN mkdir -p $PHP_INI_DIR/conf.d
# Fri, 10 Jun 2016 02:43:42 GMT
RUN apt-get update && apt-get install -y apache2-bin apache2.2-common --no-install-recommends && rm -rf /var/lib/apt/lists/*
# Thu, 07 Jul 2016 19:23:45 GMT
ENV APACHE_CONFDIR=/etc/apache2
# Thu, 07 Jul 2016 19:23:46 GMT
ENV APACHE_ENVVARS=/etc/apache2/envvars
# Thu, 07 Jul 2016 19:23:48 GMT
RUN set -ex 	&& . "$APACHE_ENVVARS" 	&& for dir in 		"$APACHE_LOCK_DIR" 		"$APACHE_RUN_DIR" 		"$APACHE_LOG_DIR" 		/var/www/html 	; do 		rm -rvf "$dir" 		&& mkdir -p "$dir" 		&& chown -R "$APACHE_RUN_USER:$APACHE_RUN_GROUP" "$dir"; 	done
# Thu, 07 Jul 2016 19:23:49 GMT
RUN a2dismod mpm_event && a2enmod mpm_prefork
# Thu, 07 Jul 2016 19:23:51 GMT
RUN set -ex 	&& . "$APACHE_ENVVARS" 	&& ln -sfT /dev/stderr "$APACHE_LOG_DIR/error.log" 	&& ln -sfT /dev/stdout "$APACHE_LOG_DIR/access.log" 	&& ln -sfT /dev/stdout "$APACHE_LOG_DIR/other_vhosts_access.log"
# Fri, 08 Jul 2016 22:14:00 GMT
RUN { 		echo '<FilesMatch \.php$>'; 		echo '\tSetHandler application/x-httpd-php'; 		echo '</FilesMatch>'; 		echo; 		echo 'DirectoryIndex disabled'; 		echo 'DirectoryIndex index.php index.html'; 		echo; 		echo '<Directory /var/www/>'; 		echo '\tOptions -Indexes'; 		echo '\tAllowOverride All'; 		echo '</Directory>'; 	} | tee "$APACHE_CONFDIR/conf-available/docker-php.conf" 	&& a2enconf docker-php
# Fri, 08 Jul 2016 22:14:01 GMT
ENV PHP_EXTRA_BUILD_DEPS=apache2-dev
# Fri, 08 Jul 2016 22:14:01 GMT
ENV PHP_EXTRA_CONFIGURE_ARGS=--with-apxs2
# Fri, 08 Jul 2016 22:19:29 GMT
ENV GPG_KEYS=0BD78B5F97500D450838F95DFE857D9A90D90EC1 6E4F6AB321FDC07F2C332E3AC2BF0BC433CFC8B3
# Fri, 08 Jul 2016 22:19:30 GMT
ENV PHP_VERSION=5.6.23
# Fri, 08 Jul 2016 22:19:30 GMT
ENV PHP_FILENAME=php-5.6.23.tar.xz
# Fri, 08 Jul 2016 22:19:30 GMT
ENV PHP_SHA256=39141e9a617af172aedbbacee7a63eb15502850f7cea20d759a9cffa7cfb0a1a
# Fri, 08 Jul 2016 22:24:42 GMT
RUN set -xe 	&& buildDeps=" 		$PHP_EXTRA_BUILD_DEPS 		libcurl4-openssl-dev 		libedit-dev 		libsqlite3-dev 		libssl-dev 		libxml2-dev 		xz-utils 	" 	&& apt-get update && apt-get install -y $buildDeps --no-install-recommends && rm -rf /var/lib/apt/lists/* 	&& curl -fSL "http://php.net/get/$PHP_FILENAME/from/this/mirror" -o "$PHP_FILENAME" 	&& echo "$PHP_SHA256 *$PHP_FILENAME" | sha256sum -c - 	&& curl -fSL "http://php.net/get/$PHP_FILENAME.asc/from/this/mirror" -o "$PHP_FILENAME.asc" 	&& export GNUPGHOME="$(mktemp -d)" 	&& for key in $GPG_KEYS; do 		gpg --keyserver ha.pool.sks-keyservers.net --recv-keys "$key"; 	done 	&& gpg --batch --verify "$PHP_FILENAME.asc" "$PHP_FILENAME" 	&& rm -r "$GNUPGHOME" "$PHP_FILENAME.asc" 	&& mkdir -p /usr/src/php 	&& tar -xf "$PHP_FILENAME" -C /usr/src/php --strip-components=1 	&& rm "$PHP_FILENAME" 	&& cd /usr/src/php 	&& ./configure 		--with-config-file-path="$PHP_INI_DIR" 		--with-config-file-scan-dir="$PHP_INI_DIR/conf.d" 		$PHP_EXTRA_CONFIGURE_ARGS 		--disable-cgi 		--enable-mysqlnd 		--enable-mbstring 		--with-curl 		--with-libedit 		--with-openssl 		--with-zlib 	&& make -j"$(nproc)" 	&& make install 	&& { find /usr/local/bin /usr/local/sbin -type f -executable -exec strip --strip-all '{}' + || true; } 	&& make clean 	&& apt-get purge -y --auto-remove -o APT::AutoRemove::RecommendsImportant=false -o APT::AutoRemove::SuggestsImportant=false $buildDeps
# Fri, 08 Jul 2016 22:24:43 GMT
COPY multi:a8819301efc7ce6569bcf183723931153c5b968224bce96498ddbabe72ce7eaa in /usr/local/bin/
# Fri, 08 Jul 2016 22:24:44 GMT
COPY file:3014772111b66da3129ca8caeafdd1dcfa9a3bf518f015ae9acc3c7b9b1b44c9 in /usr/local/bin/
# Fri, 08 Jul 2016 22:24:44 GMT
WORKDIR /var/www/html
# Fri, 08 Jul 2016 22:24:45 GMT
EXPOSE 80/tcp
# Fri, 08 Jul 2016 22:24:45 GMT
CMD ["apache2-foreground"]
# Fri, 08 Jul 2016 23:10:56 GMT
RUN a2enmod rewrite expires
# Fri, 08 Jul 2016 23:12:37 GMT
RUN apt-get update && apt-get install -y libpng12-dev libjpeg-dev && rm -rf /var/lib/apt/lists/* 	&& docker-php-ext-configure gd --with-png-dir=/usr --with-jpeg-dir=/usr 	&& docker-php-ext-install gd mysqli opcache
# Fri, 08 Jul 2016 23:12:39 GMT
RUN { 		echo 'opcache.memory_consumption=128'; 		echo 'opcache.interned_strings_buffer=8'; 		echo 'opcache.max_accelerated_files=4000'; 		echo 'opcache.revalidate_freq=60'; 		echo 'opcache.fast_shutdown=1'; 		echo 'opcache.enable_cli=1'; 	} > /usr/local/etc/php/conf.d/opcache-recommended.ini
# Fri, 08 Jul 2016 23:12:40 GMT
VOLUME [/var/www/html]
# Fri, 08 Jul 2016 23:12:40 GMT
ENV WORDPRESS_VERSION=4.5.3
# Fri, 08 Jul 2016 23:12:41 GMT
ENV WORDPRESS_SHA1=835b68748dae5a9d31c059313cd0150f03a49269
# Fri, 08 Jul 2016 23:12:44 GMT
RUN curl -o wordpress.tar.gz -SL https://wordpress.org/wordpress-${WORDPRESS_VERSION}.tar.gz 	&& echo "$WORDPRESS_SHA1 *wordpress.tar.gz" | sha1sum -c - 	&& tar -xzf wordpress.tar.gz -C /usr/src/ 	&& rm wordpress.tar.gz 	&& chown -R www-data:www-data /usr/src/wordpress
# Fri, 08 Jul 2016 23:12:45 GMT
COPY file:28ccaf78edbf6e7811305e5409bbaa660f9992cad70c071c67cd040bfcb9057e in /entrypoint.sh
# Fri, 08 Jul 2016 23:12:46 GMT
ENTRYPOINT &{["/entrypoint.sh"]}
# Fri, 08 Jul 2016 23:12:46 GMT
CMD ["apache2-foreground"]
```

-	Layers:
	-	`sha256:5c90d4a2d1a8dfffd05ff2dd659923f0ca2d843b5e45d030e17abbcd06a11b5b`  
		Last Modified: Thu, 09 Jun 2016 21:30:47 GMT  
		Size: 51.4 MB (51352535 bytes)
	-	`sha256:357b76a4983822c380125e911928d20bf853d3a4ca869181c757d855408a9c90`  
		Last Modified: Tue, 14 Jun 2016 21:44:40 GMT  
		Size: 77.3 MB (77343405 bytes)
	-	`sha256:0e87614c69f0ba521d6a89ea9b82a5712ff209dfa89e14b1fef8be2056d5680d`  
		Last Modified: Tue, 14 Jun 2016 21:44:12 GMT  
		Size: 180.0 B
	-	`sha256:a3a94d3df9be4137d53c70f13e1bf0e40d300e41c9773a3b5b26d68d75f31797`  
		Last Modified: Tue, 14 Jun 2016 21:44:14 GMT  
		Size: 2.9 MB (2874106 bytes)
	-	`sha256:ac140e12d947b453d23e00fd4099540ef06a9cfec9ac8d0183641b8d301e0f4f`  
		Last Modified: Thu, 07 Jul 2016 19:41:39 GMT  
		Size: 277.0 B
	-	`sha256:e08ee42cd95f62a54fcd329593aa277c5a62fb2fb6bfc8a3103556b23f7a9cd8`  
		Last Modified: Thu, 07 Jul 2016 19:41:39 GMT  
		Size: 430.0 B
	-	`sha256:d4cac1e00ff618b3862877517bb6b85ad52560be5ea79d076c2f670ed7471f34`  
		Last Modified: Thu, 07 Jul 2016 19:41:36 GMT  
		Size: 224.0 B
	-	`sha256:f2749ebafcf639d790352065364892fb26e952ee2c90f41a94b9af3e2a06b6fc`  
		Last Modified: Fri, 08 Jul 2016 22:31:48 GMT  
		Size: 474.0 B
	-	`sha256:b83b18211b0e6523d464cf2237852f82bbc2f6477a2b8a6e27b88a9cdd7c884c`  
		Last Modified: Fri, 08 Jul 2016 22:36:55 GMT  
		Size: 33.5 MB (33498380 bytes)
	-	`sha256:eff2616aae67a23b0fa5482b3a3771e05a0875eae9d3a02c20ced93b155098ab`  
		Last Modified: Fri, 08 Jul 2016 22:36:40 GMT  
		Size: 1.8 KB (1756 bytes)
	-	`sha256:76333cc4945328a2d994e3b590629e2fd2bfa8f9e82f395816da523fc11ac31f`  
		Last Modified: Fri, 08 Jul 2016 22:36:37 GMT  
		Size: 584.0 B
	-	`sha256:81895367a65f4cdf8f2454d668080dd83c43dadc2f69f6a01ebfe0426be7e13f`  
		Last Modified: Fri, 08 Jul 2016 23:12:54 GMT  
		Size: 326.0 B
	-	`sha256:dceeb874afb26f6b1cd50f1b5b5afdcce69f3b09a61ef2bccbf80a5c7f198d76`  
		Last Modified: Fri, 08 Jul 2016 23:12:56 GMT  
		Size: 4.5 MB (4473999 bytes)
	-	`sha256:b7b129bc1e78347a1544b8c03108d3c67e7e679fe76c85ae852915b6a15059a6`  
		Last Modified: Fri, 08 Jul 2016 23:12:54 GMT  
		Size: 333.0 B
	-	`sha256:65a991c10dcb57bdd0f3a93991780e0309d70fe2a876472e20648ca31372903d`  
		Last Modified: Fri, 08 Jul 2016 23:12:56 GMT  
		Size: 7.6 MB (7611911 bytes)
	-	`sha256:adff62f88fa960539b49ecb3ac3b1a29a92ff6421ded81455f5b545a1c772b21`  
		Last Modified: Fri, 08 Jul 2016 23:12:55 GMT  
		Size: 2.5 KB (2493 bytes)

## `wordpress:4-apache`

```console
$ docker pull wordpress@sha256:7bb9549fb6d80c230bec2da6bd181be8f30e5199687e53e5ad5744a3144eae1b
```

-	Platforms:
	-	linux; amd64

### `wordpress:4-apache` - linux; amd64

-	Docker Version: 1.10.3
-	Manifest MIME: `application/vnd.docker.distribution.manifest.v2+json`
-	Total Size: **177.2 MB (177161413 bytes)**  
	(compressed transfer size, not on-disk size)
-	Image ID: `sha256:e3f325718719293c09079bbbb1a2b9bf9053172bc594b5f3acf8d370efe8afae`
-	Entrypoint: `["\/entrypoint.sh"]`
-	Default Command: `["apache2-foreground"]`

```dockerfile
# Thu, 09 Jun 2016 21:28:42 GMT
ADD file:76679eeb94129df23c99013487d6b6bd779d2107bf07d194a524fdbb6a961530 in /
# Thu, 09 Jun 2016 21:28:43 GMT
CMD ["/bin/bash"]
# Fri, 10 Jun 2016 02:34:30 GMT
ENV PHPIZE_DEPS=autoconf 		file 		g++ 		gcc 		libc-dev 		make 		pkg-config 		re2c
# Fri, 10 Jun 2016 02:35:57 GMT
RUN apt-get update && apt-get install -y 		$PHPIZE_DEPS 		ca-certificates 		curl 		libedit2 		libsqlite3-0 		libxml2 	--no-install-recommends && rm -r /var/lib/apt/lists/*
# Fri, 10 Jun 2016 02:35:58 GMT
ENV PHP_INI_DIR=/usr/local/etc/php
# Fri, 10 Jun 2016 02:35:59 GMT
RUN mkdir -p $PHP_INI_DIR/conf.d
# Fri, 10 Jun 2016 02:43:42 GMT
RUN apt-get update && apt-get install -y apache2-bin apache2.2-common --no-install-recommends && rm -rf /var/lib/apt/lists/*
# Thu, 07 Jul 2016 19:23:45 GMT
ENV APACHE_CONFDIR=/etc/apache2
# Thu, 07 Jul 2016 19:23:46 GMT
ENV APACHE_ENVVARS=/etc/apache2/envvars
# Thu, 07 Jul 2016 19:23:48 GMT
RUN set -ex 	&& . "$APACHE_ENVVARS" 	&& for dir in 		"$APACHE_LOCK_DIR" 		"$APACHE_RUN_DIR" 		"$APACHE_LOG_DIR" 		/var/www/html 	; do 		rm -rvf "$dir" 		&& mkdir -p "$dir" 		&& chown -R "$APACHE_RUN_USER:$APACHE_RUN_GROUP" "$dir"; 	done
# Thu, 07 Jul 2016 19:23:49 GMT
RUN a2dismod mpm_event && a2enmod mpm_prefork
# Thu, 07 Jul 2016 19:23:51 GMT
RUN set -ex 	&& . "$APACHE_ENVVARS" 	&& ln -sfT /dev/stderr "$APACHE_LOG_DIR/error.log" 	&& ln -sfT /dev/stdout "$APACHE_LOG_DIR/access.log" 	&& ln -sfT /dev/stdout "$APACHE_LOG_DIR/other_vhosts_access.log"
# Fri, 08 Jul 2016 22:14:00 GMT
RUN { 		echo '<FilesMatch \.php$>'; 		echo '\tSetHandler application/x-httpd-php'; 		echo '</FilesMatch>'; 		echo; 		echo 'DirectoryIndex disabled'; 		echo 'DirectoryIndex index.php index.html'; 		echo; 		echo '<Directory /var/www/>'; 		echo '\tOptions -Indexes'; 		echo '\tAllowOverride All'; 		echo '</Directory>'; 	} | tee "$APACHE_CONFDIR/conf-available/docker-php.conf" 	&& a2enconf docker-php
# Fri, 08 Jul 2016 22:14:01 GMT
ENV PHP_EXTRA_BUILD_DEPS=apache2-dev
# Fri, 08 Jul 2016 22:14:01 GMT
ENV PHP_EXTRA_CONFIGURE_ARGS=--with-apxs2
# Fri, 08 Jul 2016 22:19:29 GMT
ENV GPG_KEYS=0BD78B5F97500D450838F95DFE857D9A90D90EC1 6E4F6AB321FDC07F2C332E3AC2BF0BC433CFC8B3
# Fri, 08 Jul 2016 22:19:30 GMT
ENV PHP_VERSION=5.6.23
# Fri, 08 Jul 2016 22:19:30 GMT
ENV PHP_FILENAME=php-5.6.23.tar.xz
# Fri, 08 Jul 2016 22:19:30 GMT
ENV PHP_SHA256=39141e9a617af172aedbbacee7a63eb15502850f7cea20d759a9cffa7cfb0a1a
# Fri, 08 Jul 2016 22:24:42 GMT
RUN set -xe 	&& buildDeps=" 		$PHP_EXTRA_BUILD_DEPS 		libcurl4-openssl-dev 		libedit-dev 		libsqlite3-dev 		libssl-dev 		libxml2-dev 		xz-utils 	" 	&& apt-get update && apt-get install -y $buildDeps --no-install-recommends && rm -rf /var/lib/apt/lists/* 	&& curl -fSL "http://php.net/get/$PHP_FILENAME/from/this/mirror" -o "$PHP_FILENAME" 	&& echo "$PHP_SHA256 *$PHP_FILENAME" | sha256sum -c - 	&& curl -fSL "http://php.net/get/$PHP_FILENAME.asc/from/this/mirror" -o "$PHP_FILENAME.asc" 	&& export GNUPGHOME="$(mktemp -d)" 	&& for key in $GPG_KEYS; do 		gpg --keyserver ha.pool.sks-keyservers.net --recv-keys "$key"; 	done 	&& gpg --batch --verify "$PHP_FILENAME.asc" "$PHP_FILENAME" 	&& rm -r "$GNUPGHOME" "$PHP_FILENAME.asc" 	&& mkdir -p /usr/src/php 	&& tar -xf "$PHP_FILENAME" -C /usr/src/php --strip-components=1 	&& rm "$PHP_FILENAME" 	&& cd /usr/src/php 	&& ./configure 		--with-config-file-path="$PHP_INI_DIR" 		--with-config-file-scan-dir="$PHP_INI_DIR/conf.d" 		$PHP_EXTRA_CONFIGURE_ARGS 		--disable-cgi 		--enable-mysqlnd 		--enable-mbstring 		--with-curl 		--with-libedit 		--with-openssl 		--with-zlib 	&& make -j"$(nproc)" 	&& make install 	&& { find /usr/local/bin /usr/local/sbin -type f -executable -exec strip --strip-all '{}' + || true; } 	&& make clean 	&& apt-get purge -y --auto-remove -o APT::AutoRemove::RecommendsImportant=false -o APT::AutoRemove::SuggestsImportant=false $buildDeps
# Fri, 08 Jul 2016 22:24:43 GMT
COPY multi:a8819301efc7ce6569bcf183723931153c5b968224bce96498ddbabe72ce7eaa in /usr/local/bin/
# Fri, 08 Jul 2016 22:24:44 GMT
COPY file:3014772111b66da3129ca8caeafdd1dcfa9a3bf518f015ae9acc3c7b9b1b44c9 in /usr/local/bin/
# Fri, 08 Jul 2016 22:24:44 GMT
WORKDIR /var/www/html
# Fri, 08 Jul 2016 22:24:45 GMT
EXPOSE 80/tcp
# Fri, 08 Jul 2016 22:24:45 GMT
CMD ["apache2-foreground"]
# Fri, 08 Jul 2016 23:10:56 GMT
RUN a2enmod rewrite expires
# Fri, 08 Jul 2016 23:12:37 GMT
RUN apt-get update && apt-get install -y libpng12-dev libjpeg-dev && rm -rf /var/lib/apt/lists/* 	&& docker-php-ext-configure gd --with-png-dir=/usr --with-jpeg-dir=/usr 	&& docker-php-ext-install gd mysqli opcache
# Fri, 08 Jul 2016 23:12:39 GMT
RUN { 		echo 'opcache.memory_consumption=128'; 		echo 'opcache.interned_strings_buffer=8'; 		echo 'opcache.max_accelerated_files=4000'; 		echo 'opcache.revalidate_freq=60'; 		echo 'opcache.fast_shutdown=1'; 		echo 'opcache.enable_cli=1'; 	} > /usr/local/etc/php/conf.d/opcache-recommended.ini
# Fri, 08 Jul 2016 23:12:40 GMT
VOLUME [/var/www/html]
# Fri, 08 Jul 2016 23:12:40 GMT
ENV WORDPRESS_VERSION=4.5.3
# Fri, 08 Jul 2016 23:12:41 GMT
ENV WORDPRESS_SHA1=835b68748dae5a9d31c059313cd0150f03a49269
# Fri, 08 Jul 2016 23:12:44 GMT
RUN curl -o wordpress.tar.gz -SL https://wordpress.org/wordpress-${WORDPRESS_VERSION}.tar.gz 	&& echo "$WORDPRESS_SHA1 *wordpress.tar.gz" | sha1sum -c - 	&& tar -xzf wordpress.tar.gz -C /usr/src/ 	&& rm wordpress.tar.gz 	&& chown -R www-data:www-data /usr/src/wordpress
# Fri, 08 Jul 2016 23:12:45 GMT
COPY file:28ccaf78edbf6e7811305e5409bbaa660f9992cad70c071c67cd040bfcb9057e in /entrypoint.sh
# Fri, 08 Jul 2016 23:12:46 GMT
ENTRYPOINT &{["/entrypoint.sh"]}
# Fri, 08 Jul 2016 23:12:46 GMT
CMD ["apache2-foreground"]
```

-	Layers:
	-	`sha256:5c90d4a2d1a8dfffd05ff2dd659923f0ca2d843b5e45d030e17abbcd06a11b5b`  
		Last Modified: Thu, 09 Jun 2016 21:30:47 GMT  
		Size: 51.4 MB (51352535 bytes)
	-	`sha256:357b76a4983822c380125e911928d20bf853d3a4ca869181c757d855408a9c90`  
		Last Modified: Tue, 14 Jun 2016 21:44:40 GMT  
		Size: 77.3 MB (77343405 bytes)
	-	`sha256:0e87614c69f0ba521d6a89ea9b82a5712ff209dfa89e14b1fef8be2056d5680d`  
		Last Modified: Tue, 14 Jun 2016 21:44:12 GMT  
		Size: 180.0 B
	-	`sha256:a3a94d3df9be4137d53c70f13e1bf0e40d300e41c9773a3b5b26d68d75f31797`  
		Last Modified: Tue, 14 Jun 2016 21:44:14 GMT  
		Size: 2.9 MB (2874106 bytes)
	-	`sha256:ac140e12d947b453d23e00fd4099540ef06a9cfec9ac8d0183641b8d301e0f4f`  
		Last Modified: Thu, 07 Jul 2016 19:41:39 GMT  
		Size: 277.0 B
	-	`sha256:e08ee42cd95f62a54fcd329593aa277c5a62fb2fb6bfc8a3103556b23f7a9cd8`  
		Last Modified: Thu, 07 Jul 2016 19:41:39 GMT  
		Size: 430.0 B
	-	`sha256:d4cac1e00ff618b3862877517bb6b85ad52560be5ea79d076c2f670ed7471f34`  
		Last Modified: Thu, 07 Jul 2016 19:41:36 GMT  
		Size: 224.0 B
	-	`sha256:f2749ebafcf639d790352065364892fb26e952ee2c90f41a94b9af3e2a06b6fc`  
		Last Modified: Fri, 08 Jul 2016 22:31:48 GMT  
		Size: 474.0 B
	-	`sha256:b83b18211b0e6523d464cf2237852f82bbc2f6477a2b8a6e27b88a9cdd7c884c`  
		Last Modified: Fri, 08 Jul 2016 22:36:55 GMT  
		Size: 33.5 MB (33498380 bytes)
	-	`sha256:eff2616aae67a23b0fa5482b3a3771e05a0875eae9d3a02c20ced93b155098ab`  
		Last Modified: Fri, 08 Jul 2016 22:36:40 GMT  
		Size: 1.8 KB (1756 bytes)
	-	`sha256:76333cc4945328a2d994e3b590629e2fd2bfa8f9e82f395816da523fc11ac31f`  
		Last Modified: Fri, 08 Jul 2016 22:36:37 GMT  
		Size: 584.0 B
	-	`sha256:81895367a65f4cdf8f2454d668080dd83c43dadc2f69f6a01ebfe0426be7e13f`  
		Last Modified: Fri, 08 Jul 2016 23:12:54 GMT  
		Size: 326.0 B
	-	`sha256:dceeb874afb26f6b1cd50f1b5b5afdcce69f3b09a61ef2bccbf80a5c7f198d76`  
		Last Modified: Fri, 08 Jul 2016 23:12:56 GMT  
		Size: 4.5 MB (4473999 bytes)
	-	`sha256:b7b129bc1e78347a1544b8c03108d3c67e7e679fe76c85ae852915b6a15059a6`  
		Last Modified: Fri, 08 Jul 2016 23:12:54 GMT  
		Size: 333.0 B
	-	`sha256:65a991c10dcb57bdd0f3a93991780e0309d70fe2a876472e20648ca31372903d`  
		Last Modified: Fri, 08 Jul 2016 23:12:56 GMT  
		Size: 7.6 MB (7611911 bytes)
	-	`sha256:adff62f88fa960539b49ecb3ac3b1a29a92ff6421ded81455f5b545a1c772b21`  
		Last Modified: Fri, 08 Jul 2016 23:12:55 GMT  
		Size: 2.5 KB (2493 bytes)

## `wordpress:apache`

```console
$ docker pull wordpress@sha256:7bb9549fb6d80c230bec2da6bd181be8f30e5199687e53e5ad5744a3144eae1b
```

-	Platforms:
	-	linux; amd64

### `wordpress:apache` - linux; amd64

-	Docker Version: 1.10.3
-	Manifest MIME: `application/vnd.docker.distribution.manifest.v2+json`
-	Total Size: **177.2 MB (177161413 bytes)**  
	(compressed transfer size, not on-disk size)
-	Image ID: `sha256:e3f325718719293c09079bbbb1a2b9bf9053172bc594b5f3acf8d370efe8afae`
-	Entrypoint: `["\/entrypoint.sh"]`
-	Default Command: `["apache2-foreground"]`

```dockerfile
# Thu, 09 Jun 2016 21:28:42 GMT
ADD file:76679eeb94129df23c99013487d6b6bd779d2107bf07d194a524fdbb6a961530 in /
# Thu, 09 Jun 2016 21:28:43 GMT
CMD ["/bin/bash"]
# Fri, 10 Jun 2016 02:34:30 GMT
ENV PHPIZE_DEPS=autoconf 		file 		g++ 		gcc 		libc-dev 		make 		pkg-config 		re2c
# Fri, 10 Jun 2016 02:35:57 GMT
RUN apt-get update && apt-get install -y 		$PHPIZE_DEPS 		ca-certificates 		curl 		libedit2 		libsqlite3-0 		libxml2 	--no-install-recommends && rm -r /var/lib/apt/lists/*
# Fri, 10 Jun 2016 02:35:58 GMT
ENV PHP_INI_DIR=/usr/local/etc/php
# Fri, 10 Jun 2016 02:35:59 GMT
RUN mkdir -p $PHP_INI_DIR/conf.d
# Fri, 10 Jun 2016 02:43:42 GMT
RUN apt-get update && apt-get install -y apache2-bin apache2.2-common --no-install-recommends && rm -rf /var/lib/apt/lists/*
# Thu, 07 Jul 2016 19:23:45 GMT
ENV APACHE_CONFDIR=/etc/apache2
# Thu, 07 Jul 2016 19:23:46 GMT
ENV APACHE_ENVVARS=/etc/apache2/envvars
# Thu, 07 Jul 2016 19:23:48 GMT
RUN set -ex 	&& . "$APACHE_ENVVARS" 	&& for dir in 		"$APACHE_LOCK_DIR" 		"$APACHE_RUN_DIR" 		"$APACHE_LOG_DIR" 		/var/www/html 	; do 		rm -rvf "$dir" 		&& mkdir -p "$dir" 		&& chown -R "$APACHE_RUN_USER:$APACHE_RUN_GROUP" "$dir"; 	done
# Thu, 07 Jul 2016 19:23:49 GMT
RUN a2dismod mpm_event && a2enmod mpm_prefork
# Thu, 07 Jul 2016 19:23:51 GMT
RUN set -ex 	&& . "$APACHE_ENVVARS" 	&& ln -sfT /dev/stderr "$APACHE_LOG_DIR/error.log" 	&& ln -sfT /dev/stdout "$APACHE_LOG_DIR/access.log" 	&& ln -sfT /dev/stdout "$APACHE_LOG_DIR/other_vhosts_access.log"
# Fri, 08 Jul 2016 22:14:00 GMT
RUN { 		echo '<FilesMatch \.php$>'; 		echo '\tSetHandler application/x-httpd-php'; 		echo '</FilesMatch>'; 		echo; 		echo 'DirectoryIndex disabled'; 		echo 'DirectoryIndex index.php index.html'; 		echo; 		echo '<Directory /var/www/>'; 		echo '\tOptions -Indexes'; 		echo '\tAllowOverride All'; 		echo '</Directory>'; 	} | tee "$APACHE_CONFDIR/conf-available/docker-php.conf" 	&& a2enconf docker-php
# Fri, 08 Jul 2016 22:14:01 GMT
ENV PHP_EXTRA_BUILD_DEPS=apache2-dev
# Fri, 08 Jul 2016 22:14:01 GMT
ENV PHP_EXTRA_CONFIGURE_ARGS=--with-apxs2
# Fri, 08 Jul 2016 22:19:29 GMT
ENV GPG_KEYS=0BD78B5F97500D450838F95DFE857D9A90D90EC1 6E4F6AB321FDC07F2C332E3AC2BF0BC433CFC8B3
# Fri, 08 Jul 2016 22:19:30 GMT
ENV PHP_VERSION=5.6.23
# Fri, 08 Jul 2016 22:19:30 GMT
ENV PHP_FILENAME=php-5.6.23.tar.xz
# Fri, 08 Jul 2016 22:19:30 GMT
ENV PHP_SHA256=39141e9a617af172aedbbacee7a63eb15502850f7cea20d759a9cffa7cfb0a1a
# Fri, 08 Jul 2016 22:24:42 GMT
RUN set -xe 	&& buildDeps=" 		$PHP_EXTRA_BUILD_DEPS 		libcurl4-openssl-dev 		libedit-dev 		libsqlite3-dev 		libssl-dev 		libxml2-dev 		xz-utils 	" 	&& apt-get update && apt-get install -y $buildDeps --no-install-recommends && rm -rf /var/lib/apt/lists/* 	&& curl -fSL "http://php.net/get/$PHP_FILENAME/from/this/mirror" -o "$PHP_FILENAME" 	&& echo "$PHP_SHA256 *$PHP_FILENAME" | sha256sum -c - 	&& curl -fSL "http://php.net/get/$PHP_FILENAME.asc/from/this/mirror" -o "$PHP_FILENAME.asc" 	&& export GNUPGHOME="$(mktemp -d)" 	&& for key in $GPG_KEYS; do 		gpg --keyserver ha.pool.sks-keyservers.net --recv-keys "$key"; 	done 	&& gpg --batch --verify "$PHP_FILENAME.asc" "$PHP_FILENAME" 	&& rm -r "$GNUPGHOME" "$PHP_FILENAME.asc" 	&& mkdir -p /usr/src/php 	&& tar -xf "$PHP_FILENAME" -C /usr/src/php --strip-components=1 	&& rm "$PHP_FILENAME" 	&& cd /usr/src/php 	&& ./configure 		--with-config-file-path="$PHP_INI_DIR" 		--with-config-file-scan-dir="$PHP_INI_DIR/conf.d" 		$PHP_EXTRA_CONFIGURE_ARGS 		--disable-cgi 		--enable-mysqlnd 		--enable-mbstring 		--with-curl 		--with-libedit 		--with-openssl 		--with-zlib 	&& make -j"$(nproc)" 	&& make install 	&& { find /usr/local/bin /usr/local/sbin -type f -executable -exec strip --strip-all '{}' + || true; } 	&& make clean 	&& apt-get purge -y --auto-remove -o APT::AutoRemove::RecommendsImportant=false -o APT::AutoRemove::SuggestsImportant=false $buildDeps
# Fri, 08 Jul 2016 22:24:43 GMT
COPY multi:a8819301efc7ce6569bcf183723931153c5b968224bce96498ddbabe72ce7eaa in /usr/local/bin/
# Fri, 08 Jul 2016 22:24:44 GMT
COPY file:3014772111b66da3129ca8caeafdd1dcfa9a3bf518f015ae9acc3c7b9b1b44c9 in /usr/local/bin/
# Fri, 08 Jul 2016 22:24:44 GMT
WORKDIR /var/www/html
# Fri, 08 Jul 2016 22:24:45 GMT
EXPOSE 80/tcp
# Fri, 08 Jul 2016 22:24:45 GMT
CMD ["apache2-foreground"]
# Fri, 08 Jul 2016 23:10:56 GMT
RUN a2enmod rewrite expires
# Fri, 08 Jul 2016 23:12:37 GMT
RUN apt-get update && apt-get install -y libpng12-dev libjpeg-dev && rm -rf /var/lib/apt/lists/* 	&& docker-php-ext-configure gd --with-png-dir=/usr --with-jpeg-dir=/usr 	&& docker-php-ext-install gd mysqli opcache
# Fri, 08 Jul 2016 23:12:39 GMT
RUN { 		echo 'opcache.memory_consumption=128'; 		echo 'opcache.interned_strings_buffer=8'; 		echo 'opcache.max_accelerated_files=4000'; 		echo 'opcache.revalidate_freq=60'; 		echo 'opcache.fast_shutdown=1'; 		echo 'opcache.enable_cli=1'; 	} > /usr/local/etc/php/conf.d/opcache-recommended.ini
# Fri, 08 Jul 2016 23:12:40 GMT
VOLUME [/var/www/html]
# Fri, 08 Jul 2016 23:12:40 GMT
ENV WORDPRESS_VERSION=4.5.3
# Fri, 08 Jul 2016 23:12:41 GMT
ENV WORDPRESS_SHA1=835b68748dae5a9d31c059313cd0150f03a49269
# Fri, 08 Jul 2016 23:12:44 GMT
RUN curl -o wordpress.tar.gz -SL https://wordpress.org/wordpress-${WORDPRESS_VERSION}.tar.gz 	&& echo "$WORDPRESS_SHA1 *wordpress.tar.gz" | sha1sum -c - 	&& tar -xzf wordpress.tar.gz -C /usr/src/ 	&& rm wordpress.tar.gz 	&& chown -R www-data:www-data /usr/src/wordpress
# Fri, 08 Jul 2016 23:12:45 GMT
COPY file:28ccaf78edbf6e7811305e5409bbaa660f9992cad70c071c67cd040bfcb9057e in /entrypoint.sh
# Fri, 08 Jul 2016 23:12:46 GMT
ENTRYPOINT &{["/entrypoint.sh"]}
# Fri, 08 Jul 2016 23:12:46 GMT
CMD ["apache2-foreground"]
```

-	Layers:
	-	`sha256:5c90d4a2d1a8dfffd05ff2dd659923f0ca2d843b5e45d030e17abbcd06a11b5b`  
		Last Modified: Thu, 09 Jun 2016 21:30:47 GMT  
		Size: 51.4 MB (51352535 bytes)
	-	`sha256:357b76a4983822c380125e911928d20bf853d3a4ca869181c757d855408a9c90`  
		Last Modified: Tue, 14 Jun 2016 21:44:40 GMT  
		Size: 77.3 MB (77343405 bytes)
	-	`sha256:0e87614c69f0ba521d6a89ea9b82a5712ff209dfa89e14b1fef8be2056d5680d`  
		Last Modified: Tue, 14 Jun 2016 21:44:12 GMT  
		Size: 180.0 B
	-	`sha256:a3a94d3df9be4137d53c70f13e1bf0e40d300e41c9773a3b5b26d68d75f31797`  
		Last Modified: Tue, 14 Jun 2016 21:44:14 GMT  
		Size: 2.9 MB (2874106 bytes)
	-	`sha256:ac140e12d947b453d23e00fd4099540ef06a9cfec9ac8d0183641b8d301e0f4f`  
		Last Modified: Thu, 07 Jul 2016 19:41:39 GMT  
		Size: 277.0 B
	-	`sha256:e08ee42cd95f62a54fcd329593aa277c5a62fb2fb6bfc8a3103556b23f7a9cd8`  
		Last Modified: Thu, 07 Jul 2016 19:41:39 GMT  
		Size: 430.0 B
	-	`sha256:d4cac1e00ff618b3862877517bb6b85ad52560be5ea79d076c2f670ed7471f34`  
		Last Modified: Thu, 07 Jul 2016 19:41:36 GMT  
		Size: 224.0 B
	-	`sha256:f2749ebafcf639d790352065364892fb26e952ee2c90f41a94b9af3e2a06b6fc`  
		Last Modified: Fri, 08 Jul 2016 22:31:48 GMT  
		Size: 474.0 B
	-	`sha256:b83b18211b0e6523d464cf2237852f82bbc2f6477a2b8a6e27b88a9cdd7c884c`  
		Last Modified: Fri, 08 Jul 2016 22:36:55 GMT  
		Size: 33.5 MB (33498380 bytes)
	-	`sha256:eff2616aae67a23b0fa5482b3a3771e05a0875eae9d3a02c20ced93b155098ab`  
		Last Modified: Fri, 08 Jul 2016 22:36:40 GMT  
		Size: 1.8 KB (1756 bytes)
	-	`sha256:76333cc4945328a2d994e3b590629e2fd2bfa8f9e82f395816da523fc11ac31f`  
		Last Modified: Fri, 08 Jul 2016 22:36:37 GMT  
		Size: 584.0 B
	-	`sha256:81895367a65f4cdf8f2454d668080dd83c43dadc2f69f6a01ebfe0426be7e13f`  
		Last Modified: Fri, 08 Jul 2016 23:12:54 GMT  
		Size: 326.0 B
	-	`sha256:dceeb874afb26f6b1cd50f1b5b5afdcce69f3b09a61ef2bccbf80a5c7f198d76`  
		Last Modified: Fri, 08 Jul 2016 23:12:56 GMT  
		Size: 4.5 MB (4473999 bytes)
	-	`sha256:b7b129bc1e78347a1544b8c03108d3c67e7e679fe76c85ae852915b6a15059a6`  
		Last Modified: Fri, 08 Jul 2016 23:12:54 GMT  
		Size: 333.0 B
	-	`sha256:65a991c10dcb57bdd0f3a93991780e0309d70fe2a876472e20648ca31372903d`  
		Last Modified: Fri, 08 Jul 2016 23:12:56 GMT  
		Size: 7.6 MB (7611911 bytes)
	-	`sha256:adff62f88fa960539b49ecb3ac3b1a29a92ff6421ded81455f5b545a1c772b21`  
		Last Modified: Fri, 08 Jul 2016 23:12:55 GMT  
		Size: 2.5 KB (2493 bytes)

## `wordpress:4.5.3`

```console
$ docker pull wordpress@sha256:7bb9549fb6d80c230bec2da6bd181be8f30e5199687e53e5ad5744a3144eae1b
```

-	Platforms:
	-	linux; amd64

### `wordpress:4.5.3` - linux; amd64

-	Docker Version: 1.10.3
-	Manifest MIME: `application/vnd.docker.distribution.manifest.v2+json`
-	Total Size: **177.2 MB (177161413 bytes)**  
	(compressed transfer size, not on-disk size)
-	Image ID: `sha256:e3f325718719293c09079bbbb1a2b9bf9053172bc594b5f3acf8d370efe8afae`
-	Entrypoint: `["\/entrypoint.sh"]`
-	Default Command: `["apache2-foreground"]`

```dockerfile
# Thu, 09 Jun 2016 21:28:42 GMT
ADD file:76679eeb94129df23c99013487d6b6bd779d2107bf07d194a524fdbb6a961530 in /
# Thu, 09 Jun 2016 21:28:43 GMT
CMD ["/bin/bash"]
# Fri, 10 Jun 2016 02:34:30 GMT
ENV PHPIZE_DEPS=autoconf 		file 		g++ 		gcc 		libc-dev 		make 		pkg-config 		re2c
# Fri, 10 Jun 2016 02:35:57 GMT
RUN apt-get update && apt-get install -y 		$PHPIZE_DEPS 		ca-certificates 		curl 		libedit2 		libsqlite3-0 		libxml2 	--no-install-recommends && rm -r /var/lib/apt/lists/*
# Fri, 10 Jun 2016 02:35:58 GMT
ENV PHP_INI_DIR=/usr/local/etc/php
# Fri, 10 Jun 2016 02:35:59 GMT
RUN mkdir -p $PHP_INI_DIR/conf.d
# Fri, 10 Jun 2016 02:43:42 GMT
RUN apt-get update && apt-get install -y apache2-bin apache2.2-common --no-install-recommends && rm -rf /var/lib/apt/lists/*
# Thu, 07 Jul 2016 19:23:45 GMT
ENV APACHE_CONFDIR=/etc/apache2
# Thu, 07 Jul 2016 19:23:46 GMT
ENV APACHE_ENVVARS=/etc/apache2/envvars
# Thu, 07 Jul 2016 19:23:48 GMT
RUN set -ex 	&& . "$APACHE_ENVVARS" 	&& for dir in 		"$APACHE_LOCK_DIR" 		"$APACHE_RUN_DIR" 		"$APACHE_LOG_DIR" 		/var/www/html 	; do 		rm -rvf "$dir" 		&& mkdir -p "$dir" 		&& chown -R "$APACHE_RUN_USER:$APACHE_RUN_GROUP" "$dir"; 	done
# Thu, 07 Jul 2016 19:23:49 GMT
RUN a2dismod mpm_event && a2enmod mpm_prefork
# Thu, 07 Jul 2016 19:23:51 GMT
RUN set -ex 	&& . "$APACHE_ENVVARS" 	&& ln -sfT /dev/stderr "$APACHE_LOG_DIR/error.log" 	&& ln -sfT /dev/stdout "$APACHE_LOG_DIR/access.log" 	&& ln -sfT /dev/stdout "$APACHE_LOG_DIR/other_vhosts_access.log"
# Fri, 08 Jul 2016 22:14:00 GMT
RUN { 		echo '<FilesMatch \.php$>'; 		echo '\tSetHandler application/x-httpd-php'; 		echo '</FilesMatch>'; 		echo; 		echo 'DirectoryIndex disabled'; 		echo 'DirectoryIndex index.php index.html'; 		echo; 		echo '<Directory /var/www/>'; 		echo '\tOptions -Indexes'; 		echo '\tAllowOverride All'; 		echo '</Directory>'; 	} | tee "$APACHE_CONFDIR/conf-available/docker-php.conf" 	&& a2enconf docker-php
# Fri, 08 Jul 2016 22:14:01 GMT
ENV PHP_EXTRA_BUILD_DEPS=apache2-dev
# Fri, 08 Jul 2016 22:14:01 GMT
ENV PHP_EXTRA_CONFIGURE_ARGS=--with-apxs2
# Fri, 08 Jul 2016 22:19:29 GMT
ENV GPG_KEYS=0BD78B5F97500D450838F95DFE857D9A90D90EC1 6E4F6AB321FDC07F2C332E3AC2BF0BC433CFC8B3
# Fri, 08 Jul 2016 22:19:30 GMT
ENV PHP_VERSION=5.6.23
# Fri, 08 Jul 2016 22:19:30 GMT
ENV PHP_FILENAME=php-5.6.23.tar.xz
# Fri, 08 Jul 2016 22:19:30 GMT
ENV PHP_SHA256=39141e9a617af172aedbbacee7a63eb15502850f7cea20d759a9cffa7cfb0a1a
# Fri, 08 Jul 2016 22:24:42 GMT
RUN set -xe 	&& buildDeps=" 		$PHP_EXTRA_BUILD_DEPS 		libcurl4-openssl-dev 		libedit-dev 		libsqlite3-dev 		libssl-dev 		libxml2-dev 		xz-utils 	" 	&& apt-get update && apt-get install -y $buildDeps --no-install-recommends && rm -rf /var/lib/apt/lists/* 	&& curl -fSL "http://php.net/get/$PHP_FILENAME/from/this/mirror" -o "$PHP_FILENAME" 	&& echo "$PHP_SHA256 *$PHP_FILENAME" | sha256sum -c - 	&& curl -fSL "http://php.net/get/$PHP_FILENAME.asc/from/this/mirror" -o "$PHP_FILENAME.asc" 	&& export GNUPGHOME="$(mktemp -d)" 	&& for key in $GPG_KEYS; do 		gpg --keyserver ha.pool.sks-keyservers.net --recv-keys "$key"; 	done 	&& gpg --batch --verify "$PHP_FILENAME.asc" "$PHP_FILENAME" 	&& rm -r "$GNUPGHOME" "$PHP_FILENAME.asc" 	&& mkdir -p /usr/src/php 	&& tar -xf "$PHP_FILENAME" -C /usr/src/php --strip-components=1 	&& rm "$PHP_FILENAME" 	&& cd /usr/src/php 	&& ./configure 		--with-config-file-path="$PHP_INI_DIR" 		--with-config-file-scan-dir="$PHP_INI_DIR/conf.d" 		$PHP_EXTRA_CONFIGURE_ARGS 		--disable-cgi 		--enable-mysqlnd 		--enable-mbstring 		--with-curl 		--with-libedit 		--with-openssl 		--with-zlib 	&& make -j"$(nproc)" 	&& make install 	&& { find /usr/local/bin /usr/local/sbin -type f -executable -exec strip --strip-all '{}' + || true; } 	&& make clean 	&& apt-get purge -y --auto-remove -o APT::AutoRemove::RecommendsImportant=false -o APT::AutoRemove::SuggestsImportant=false $buildDeps
# Fri, 08 Jul 2016 22:24:43 GMT
COPY multi:a8819301efc7ce6569bcf183723931153c5b968224bce96498ddbabe72ce7eaa in /usr/local/bin/
# Fri, 08 Jul 2016 22:24:44 GMT
COPY file:3014772111b66da3129ca8caeafdd1dcfa9a3bf518f015ae9acc3c7b9b1b44c9 in /usr/local/bin/
# Fri, 08 Jul 2016 22:24:44 GMT
WORKDIR /var/www/html
# Fri, 08 Jul 2016 22:24:45 GMT
EXPOSE 80/tcp
# Fri, 08 Jul 2016 22:24:45 GMT
CMD ["apache2-foreground"]
# Fri, 08 Jul 2016 23:10:56 GMT
RUN a2enmod rewrite expires
# Fri, 08 Jul 2016 23:12:37 GMT
RUN apt-get update && apt-get install -y libpng12-dev libjpeg-dev && rm -rf /var/lib/apt/lists/* 	&& docker-php-ext-configure gd --with-png-dir=/usr --with-jpeg-dir=/usr 	&& docker-php-ext-install gd mysqli opcache
# Fri, 08 Jul 2016 23:12:39 GMT
RUN { 		echo 'opcache.memory_consumption=128'; 		echo 'opcache.interned_strings_buffer=8'; 		echo 'opcache.max_accelerated_files=4000'; 		echo 'opcache.revalidate_freq=60'; 		echo 'opcache.fast_shutdown=1'; 		echo 'opcache.enable_cli=1'; 	} > /usr/local/etc/php/conf.d/opcache-recommended.ini
# Fri, 08 Jul 2016 23:12:40 GMT
VOLUME [/var/www/html]
# Fri, 08 Jul 2016 23:12:40 GMT
ENV WORDPRESS_VERSION=4.5.3
# Fri, 08 Jul 2016 23:12:41 GMT
ENV WORDPRESS_SHA1=835b68748dae5a9d31c059313cd0150f03a49269
# Fri, 08 Jul 2016 23:12:44 GMT
RUN curl -o wordpress.tar.gz -SL https://wordpress.org/wordpress-${WORDPRESS_VERSION}.tar.gz 	&& echo "$WORDPRESS_SHA1 *wordpress.tar.gz" | sha1sum -c - 	&& tar -xzf wordpress.tar.gz -C /usr/src/ 	&& rm wordpress.tar.gz 	&& chown -R www-data:www-data /usr/src/wordpress
# Fri, 08 Jul 2016 23:12:45 GMT
COPY file:28ccaf78edbf6e7811305e5409bbaa660f9992cad70c071c67cd040bfcb9057e in /entrypoint.sh
# Fri, 08 Jul 2016 23:12:46 GMT
ENTRYPOINT &{["/entrypoint.sh"]}
# Fri, 08 Jul 2016 23:12:46 GMT
CMD ["apache2-foreground"]
```

-	Layers:
	-	`sha256:5c90d4a2d1a8dfffd05ff2dd659923f0ca2d843b5e45d030e17abbcd06a11b5b`  
		Last Modified: Thu, 09 Jun 2016 21:30:47 GMT  
		Size: 51.4 MB (51352535 bytes)
	-	`sha256:357b76a4983822c380125e911928d20bf853d3a4ca869181c757d855408a9c90`  
		Last Modified: Tue, 14 Jun 2016 21:44:40 GMT  
		Size: 77.3 MB (77343405 bytes)
	-	`sha256:0e87614c69f0ba521d6a89ea9b82a5712ff209dfa89e14b1fef8be2056d5680d`  
		Last Modified: Tue, 14 Jun 2016 21:44:12 GMT  
		Size: 180.0 B
	-	`sha256:a3a94d3df9be4137d53c70f13e1bf0e40d300e41c9773a3b5b26d68d75f31797`  
		Last Modified: Tue, 14 Jun 2016 21:44:14 GMT  
		Size: 2.9 MB (2874106 bytes)
	-	`sha256:ac140e12d947b453d23e00fd4099540ef06a9cfec9ac8d0183641b8d301e0f4f`  
		Last Modified: Thu, 07 Jul 2016 19:41:39 GMT  
		Size: 277.0 B
	-	`sha256:e08ee42cd95f62a54fcd329593aa277c5a62fb2fb6bfc8a3103556b23f7a9cd8`  
		Last Modified: Thu, 07 Jul 2016 19:41:39 GMT  
		Size: 430.0 B
	-	`sha256:d4cac1e00ff618b3862877517bb6b85ad52560be5ea79d076c2f670ed7471f34`  
		Last Modified: Thu, 07 Jul 2016 19:41:36 GMT  
		Size: 224.0 B
	-	`sha256:f2749ebafcf639d790352065364892fb26e952ee2c90f41a94b9af3e2a06b6fc`  
		Last Modified: Fri, 08 Jul 2016 22:31:48 GMT  
		Size: 474.0 B
	-	`sha256:b83b18211b0e6523d464cf2237852f82bbc2f6477a2b8a6e27b88a9cdd7c884c`  
		Last Modified: Fri, 08 Jul 2016 22:36:55 GMT  
		Size: 33.5 MB (33498380 bytes)
	-	`sha256:eff2616aae67a23b0fa5482b3a3771e05a0875eae9d3a02c20ced93b155098ab`  
		Last Modified: Fri, 08 Jul 2016 22:36:40 GMT  
		Size: 1.8 KB (1756 bytes)
	-	`sha256:76333cc4945328a2d994e3b590629e2fd2bfa8f9e82f395816da523fc11ac31f`  
		Last Modified: Fri, 08 Jul 2016 22:36:37 GMT  
		Size: 584.0 B
	-	`sha256:81895367a65f4cdf8f2454d668080dd83c43dadc2f69f6a01ebfe0426be7e13f`  
		Last Modified: Fri, 08 Jul 2016 23:12:54 GMT  
		Size: 326.0 B
	-	`sha256:dceeb874afb26f6b1cd50f1b5b5afdcce69f3b09a61ef2bccbf80a5c7f198d76`  
		Last Modified: Fri, 08 Jul 2016 23:12:56 GMT  
		Size: 4.5 MB (4473999 bytes)
	-	`sha256:b7b129bc1e78347a1544b8c03108d3c67e7e679fe76c85ae852915b6a15059a6`  
		Last Modified: Fri, 08 Jul 2016 23:12:54 GMT  
		Size: 333.0 B
	-	`sha256:65a991c10dcb57bdd0f3a93991780e0309d70fe2a876472e20648ca31372903d`  
		Last Modified: Fri, 08 Jul 2016 23:12:56 GMT  
		Size: 7.6 MB (7611911 bytes)
	-	`sha256:adff62f88fa960539b49ecb3ac3b1a29a92ff6421ded81455f5b545a1c772b21`  
		Last Modified: Fri, 08 Jul 2016 23:12:55 GMT  
		Size: 2.5 KB (2493 bytes)

## `wordpress:4.5`

```console
$ docker pull wordpress@sha256:7bb9549fb6d80c230bec2da6bd181be8f30e5199687e53e5ad5744a3144eae1b
```

-	Platforms:
	-	linux; amd64

### `wordpress:4.5` - linux; amd64

-	Docker Version: 1.10.3
-	Manifest MIME: `application/vnd.docker.distribution.manifest.v2+json`
-	Total Size: **177.2 MB (177161413 bytes)**  
	(compressed transfer size, not on-disk size)
-	Image ID: `sha256:e3f325718719293c09079bbbb1a2b9bf9053172bc594b5f3acf8d370efe8afae`
-	Entrypoint: `["\/entrypoint.sh"]`
-	Default Command: `["apache2-foreground"]`

```dockerfile
# Thu, 09 Jun 2016 21:28:42 GMT
ADD file:76679eeb94129df23c99013487d6b6bd779d2107bf07d194a524fdbb6a961530 in /
# Thu, 09 Jun 2016 21:28:43 GMT
CMD ["/bin/bash"]
# Fri, 10 Jun 2016 02:34:30 GMT
ENV PHPIZE_DEPS=autoconf 		file 		g++ 		gcc 		libc-dev 		make 		pkg-config 		re2c
# Fri, 10 Jun 2016 02:35:57 GMT
RUN apt-get update && apt-get install -y 		$PHPIZE_DEPS 		ca-certificates 		curl 		libedit2 		libsqlite3-0 		libxml2 	--no-install-recommends && rm -r /var/lib/apt/lists/*
# Fri, 10 Jun 2016 02:35:58 GMT
ENV PHP_INI_DIR=/usr/local/etc/php
# Fri, 10 Jun 2016 02:35:59 GMT
RUN mkdir -p $PHP_INI_DIR/conf.d
# Fri, 10 Jun 2016 02:43:42 GMT
RUN apt-get update && apt-get install -y apache2-bin apache2.2-common --no-install-recommends && rm -rf /var/lib/apt/lists/*
# Thu, 07 Jul 2016 19:23:45 GMT
ENV APACHE_CONFDIR=/etc/apache2
# Thu, 07 Jul 2016 19:23:46 GMT
ENV APACHE_ENVVARS=/etc/apache2/envvars
# Thu, 07 Jul 2016 19:23:48 GMT
RUN set -ex 	&& . "$APACHE_ENVVARS" 	&& for dir in 		"$APACHE_LOCK_DIR" 		"$APACHE_RUN_DIR" 		"$APACHE_LOG_DIR" 		/var/www/html 	; do 		rm -rvf "$dir" 		&& mkdir -p "$dir" 		&& chown -R "$APACHE_RUN_USER:$APACHE_RUN_GROUP" "$dir"; 	done
# Thu, 07 Jul 2016 19:23:49 GMT
RUN a2dismod mpm_event && a2enmod mpm_prefork
# Thu, 07 Jul 2016 19:23:51 GMT
RUN set -ex 	&& . "$APACHE_ENVVARS" 	&& ln -sfT /dev/stderr "$APACHE_LOG_DIR/error.log" 	&& ln -sfT /dev/stdout "$APACHE_LOG_DIR/access.log" 	&& ln -sfT /dev/stdout "$APACHE_LOG_DIR/other_vhosts_access.log"
# Fri, 08 Jul 2016 22:14:00 GMT
RUN { 		echo '<FilesMatch \.php$>'; 		echo '\tSetHandler application/x-httpd-php'; 		echo '</FilesMatch>'; 		echo; 		echo 'DirectoryIndex disabled'; 		echo 'DirectoryIndex index.php index.html'; 		echo; 		echo '<Directory /var/www/>'; 		echo '\tOptions -Indexes'; 		echo '\tAllowOverride All'; 		echo '</Directory>'; 	} | tee "$APACHE_CONFDIR/conf-available/docker-php.conf" 	&& a2enconf docker-php
# Fri, 08 Jul 2016 22:14:01 GMT
ENV PHP_EXTRA_BUILD_DEPS=apache2-dev
# Fri, 08 Jul 2016 22:14:01 GMT
ENV PHP_EXTRA_CONFIGURE_ARGS=--with-apxs2
# Fri, 08 Jul 2016 22:19:29 GMT
ENV GPG_KEYS=0BD78B5F97500D450838F95DFE857D9A90D90EC1 6E4F6AB321FDC07F2C332E3AC2BF0BC433CFC8B3
# Fri, 08 Jul 2016 22:19:30 GMT
ENV PHP_VERSION=5.6.23
# Fri, 08 Jul 2016 22:19:30 GMT
ENV PHP_FILENAME=php-5.6.23.tar.xz
# Fri, 08 Jul 2016 22:19:30 GMT
ENV PHP_SHA256=39141e9a617af172aedbbacee7a63eb15502850f7cea20d759a9cffa7cfb0a1a
# Fri, 08 Jul 2016 22:24:42 GMT
RUN set -xe 	&& buildDeps=" 		$PHP_EXTRA_BUILD_DEPS 		libcurl4-openssl-dev 		libedit-dev 		libsqlite3-dev 		libssl-dev 		libxml2-dev 		xz-utils 	" 	&& apt-get update && apt-get install -y $buildDeps --no-install-recommends && rm -rf /var/lib/apt/lists/* 	&& curl -fSL "http://php.net/get/$PHP_FILENAME/from/this/mirror" -o "$PHP_FILENAME" 	&& echo "$PHP_SHA256 *$PHP_FILENAME" | sha256sum -c - 	&& curl -fSL "http://php.net/get/$PHP_FILENAME.asc/from/this/mirror" -o "$PHP_FILENAME.asc" 	&& export GNUPGHOME="$(mktemp -d)" 	&& for key in $GPG_KEYS; do 		gpg --keyserver ha.pool.sks-keyservers.net --recv-keys "$key"; 	done 	&& gpg --batch --verify "$PHP_FILENAME.asc" "$PHP_FILENAME" 	&& rm -r "$GNUPGHOME" "$PHP_FILENAME.asc" 	&& mkdir -p /usr/src/php 	&& tar -xf "$PHP_FILENAME" -C /usr/src/php --strip-components=1 	&& rm "$PHP_FILENAME" 	&& cd /usr/src/php 	&& ./configure 		--with-config-file-path="$PHP_INI_DIR" 		--with-config-file-scan-dir="$PHP_INI_DIR/conf.d" 		$PHP_EXTRA_CONFIGURE_ARGS 		--disable-cgi 		--enable-mysqlnd 		--enable-mbstring 		--with-curl 		--with-libedit 		--with-openssl 		--with-zlib 	&& make -j"$(nproc)" 	&& make install 	&& { find /usr/local/bin /usr/local/sbin -type f -executable -exec strip --strip-all '{}' + || true; } 	&& make clean 	&& apt-get purge -y --auto-remove -o APT::AutoRemove::RecommendsImportant=false -o APT::AutoRemove::SuggestsImportant=false $buildDeps
# Fri, 08 Jul 2016 22:24:43 GMT
COPY multi:a8819301efc7ce6569bcf183723931153c5b968224bce96498ddbabe72ce7eaa in /usr/local/bin/
# Fri, 08 Jul 2016 22:24:44 GMT
COPY file:3014772111b66da3129ca8caeafdd1dcfa9a3bf518f015ae9acc3c7b9b1b44c9 in /usr/local/bin/
# Fri, 08 Jul 2016 22:24:44 GMT
WORKDIR /var/www/html
# Fri, 08 Jul 2016 22:24:45 GMT
EXPOSE 80/tcp
# Fri, 08 Jul 2016 22:24:45 GMT
CMD ["apache2-foreground"]
# Fri, 08 Jul 2016 23:10:56 GMT
RUN a2enmod rewrite expires
# Fri, 08 Jul 2016 23:12:37 GMT
RUN apt-get update && apt-get install -y libpng12-dev libjpeg-dev && rm -rf /var/lib/apt/lists/* 	&& docker-php-ext-configure gd --with-png-dir=/usr --with-jpeg-dir=/usr 	&& docker-php-ext-install gd mysqli opcache
# Fri, 08 Jul 2016 23:12:39 GMT
RUN { 		echo 'opcache.memory_consumption=128'; 		echo 'opcache.interned_strings_buffer=8'; 		echo 'opcache.max_accelerated_files=4000'; 		echo 'opcache.revalidate_freq=60'; 		echo 'opcache.fast_shutdown=1'; 		echo 'opcache.enable_cli=1'; 	} > /usr/local/etc/php/conf.d/opcache-recommended.ini
# Fri, 08 Jul 2016 23:12:40 GMT
VOLUME [/var/www/html]
# Fri, 08 Jul 2016 23:12:40 GMT
ENV WORDPRESS_VERSION=4.5.3
# Fri, 08 Jul 2016 23:12:41 GMT
ENV WORDPRESS_SHA1=835b68748dae5a9d31c059313cd0150f03a49269
# Fri, 08 Jul 2016 23:12:44 GMT
RUN curl -o wordpress.tar.gz -SL https://wordpress.org/wordpress-${WORDPRESS_VERSION}.tar.gz 	&& echo "$WORDPRESS_SHA1 *wordpress.tar.gz" | sha1sum -c - 	&& tar -xzf wordpress.tar.gz -C /usr/src/ 	&& rm wordpress.tar.gz 	&& chown -R www-data:www-data /usr/src/wordpress
# Fri, 08 Jul 2016 23:12:45 GMT
COPY file:28ccaf78edbf6e7811305e5409bbaa660f9992cad70c071c67cd040bfcb9057e in /entrypoint.sh
# Fri, 08 Jul 2016 23:12:46 GMT
ENTRYPOINT &{["/entrypoint.sh"]}
# Fri, 08 Jul 2016 23:12:46 GMT
CMD ["apache2-foreground"]
```

-	Layers:
	-	`sha256:5c90d4a2d1a8dfffd05ff2dd659923f0ca2d843b5e45d030e17abbcd06a11b5b`  
		Last Modified: Thu, 09 Jun 2016 21:30:47 GMT  
		Size: 51.4 MB (51352535 bytes)
	-	`sha256:357b76a4983822c380125e911928d20bf853d3a4ca869181c757d855408a9c90`  
		Last Modified: Tue, 14 Jun 2016 21:44:40 GMT  
		Size: 77.3 MB (77343405 bytes)
	-	`sha256:0e87614c69f0ba521d6a89ea9b82a5712ff209dfa89e14b1fef8be2056d5680d`  
		Last Modified: Tue, 14 Jun 2016 21:44:12 GMT  
		Size: 180.0 B
	-	`sha256:a3a94d3df9be4137d53c70f13e1bf0e40d300e41c9773a3b5b26d68d75f31797`  
		Last Modified: Tue, 14 Jun 2016 21:44:14 GMT  
		Size: 2.9 MB (2874106 bytes)
	-	`sha256:ac140e12d947b453d23e00fd4099540ef06a9cfec9ac8d0183641b8d301e0f4f`  
		Last Modified: Thu, 07 Jul 2016 19:41:39 GMT  
		Size: 277.0 B
	-	`sha256:e08ee42cd95f62a54fcd329593aa277c5a62fb2fb6bfc8a3103556b23f7a9cd8`  
		Last Modified: Thu, 07 Jul 2016 19:41:39 GMT  
		Size: 430.0 B
	-	`sha256:d4cac1e00ff618b3862877517bb6b85ad52560be5ea79d076c2f670ed7471f34`  
		Last Modified: Thu, 07 Jul 2016 19:41:36 GMT  
		Size: 224.0 B
	-	`sha256:f2749ebafcf639d790352065364892fb26e952ee2c90f41a94b9af3e2a06b6fc`  
		Last Modified: Fri, 08 Jul 2016 22:31:48 GMT  
		Size: 474.0 B
	-	`sha256:b83b18211b0e6523d464cf2237852f82bbc2f6477a2b8a6e27b88a9cdd7c884c`  
		Last Modified: Fri, 08 Jul 2016 22:36:55 GMT  
		Size: 33.5 MB (33498380 bytes)
	-	`sha256:eff2616aae67a23b0fa5482b3a3771e05a0875eae9d3a02c20ced93b155098ab`  
		Last Modified: Fri, 08 Jul 2016 22:36:40 GMT  
		Size: 1.8 KB (1756 bytes)
	-	`sha256:76333cc4945328a2d994e3b590629e2fd2bfa8f9e82f395816da523fc11ac31f`  
		Last Modified: Fri, 08 Jul 2016 22:36:37 GMT  
		Size: 584.0 B
	-	`sha256:81895367a65f4cdf8f2454d668080dd83c43dadc2f69f6a01ebfe0426be7e13f`  
		Last Modified: Fri, 08 Jul 2016 23:12:54 GMT  
		Size: 326.0 B
	-	`sha256:dceeb874afb26f6b1cd50f1b5b5afdcce69f3b09a61ef2bccbf80a5c7f198d76`  
		Last Modified: Fri, 08 Jul 2016 23:12:56 GMT  
		Size: 4.5 MB (4473999 bytes)
	-	`sha256:b7b129bc1e78347a1544b8c03108d3c67e7e679fe76c85ae852915b6a15059a6`  
		Last Modified: Fri, 08 Jul 2016 23:12:54 GMT  
		Size: 333.0 B
	-	`sha256:65a991c10dcb57bdd0f3a93991780e0309d70fe2a876472e20648ca31372903d`  
		Last Modified: Fri, 08 Jul 2016 23:12:56 GMT  
		Size: 7.6 MB (7611911 bytes)
	-	`sha256:adff62f88fa960539b49ecb3ac3b1a29a92ff6421ded81455f5b545a1c772b21`  
		Last Modified: Fri, 08 Jul 2016 23:12:55 GMT  
		Size: 2.5 KB (2493 bytes)

## `wordpress:4`

```console
$ docker pull wordpress@sha256:7bb9549fb6d80c230bec2da6bd181be8f30e5199687e53e5ad5744a3144eae1b
```

-	Platforms:
	-	linux; amd64

### `wordpress:4` - linux; amd64

-	Docker Version: 1.10.3
-	Manifest MIME: `application/vnd.docker.distribution.manifest.v2+json`
-	Total Size: **177.2 MB (177161413 bytes)**  
	(compressed transfer size, not on-disk size)
-	Image ID: `sha256:e3f325718719293c09079bbbb1a2b9bf9053172bc594b5f3acf8d370efe8afae`
-	Entrypoint: `["\/entrypoint.sh"]`
-	Default Command: `["apache2-foreground"]`

```dockerfile
# Thu, 09 Jun 2016 21:28:42 GMT
ADD file:76679eeb94129df23c99013487d6b6bd779d2107bf07d194a524fdbb6a961530 in /
# Thu, 09 Jun 2016 21:28:43 GMT
CMD ["/bin/bash"]
# Fri, 10 Jun 2016 02:34:30 GMT
ENV PHPIZE_DEPS=autoconf 		file 		g++ 		gcc 		libc-dev 		make 		pkg-config 		re2c
# Fri, 10 Jun 2016 02:35:57 GMT
RUN apt-get update && apt-get install -y 		$PHPIZE_DEPS 		ca-certificates 		curl 		libedit2 		libsqlite3-0 		libxml2 	--no-install-recommends && rm -r /var/lib/apt/lists/*
# Fri, 10 Jun 2016 02:35:58 GMT
ENV PHP_INI_DIR=/usr/local/etc/php
# Fri, 10 Jun 2016 02:35:59 GMT
RUN mkdir -p $PHP_INI_DIR/conf.d
# Fri, 10 Jun 2016 02:43:42 GMT
RUN apt-get update && apt-get install -y apache2-bin apache2.2-common --no-install-recommends && rm -rf /var/lib/apt/lists/*
# Thu, 07 Jul 2016 19:23:45 GMT
ENV APACHE_CONFDIR=/etc/apache2
# Thu, 07 Jul 2016 19:23:46 GMT
ENV APACHE_ENVVARS=/etc/apache2/envvars
# Thu, 07 Jul 2016 19:23:48 GMT
RUN set -ex 	&& . "$APACHE_ENVVARS" 	&& for dir in 		"$APACHE_LOCK_DIR" 		"$APACHE_RUN_DIR" 		"$APACHE_LOG_DIR" 		/var/www/html 	; do 		rm -rvf "$dir" 		&& mkdir -p "$dir" 		&& chown -R "$APACHE_RUN_USER:$APACHE_RUN_GROUP" "$dir"; 	done
# Thu, 07 Jul 2016 19:23:49 GMT
RUN a2dismod mpm_event && a2enmod mpm_prefork
# Thu, 07 Jul 2016 19:23:51 GMT
RUN set -ex 	&& . "$APACHE_ENVVARS" 	&& ln -sfT /dev/stderr "$APACHE_LOG_DIR/error.log" 	&& ln -sfT /dev/stdout "$APACHE_LOG_DIR/access.log" 	&& ln -sfT /dev/stdout "$APACHE_LOG_DIR/other_vhosts_access.log"
# Fri, 08 Jul 2016 22:14:00 GMT
RUN { 		echo '<FilesMatch \.php$>'; 		echo '\tSetHandler application/x-httpd-php'; 		echo '</FilesMatch>'; 		echo; 		echo 'DirectoryIndex disabled'; 		echo 'DirectoryIndex index.php index.html'; 		echo; 		echo '<Directory /var/www/>'; 		echo '\tOptions -Indexes'; 		echo '\tAllowOverride All'; 		echo '</Directory>'; 	} | tee "$APACHE_CONFDIR/conf-available/docker-php.conf" 	&& a2enconf docker-php
# Fri, 08 Jul 2016 22:14:01 GMT
ENV PHP_EXTRA_BUILD_DEPS=apache2-dev
# Fri, 08 Jul 2016 22:14:01 GMT
ENV PHP_EXTRA_CONFIGURE_ARGS=--with-apxs2
# Fri, 08 Jul 2016 22:19:29 GMT
ENV GPG_KEYS=0BD78B5F97500D450838F95DFE857D9A90D90EC1 6E4F6AB321FDC07F2C332E3AC2BF0BC433CFC8B3
# Fri, 08 Jul 2016 22:19:30 GMT
ENV PHP_VERSION=5.6.23
# Fri, 08 Jul 2016 22:19:30 GMT
ENV PHP_FILENAME=php-5.6.23.tar.xz
# Fri, 08 Jul 2016 22:19:30 GMT
ENV PHP_SHA256=39141e9a617af172aedbbacee7a63eb15502850f7cea20d759a9cffa7cfb0a1a
# Fri, 08 Jul 2016 22:24:42 GMT
RUN set -xe 	&& buildDeps=" 		$PHP_EXTRA_BUILD_DEPS 		libcurl4-openssl-dev 		libedit-dev 		libsqlite3-dev 		libssl-dev 		libxml2-dev 		xz-utils 	" 	&& apt-get update && apt-get install -y $buildDeps --no-install-recommends && rm -rf /var/lib/apt/lists/* 	&& curl -fSL "http://php.net/get/$PHP_FILENAME/from/this/mirror" -o "$PHP_FILENAME" 	&& echo "$PHP_SHA256 *$PHP_FILENAME" | sha256sum -c - 	&& curl -fSL "http://php.net/get/$PHP_FILENAME.asc/from/this/mirror" -o "$PHP_FILENAME.asc" 	&& export GNUPGHOME="$(mktemp -d)" 	&& for key in $GPG_KEYS; do 		gpg --keyserver ha.pool.sks-keyservers.net --recv-keys "$key"; 	done 	&& gpg --batch --verify "$PHP_FILENAME.asc" "$PHP_FILENAME" 	&& rm -r "$GNUPGHOME" "$PHP_FILENAME.asc" 	&& mkdir -p /usr/src/php 	&& tar -xf "$PHP_FILENAME" -C /usr/src/php --strip-components=1 	&& rm "$PHP_FILENAME" 	&& cd /usr/src/php 	&& ./configure 		--with-config-file-path="$PHP_INI_DIR" 		--with-config-file-scan-dir="$PHP_INI_DIR/conf.d" 		$PHP_EXTRA_CONFIGURE_ARGS 		--disable-cgi 		--enable-mysqlnd 		--enable-mbstring 		--with-curl 		--with-libedit 		--with-openssl 		--with-zlib 	&& make -j"$(nproc)" 	&& make install 	&& { find /usr/local/bin /usr/local/sbin -type f -executable -exec strip --strip-all '{}' + || true; } 	&& make clean 	&& apt-get purge -y --auto-remove -o APT::AutoRemove::RecommendsImportant=false -o APT::AutoRemove::SuggestsImportant=false $buildDeps
# Fri, 08 Jul 2016 22:24:43 GMT
COPY multi:a8819301efc7ce6569bcf183723931153c5b968224bce96498ddbabe72ce7eaa in /usr/local/bin/
# Fri, 08 Jul 2016 22:24:44 GMT
COPY file:3014772111b66da3129ca8caeafdd1dcfa9a3bf518f015ae9acc3c7b9b1b44c9 in /usr/local/bin/
# Fri, 08 Jul 2016 22:24:44 GMT
WORKDIR /var/www/html
# Fri, 08 Jul 2016 22:24:45 GMT
EXPOSE 80/tcp
# Fri, 08 Jul 2016 22:24:45 GMT
CMD ["apache2-foreground"]
# Fri, 08 Jul 2016 23:10:56 GMT
RUN a2enmod rewrite expires
# Fri, 08 Jul 2016 23:12:37 GMT
RUN apt-get update && apt-get install -y libpng12-dev libjpeg-dev && rm -rf /var/lib/apt/lists/* 	&& docker-php-ext-configure gd --with-png-dir=/usr --with-jpeg-dir=/usr 	&& docker-php-ext-install gd mysqli opcache
# Fri, 08 Jul 2016 23:12:39 GMT
RUN { 		echo 'opcache.memory_consumption=128'; 		echo 'opcache.interned_strings_buffer=8'; 		echo 'opcache.max_accelerated_files=4000'; 		echo 'opcache.revalidate_freq=60'; 		echo 'opcache.fast_shutdown=1'; 		echo 'opcache.enable_cli=1'; 	} > /usr/local/etc/php/conf.d/opcache-recommended.ini
# Fri, 08 Jul 2016 23:12:40 GMT
VOLUME [/var/www/html]
# Fri, 08 Jul 2016 23:12:40 GMT
ENV WORDPRESS_VERSION=4.5.3
# Fri, 08 Jul 2016 23:12:41 GMT
ENV WORDPRESS_SHA1=835b68748dae5a9d31c059313cd0150f03a49269
# Fri, 08 Jul 2016 23:12:44 GMT
RUN curl -o wordpress.tar.gz -SL https://wordpress.org/wordpress-${WORDPRESS_VERSION}.tar.gz 	&& echo "$WORDPRESS_SHA1 *wordpress.tar.gz" | sha1sum -c - 	&& tar -xzf wordpress.tar.gz -C /usr/src/ 	&& rm wordpress.tar.gz 	&& chown -R www-data:www-data /usr/src/wordpress
# Fri, 08 Jul 2016 23:12:45 GMT
COPY file:28ccaf78edbf6e7811305e5409bbaa660f9992cad70c071c67cd040bfcb9057e in /entrypoint.sh
# Fri, 08 Jul 2016 23:12:46 GMT
ENTRYPOINT &{["/entrypoint.sh"]}
# Fri, 08 Jul 2016 23:12:46 GMT
CMD ["apache2-foreground"]
```

-	Layers:
	-	`sha256:5c90d4a2d1a8dfffd05ff2dd659923f0ca2d843b5e45d030e17abbcd06a11b5b`  
		Last Modified: Thu, 09 Jun 2016 21:30:47 GMT  
		Size: 51.4 MB (51352535 bytes)
	-	`sha256:357b76a4983822c380125e911928d20bf853d3a4ca869181c757d855408a9c90`  
		Last Modified: Tue, 14 Jun 2016 21:44:40 GMT  
		Size: 77.3 MB (77343405 bytes)
	-	`sha256:0e87614c69f0ba521d6a89ea9b82a5712ff209dfa89e14b1fef8be2056d5680d`  
		Last Modified: Tue, 14 Jun 2016 21:44:12 GMT  
		Size: 180.0 B
	-	`sha256:a3a94d3df9be4137d53c70f13e1bf0e40d300e41c9773a3b5b26d68d75f31797`  
		Last Modified: Tue, 14 Jun 2016 21:44:14 GMT  
		Size: 2.9 MB (2874106 bytes)
	-	`sha256:ac140e12d947b453d23e00fd4099540ef06a9cfec9ac8d0183641b8d301e0f4f`  
		Last Modified: Thu, 07 Jul 2016 19:41:39 GMT  
		Size: 277.0 B
	-	`sha256:e08ee42cd95f62a54fcd329593aa277c5a62fb2fb6bfc8a3103556b23f7a9cd8`  
		Last Modified: Thu, 07 Jul 2016 19:41:39 GMT  
		Size: 430.0 B
	-	`sha256:d4cac1e00ff618b3862877517bb6b85ad52560be5ea79d076c2f670ed7471f34`  
		Last Modified: Thu, 07 Jul 2016 19:41:36 GMT  
		Size: 224.0 B
	-	`sha256:f2749ebafcf639d790352065364892fb26e952ee2c90f41a94b9af3e2a06b6fc`  
		Last Modified: Fri, 08 Jul 2016 22:31:48 GMT  
		Size: 474.0 B
	-	`sha256:b83b18211b0e6523d464cf2237852f82bbc2f6477a2b8a6e27b88a9cdd7c884c`  
		Last Modified: Fri, 08 Jul 2016 22:36:55 GMT  
		Size: 33.5 MB (33498380 bytes)
	-	`sha256:eff2616aae67a23b0fa5482b3a3771e05a0875eae9d3a02c20ced93b155098ab`  
		Last Modified: Fri, 08 Jul 2016 22:36:40 GMT  
		Size: 1.8 KB (1756 bytes)
	-	`sha256:76333cc4945328a2d994e3b590629e2fd2bfa8f9e82f395816da523fc11ac31f`  
		Last Modified: Fri, 08 Jul 2016 22:36:37 GMT  
		Size: 584.0 B
	-	`sha256:81895367a65f4cdf8f2454d668080dd83c43dadc2f69f6a01ebfe0426be7e13f`  
		Last Modified: Fri, 08 Jul 2016 23:12:54 GMT  
		Size: 326.0 B
	-	`sha256:dceeb874afb26f6b1cd50f1b5b5afdcce69f3b09a61ef2bccbf80a5c7f198d76`  
		Last Modified: Fri, 08 Jul 2016 23:12:56 GMT  
		Size: 4.5 MB (4473999 bytes)
	-	`sha256:b7b129bc1e78347a1544b8c03108d3c67e7e679fe76c85ae852915b6a15059a6`  
		Last Modified: Fri, 08 Jul 2016 23:12:54 GMT  
		Size: 333.0 B
	-	`sha256:65a991c10dcb57bdd0f3a93991780e0309d70fe2a876472e20648ca31372903d`  
		Last Modified: Fri, 08 Jul 2016 23:12:56 GMT  
		Size: 7.6 MB (7611911 bytes)
	-	`sha256:adff62f88fa960539b49ecb3ac3b1a29a92ff6421ded81455f5b545a1c772b21`  
		Last Modified: Fri, 08 Jul 2016 23:12:55 GMT  
		Size: 2.5 KB (2493 bytes)

## `wordpress:latest`

```console
$ docker pull wordpress@sha256:7bb9549fb6d80c230bec2da6bd181be8f30e5199687e53e5ad5744a3144eae1b
```

-	Platforms:
	-	linux; amd64

### `wordpress:latest` - linux; amd64

-	Docker Version: 1.10.3
-	Manifest MIME: `application/vnd.docker.distribution.manifest.v2+json`
-	Total Size: **177.2 MB (177161413 bytes)**  
	(compressed transfer size, not on-disk size)
-	Image ID: `sha256:e3f325718719293c09079bbbb1a2b9bf9053172bc594b5f3acf8d370efe8afae`
-	Entrypoint: `["\/entrypoint.sh"]`
-	Default Command: `["apache2-foreground"]`

```dockerfile
# Thu, 09 Jun 2016 21:28:42 GMT
ADD file:76679eeb94129df23c99013487d6b6bd779d2107bf07d194a524fdbb6a961530 in /
# Thu, 09 Jun 2016 21:28:43 GMT
CMD ["/bin/bash"]
# Fri, 10 Jun 2016 02:34:30 GMT
ENV PHPIZE_DEPS=autoconf 		file 		g++ 		gcc 		libc-dev 		make 		pkg-config 		re2c
# Fri, 10 Jun 2016 02:35:57 GMT
RUN apt-get update && apt-get install -y 		$PHPIZE_DEPS 		ca-certificates 		curl 		libedit2 		libsqlite3-0 		libxml2 	--no-install-recommends && rm -r /var/lib/apt/lists/*
# Fri, 10 Jun 2016 02:35:58 GMT
ENV PHP_INI_DIR=/usr/local/etc/php
# Fri, 10 Jun 2016 02:35:59 GMT
RUN mkdir -p $PHP_INI_DIR/conf.d
# Fri, 10 Jun 2016 02:43:42 GMT
RUN apt-get update && apt-get install -y apache2-bin apache2.2-common --no-install-recommends && rm -rf /var/lib/apt/lists/*
# Thu, 07 Jul 2016 19:23:45 GMT
ENV APACHE_CONFDIR=/etc/apache2
# Thu, 07 Jul 2016 19:23:46 GMT
ENV APACHE_ENVVARS=/etc/apache2/envvars
# Thu, 07 Jul 2016 19:23:48 GMT
RUN set -ex 	&& . "$APACHE_ENVVARS" 	&& for dir in 		"$APACHE_LOCK_DIR" 		"$APACHE_RUN_DIR" 		"$APACHE_LOG_DIR" 		/var/www/html 	; do 		rm -rvf "$dir" 		&& mkdir -p "$dir" 		&& chown -R "$APACHE_RUN_USER:$APACHE_RUN_GROUP" "$dir"; 	done
# Thu, 07 Jul 2016 19:23:49 GMT
RUN a2dismod mpm_event && a2enmod mpm_prefork
# Thu, 07 Jul 2016 19:23:51 GMT
RUN set -ex 	&& . "$APACHE_ENVVARS" 	&& ln -sfT /dev/stderr "$APACHE_LOG_DIR/error.log" 	&& ln -sfT /dev/stdout "$APACHE_LOG_DIR/access.log" 	&& ln -sfT /dev/stdout "$APACHE_LOG_DIR/other_vhosts_access.log"
# Fri, 08 Jul 2016 22:14:00 GMT
RUN { 		echo '<FilesMatch \.php$>'; 		echo '\tSetHandler application/x-httpd-php'; 		echo '</FilesMatch>'; 		echo; 		echo 'DirectoryIndex disabled'; 		echo 'DirectoryIndex index.php index.html'; 		echo; 		echo '<Directory /var/www/>'; 		echo '\tOptions -Indexes'; 		echo '\tAllowOverride All'; 		echo '</Directory>'; 	} | tee "$APACHE_CONFDIR/conf-available/docker-php.conf" 	&& a2enconf docker-php
# Fri, 08 Jul 2016 22:14:01 GMT
ENV PHP_EXTRA_BUILD_DEPS=apache2-dev
# Fri, 08 Jul 2016 22:14:01 GMT
ENV PHP_EXTRA_CONFIGURE_ARGS=--with-apxs2
# Fri, 08 Jul 2016 22:19:29 GMT
ENV GPG_KEYS=0BD78B5F97500D450838F95DFE857D9A90D90EC1 6E4F6AB321FDC07F2C332E3AC2BF0BC433CFC8B3
# Fri, 08 Jul 2016 22:19:30 GMT
ENV PHP_VERSION=5.6.23
# Fri, 08 Jul 2016 22:19:30 GMT
ENV PHP_FILENAME=php-5.6.23.tar.xz
# Fri, 08 Jul 2016 22:19:30 GMT
ENV PHP_SHA256=39141e9a617af172aedbbacee7a63eb15502850f7cea20d759a9cffa7cfb0a1a
# Fri, 08 Jul 2016 22:24:42 GMT
RUN set -xe 	&& buildDeps=" 		$PHP_EXTRA_BUILD_DEPS 		libcurl4-openssl-dev 		libedit-dev 		libsqlite3-dev 		libssl-dev 		libxml2-dev 		xz-utils 	" 	&& apt-get update && apt-get install -y $buildDeps --no-install-recommends && rm -rf /var/lib/apt/lists/* 	&& curl -fSL "http://php.net/get/$PHP_FILENAME/from/this/mirror" -o "$PHP_FILENAME" 	&& echo "$PHP_SHA256 *$PHP_FILENAME" | sha256sum -c - 	&& curl -fSL "http://php.net/get/$PHP_FILENAME.asc/from/this/mirror" -o "$PHP_FILENAME.asc" 	&& export GNUPGHOME="$(mktemp -d)" 	&& for key in $GPG_KEYS; do 		gpg --keyserver ha.pool.sks-keyservers.net --recv-keys "$key"; 	done 	&& gpg --batch --verify "$PHP_FILENAME.asc" "$PHP_FILENAME" 	&& rm -r "$GNUPGHOME" "$PHP_FILENAME.asc" 	&& mkdir -p /usr/src/php 	&& tar -xf "$PHP_FILENAME" -C /usr/src/php --strip-components=1 	&& rm "$PHP_FILENAME" 	&& cd /usr/src/php 	&& ./configure 		--with-config-file-path="$PHP_INI_DIR" 		--with-config-file-scan-dir="$PHP_INI_DIR/conf.d" 		$PHP_EXTRA_CONFIGURE_ARGS 		--disable-cgi 		--enable-mysqlnd 		--enable-mbstring 		--with-curl 		--with-libedit 		--with-openssl 		--with-zlib 	&& make -j"$(nproc)" 	&& make install 	&& { find /usr/local/bin /usr/local/sbin -type f -executable -exec strip --strip-all '{}' + || true; } 	&& make clean 	&& apt-get purge -y --auto-remove -o APT::AutoRemove::RecommendsImportant=false -o APT::AutoRemove::SuggestsImportant=false $buildDeps
# Fri, 08 Jul 2016 22:24:43 GMT
COPY multi:a8819301efc7ce6569bcf183723931153c5b968224bce96498ddbabe72ce7eaa in /usr/local/bin/
# Fri, 08 Jul 2016 22:24:44 GMT
COPY file:3014772111b66da3129ca8caeafdd1dcfa9a3bf518f015ae9acc3c7b9b1b44c9 in /usr/local/bin/
# Fri, 08 Jul 2016 22:24:44 GMT
WORKDIR /var/www/html
# Fri, 08 Jul 2016 22:24:45 GMT
EXPOSE 80/tcp
# Fri, 08 Jul 2016 22:24:45 GMT
CMD ["apache2-foreground"]
# Fri, 08 Jul 2016 23:10:56 GMT
RUN a2enmod rewrite expires
# Fri, 08 Jul 2016 23:12:37 GMT
RUN apt-get update && apt-get install -y libpng12-dev libjpeg-dev && rm -rf /var/lib/apt/lists/* 	&& docker-php-ext-configure gd --with-png-dir=/usr --with-jpeg-dir=/usr 	&& docker-php-ext-install gd mysqli opcache
# Fri, 08 Jul 2016 23:12:39 GMT
RUN { 		echo 'opcache.memory_consumption=128'; 		echo 'opcache.interned_strings_buffer=8'; 		echo 'opcache.max_accelerated_files=4000'; 		echo 'opcache.revalidate_freq=60'; 		echo 'opcache.fast_shutdown=1'; 		echo 'opcache.enable_cli=1'; 	} > /usr/local/etc/php/conf.d/opcache-recommended.ini
# Fri, 08 Jul 2016 23:12:40 GMT
VOLUME [/var/www/html]
# Fri, 08 Jul 2016 23:12:40 GMT
ENV WORDPRESS_VERSION=4.5.3
# Fri, 08 Jul 2016 23:12:41 GMT
ENV WORDPRESS_SHA1=835b68748dae5a9d31c059313cd0150f03a49269
# Fri, 08 Jul 2016 23:12:44 GMT
RUN curl -o wordpress.tar.gz -SL https://wordpress.org/wordpress-${WORDPRESS_VERSION}.tar.gz 	&& echo "$WORDPRESS_SHA1 *wordpress.tar.gz" | sha1sum -c - 	&& tar -xzf wordpress.tar.gz -C /usr/src/ 	&& rm wordpress.tar.gz 	&& chown -R www-data:www-data /usr/src/wordpress
# Fri, 08 Jul 2016 23:12:45 GMT
COPY file:28ccaf78edbf6e7811305e5409bbaa660f9992cad70c071c67cd040bfcb9057e in /entrypoint.sh
# Fri, 08 Jul 2016 23:12:46 GMT
ENTRYPOINT &{["/entrypoint.sh"]}
# Fri, 08 Jul 2016 23:12:46 GMT
CMD ["apache2-foreground"]
```

-	Layers:
	-	`sha256:5c90d4a2d1a8dfffd05ff2dd659923f0ca2d843b5e45d030e17abbcd06a11b5b`  
		Last Modified: Thu, 09 Jun 2016 21:30:47 GMT  
		Size: 51.4 MB (51352535 bytes)
	-	`sha256:357b76a4983822c380125e911928d20bf853d3a4ca869181c757d855408a9c90`  
		Last Modified: Tue, 14 Jun 2016 21:44:40 GMT  
		Size: 77.3 MB (77343405 bytes)
	-	`sha256:0e87614c69f0ba521d6a89ea9b82a5712ff209dfa89e14b1fef8be2056d5680d`  
		Last Modified: Tue, 14 Jun 2016 21:44:12 GMT  
		Size: 180.0 B
	-	`sha256:a3a94d3df9be4137d53c70f13e1bf0e40d300e41c9773a3b5b26d68d75f31797`  
		Last Modified: Tue, 14 Jun 2016 21:44:14 GMT  
		Size: 2.9 MB (2874106 bytes)
	-	`sha256:ac140e12d947b453d23e00fd4099540ef06a9cfec9ac8d0183641b8d301e0f4f`  
		Last Modified: Thu, 07 Jul 2016 19:41:39 GMT  
		Size: 277.0 B
	-	`sha256:e08ee42cd95f62a54fcd329593aa277c5a62fb2fb6bfc8a3103556b23f7a9cd8`  
		Last Modified: Thu, 07 Jul 2016 19:41:39 GMT  
		Size: 430.0 B
	-	`sha256:d4cac1e00ff618b3862877517bb6b85ad52560be5ea79d076c2f670ed7471f34`  
		Last Modified: Thu, 07 Jul 2016 19:41:36 GMT  
		Size: 224.0 B
	-	`sha256:f2749ebafcf639d790352065364892fb26e952ee2c90f41a94b9af3e2a06b6fc`  
		Last Modified: Fri, 08 Jul 2016 22:31:48 GMT  
		Size: 474.0 B
	-	`sha256:b83b18211b0e6523d464cf2237852f82bbc2f6477a2b8a6e27b88a9cdd7c884c`  
		Last Modified: Fri, 08 Jul 2016 22:36:55 GMT  
		Size: 33.5 MB (33498380 bytes)
	-	`sha256:eff2616aae67a23b0fa5482b3a3771e05a0875eae9d3a02c20ced93b155098ab`  
		Last Modified: Fri, 08 Jul 2016 22:36:40 GMT  
		Size: 1.8 KB (1756 bytes)
	-	`sha256:76333cc4945328a2d994e3b590629e2fd2bfa8f9e82f395816da523fc11ac31f`  
		Last Modified: Fri, 08 Jul 2016 22:36:37 GMT  
		Size: 584.0 B
	-	`sha256:81895367a65f4cdf8f2454d668080dd83c43dadc2f69f6a01ebfe0426be7e13f`  
		Last Modified: Fri, 08 Jul 2016 23:12:54 GMT  
		Size: 326.0 B
	-	`sha256:dceeb874afb26f6b1cd50f1b5b5afdcce69f3b09a61ef2bccbf80a5c7f198d76`  
		Last Modified: Fri, 08 Jul 2016 23:12:56 GMT  
		Size: 4.5 MB (4473999 bytes)
	-	`sha256:b7b129bc1e78347a1544b8c03108d3c67e7e679fe76c85ae852915b6a15059a6`  
		Last Modified: Fri, 08 Jul 2016 23:12:54 GMT  
		Size: 333.0 B
	-	`sha256:65a991c10dcb57bdd0f3a93991780e0309d70fe2a876472e20648ca31372903d`  
		Last Modified: Fri, 08 Jul 2016 23:12:56 GMT  
		Size: 7.6 MB (7611911 bytes)
	-	`sha256:adff62f88fa960539b49ecb3ac3b1a29a92ff6421ded81455f5b545a1c772b21`  
		Last Modified: Fri, 08 Jul 2016 23:12:55 GMT  
		Size: 2.5 KB (2493 bytes)

## `wordpress:4.5.3-fpm`

```console
$ docker pull wordpress@sha256:18bd4dba8ccd7daf9dd83965e12f3dfb697d2552379fe88ca19c1c18cb1e06f8
```

-	Platforms:
	-	linux; amd64

### `wordpress:4.5.3-fpm` - linux; amd64

-	Docker Version: 1.10.3
-	Manifest MIME: `application/vnd.docker.distribution.manifest.v2+json`
-	Total Size: **167.3 MB (167292287 bytes)**  
	(compressed transfer size, not on-disk size)
-	Image ID: `sha256:d8f3a1044fef60c2e4757feab64f2247948cf624efbaa8af3a6113087e0fe367`
-	Entrypoint: `["\/entrypoint.sh"]`
-	Default Command: `["php-fpm"]`

```dockerfile
# Thu, 09 Jun 2016 21:28:42 GMT
ADD file:76679eeb94129df23c99013487d6b6bd779d2107bf07d194a524fdbb6a961530 in /
# Thu, 09 Jun 2016 21:28:43 GMT
CMD ["/bin/bash"]
# Fri, 10 Jun 2016 02:34:30 GMT
ENV PHPIZE_DEPS=autoconf 		file 		g++ 		gcc 		libc-dev 		make 		pkg-config 		re2c
# Fri, 10 Jun 2016 02:35:57 GMT
RUN apt-get update && apt-get install -y 		$PHPIZE_DEPS 		ca-certificates 		curl 		libedit2 		libsqlite3-0 		libxml2 	--no-install-recommends && rm -r /var/lib/apt/lists/*
# Fri, 10 Jun 2016 02:35:58 GMT
ENV PHP_INI_DIR=/usr/local/etc/php
# Fri, 10 Jun 2016 02:35:59 GMT
RUN mkdir -p $PHP_INI_DIR/conf.d
# Fri, 10 Jun 2016 02:49:04 GMT
ENV PHP_EXTRA_CONFIGURE_ARGS=--enable-fpm --with-fpm-user=www-data --with-fpm-group=www-data
# Fri, 10 Jun 2016 03:14:30 GMT
ENV GPG_KEYS=0BD78B5F97500D450838F95DFE857D9A90D90EC1 6E4F6AB321FDC07F2C332E3AC2BF0BC433CFC8B3
# Fri, 24 Jun 2016 00:29:15 GMT
ENV PHP_VERSION=5.6.23
# Fri, 24 Jun 2016 00:29:16 GMT
ENV PHP_FILENAME=php-5.6.23.tar.xz
# Fri, 24 Jun 2016 00:29:16 GMT
ENV PHP_SHA256=39141e9a617af172aedbbacee7a63eb15502850f7cea20d759a9cffa7cfb0a1a
# Fri, 24 Jun 2016 00:35:59 GMT
RUN set -xe 	&& buildDeps=" 		$PHP_EXTRA_BUILD_DEPS 		libcurl4-openssl-dev 		libedit-dev 		libsqlite3-dev 		libssl-dev 		libxml2-dev 		xz-utils 	" 	&& apt-get update && apt-get install -y $buildDeps --no-install-recommends && rm -rf /var/lib/apt/lists/* 	&& curl -fSL "http://php.net/get/$PHP_FILENAME/from/this/mirror" -o "$PHP_FILENAME" 	&& echo "$PHP_SHA256 *$PHP_FILENAME" | sha256sum -c - 	&& curl -fSL "http://php.net/get/$PHP_FILENAME.asc/from/this/mirror" -o "$PHP_FILENAME.asc" 	&& export GNUPGHOME="$(mktemp -d)" 	&& for key in $GPG_KEYS; do 		gpg --keyserver ha.pool.sks-keyservers.net --recv-keys "$key"; 	done 	&& gpg --batch --verify "$PHP_FILENAME.asc" "$PHP_FILENAME" 	&& rm -r "$GNUPGHOME" "$PHP_FILENAME.asc" 	&& mkdir -p /usr/src/php 	&& tar -xf "$PHP_FILENAME" -C /usr/src/php --strip-components=1 	&& rm "$PHP_FILENAME" 	&& cd /usr/src/php 	&& ./configure 		--with-config-file-path="$PHP_INI_DIR" 		--with-config-file-scan-dir="$PHP_INI_DIR/conf.d" 		$PHP_EXTRA_CONFIGURE_ARGS 		--disable-cgi 		--enable-mysqlnd 		--enable-mbstring 		--with-curl 		--with-libedit 		--with-openssl 		--with-zlib 	&& make -j"$(nproc)" 	&& make install 	&& { find /usr/local/bin /usr/local/sbin -type f -executable -exec strip --strip-all '{}' + || true; } 	&& make clean 	&& apt-get purge -y --auto-remove -o APT::AutoRemove::RecommendsImportant=false -o APT::AutoRemove::SuggestsImportant=false $buildDeps
# Fri, 24 Jun 2016 00:36:00 GMT
COPY multi:a8819301efc7ce6569bcf183723931153c5b968224bce96498ddbabe72ce7eaa in /usr/local/bin/
# Fri, 24 Jun 2016 00:36:01 GMT
WORKDIR /var/www/html
# Fri, 24 Jun 2016 00:36:02 GMT
RUN set -ex 	&& cd /usr/local/etc 	&& if [ -d php-fpm.d ]; then 		sed 's!=NONE/!=!g' php-fpm.conf.default | tee php-fpm.conf > /dev/null; 		cp php-fpm.d/www.conf.default php-fpm.d/www.conf; 	else 		mkdir php-fpm.d; 		cp php-fpm.conf.default php-fpm.d/www.conf; 		{ 			echo '[global]'; 			echo 'include=etc/php-fpm.d/*.conf'; 		} | tee php-fpm.conf; 	fi 	&& { 		echo '[global]'; 		echo 'error_log = /proc/self/fd/2'; 		echo; 		echo '[www]'; 		echo '; if we send this to /proc/self/fd/1, it never appears'; 		echo 'access.log = /proc/self/fd/2'; 		echo; 		echo 'clear_env = no'; 		echo; 		echo '; Ensure worker stdout and stderr are sent to the main error log.'; 		echo 'catch_workers_output = yes'; 	} | tee php-fpm.d/docker.conf 	&& { 		echo '[global]'; 		echo 'daemonize = no'; 		echo; 		echo '[www]'; 		echo 'listen = [::]:9000'; 	} | tee php-fpm.d/zz-docker.conf
# Fri, 24 Jun 2016 00:36:02 GMT
EXPOSE 9000/tcp
# Fri, 24 Jun 2016 00:36:02 GMT
CMD ["php-fpm"]
# Fri, 24 Jun 2016 02:18:25 GMT
RUN apt-get update && apt-get install -y libpng12-dev libjpeg-dev && rm -rf /var/lib/apt/lists/* 	&& docker-php-ext-configure gd --with-png-dir=/usr --with-jpeg-dir=/usr 	&& docker-php-ext-install gd mysqli opcache
# Fri, 24 Jun 2016 02:18:26 GMT
RUN { 		echo 'opcache.memory_consumption=128'; 		echo 'opcache.interned_strings_buffer=8'; 		echo 'opcache.max_accelerated_files=4000'; 		echo 'opcache.revalidate_freq=60'; 		echo 'opcache.fast_shutdown=1'; 		echo 'opcache.enable_cli=1'; 	} > /usr/local/etc/php/conf.d/opcache-recommended.ini
# Fri, 24 Jun 2016 02:18:27 GMT
VOLUME [/var/www/html]
# Fri, 24 Jun 2016 02:18:27 GMT
ENV WORDPRESS_VERSION=4.5.3
# Fri, 24 Jun 2016 02:18:28 GMT
ENV WORDPRESS_SHA1=835b68748dae5a9d31c059313cd0150f03a49269
# Fri, 24 Jun 2016 02:18:31 GMT
RUN curl -o wordpress.tar.gz -SL https://wordpress.org/wordpress-${WORDPRESS_VERSION}.tar.gz 	&& echo "$WORDPRESS_SHA1 *wordpress.tar.gz" | sha1sum -c - 	&& tar -xzf wordpress.tar.gz -C /usr/src/ 	&& rm wordpress.tar.gz 	&& chown -R www-data:www-data /usr/src/wordpress
# Fri, 24 Jun 2016 02:18:31 GMT
COPY file:28ccaf78edbf6e7811305e5409bbaa660f9992cad70c071c67cd040bfcb9057e in /entrypoint.sh
# Fri, 24 Jun 2016 02:18:32 GMT
ENTRYPOINT &{["/entrypoint.sh"]}
# Fri, 24 Jun 2016 02:18:32 GMT
CMD ["php-fpm"]
```

-	Layers:
	-	`sha256:5c90d4a2d1a8dfffd05ff2dd659923f0ca2d843b5e45d030e17abbcd06a11b5b`  
		Last Modified: Thu, 09 Jun 2016 21:30:47 GMT  
		Size: 51.4 MB (51352535 bytes)
	-	`sha256:357b76a4983822c380125e911928d20bf853d3a4ca869181c757d855408a9c90`  
		Last Modified: Tue, 14 Jun 2016 21:44:40 GMT  
		Size: 77.3 MB (77343405 bytes)
	-	`sha256:0e87614c69f0ba521d6a89ea9b82a5712ff209dfa89e14b1fef8be2056d5680d`  
		Last Modified: Tue, 14 Jun 2016 21:44:12 GMT  
		Size: 180.0 B
	-	`sha256:dca7b62ed238246a5a9fe201c16335c65abec3876ad66a39efa01991739f32e3`  
		Last Modified: Fri, 24 Jun 2016 01:03:34 GMT  
		Size: 26.5 MB (26520348 bytes)
	-	`sha256:5a5345ffe0a9c6653ef129eb8c276dd94885a8dc371f070f3430d59e708df90a`  
		Last Modified: Fri, 24 Jun 2016 01:03:23 GMT  
		Size: 1.8 KB (1755 bytes)
	-	`sha256:41df7d32ab4bc9e57df974c3c0e4646faaf6524fab6ded19c7524aecd9e73e91`  
		Last Modified: Fri, 24 Jun 2016 01:03:23 GMT  
		Size: 127.0 B
	-	`sha256:d051a6853807ad1601ea2f61f37967b7d0d1be26e02f31139fee8c1459f7c3da`  
		Last Modified: Fri, 24 Jun 2016 01:03:23 GMT  
		Size: 7.6 KB (7627 bytes)
	-	`sha256:a47801097c0eff1451a18810c67825a86f3803760acd6ef292c67736f143d211`  
		Last Modified: Fri, 24 Jun 2016 02:19:54 GMT  
		Size: 4.5 MB (4451586 bytes)
	-	`sha256:bc712271ff3fd8bef7e65646be777b3de7b395f5092c6e93945a58f1ebe58e6c`  
		Last Modified: Fri, 24 Jun 2016 02:19:55 GMT  
		Size: 332.0 B
	-	`sha256:da100891911cca941208b09a71d77eaa88f8118402c96cd97c98dd86c90efdbf`  
		Last Modified: Fri, 24 Jun 2016 02:19:55 GMT  
		Size: 7.6 MB (7611900 bytes)
	-	`sha256:8eb8484aa30bc7daed16c079e1f62a999a911115e617293c9c263326d6163e34`  
		Last Modified: Fri, 24 Jun 2016 02:19:53 GMT  
		Size: 2.5 KB (2492 bytes)

## `wordpress:4.5-fpm`

```console
$ docker pull wordpress@sha256:18bd4dba8ccd7daf9dd83965e12f3dfb697d2552379fe88ca19c1c18cb1e06f8
```

-	Platforms:
	-	linux; amd64

### `wordpress:4.5-fpm` - linux; amd64

-	Docker Version: 1.10.3
-	Manifest MIME: `application/vnd.docker.distribution.manifest.v2+json`
-	Total Size: **167.3 MB (167292287 bytes)**  
	(compressed transfer size, not on-disk size)
-	Image ID: `sha256:d8f3a1044fef60c2e4757feab64f2247948cf624efbaa8af3a6113087e0fe367`
-	Entrypoint: `["\/entrypoint.sh"]`
-	Default Command: `["php-fpm"]`

```dockerfile
# Thu, 09 Jun 2016 21:28:42 GMT
ADD file:76679eeb94129df23c99013487d6b6bd779d2107bf07d194a524fdbb6a961530 in /
# Thu, 09 Jun 2016 21:28:43 GMT
CMD ["/bin/bash"]
# Fri, 10 Jun 2016 02:34:30 GMT
ENV PHPIZE_DEPS=autoconf 		file 		g++ 		gcc 		libc-dev 		make 		pkg-config 		re2c
# Fri, 10 Jun 2016 02:35:57 GMT
RUN apt-get update && apt-get install -y 		$PHPIZE_DEPS 		ca-certificates 		curl 		libedit2 		libsqlite3-0 		libxml2 	--no-install-recommends && rm -r /var/lib/apt/lists/*
# Fri, 10 Jun 2016 02:35:58 GMT
ENV PHP_INI_DIR=/usr/local/etc/php
# Fri, 10 Jun 2016 02:35:59 GMT
RUN mkdir -p $PHP_INI_DIR/conf.d
# Fri, 10 Jun 2016 02:49:04 GMT
ENV PHP_EXTRA_CONFIGURE_ARGS=--enable-fpm --with-fpm-user=www-data --with-fpm-group=www-data
# Fri, 10 Jun 2016 03:14:30 GMT
ENV GPG_KEYS=0BD78B5F97500D450838F95DFE857D9A90D90EC1 6E4F6AB321FDC07F2C332E3AC2BF0BC433CFC8B3
# Fri, 24 Jun 2016 00:29:15 GMT
ENV PHP_VERSION=5.6.23
# Fri, 24 Jun 2016 00:29:16 GMT
ENV PHP_FILENAME=php-5.6.23.tar.xz
# Fri, 24 Jun 2016 00:29:16 GMT
ENV PHP_SHA256=39141e9a617af172aedbbacee7a63eb15502850f7cea20d759a9cffa7cfb0a1a
# Fri, 24 Jun 2016 00:35:59 GMT
RUN set -xe 	&& buildDeps=" 		$PHP_EXTRA_BUILD_DEPS 		libcurl4-openssl-dev 		libedit-dev 		libsqlite3-dev 		libssl-dev 		libxml2-dev 		xz-utils 	" 	&& apt-get update && apt-get install -y $buildDeps --no-install-recommends && rm -rf /var/lib/apt/lists/* 	&& curl -fSL "http://php.net/get/$PHP_FILENAME/from/this/mirror" -o "$PHP_FILENAME" 	&& echo "$PHP_SHA256 *$PHP_FILENAME" | sha256sum -c - 	&& curl -fSL "http://php.net/get/$PHP_FILENAME.asc/from/this/mirror" -o "$PHP_FILENAME.asc" 	&& export GNUPGHOME="$(mktemp -d)" 	&& for key in $GPG_KEYS; do 		gpg --keyserver ha.pool.sks-keyservers.net --recv-keys "$key"; 	done 	&& gpg --batch --verify "$PHP_FILENAME.asc" "$PHP_FILENAME" 	&& rm -r "$GNUPGHOME" "$PHP_FILENAME.asc" 	&& mkdir -p /usr/src/php 	&& tar -xf "$PHP_FILENAME" -C /usr/src/php --strip-components=1 	&& rm "$PHP_FILENAME" 	&& cd /usr/src/php 	&& ./configure 		--with-config-file-path="$PHP_INI_DIR" 		--with-config-file-scan-dir="$PHP_INI_DIR/conf.d" 		$PHP_EXTRA_CONFIGURE_ARGS 		--disable-cgi 		--enable-mysqlnd 		--enable-mbstring 		--with-curl 		--with-libedit 		--with-openssl 		--with-zlib 	&& make -j"$(nproc)" 	&& make install 	&& { find /usr/local/bin /usr/local/sbin -type f -executable -exec strip --strip-all '{}' + || true; } 	&& make clean 	&& apt-get purge -y --auto-remove -o APT::AutoRemove::RecommendsImportant=false -o APT::AutoRemove::SuggestsImportant=false $buildDeps
# Fri, 24 Jun 2016 00:36:00 GMT
COPY multi:a8819301efc7ce6569bcf183723931153c5b968224bce96498ddbabe72ce7eaa in /usr/local/bin/
# Fri, 24 Jun 2016 00:36:01 GMT
WORKDIR /var/www/html
# Fri, 24 Jun 2016 00:36:02 GMT
RUN set -ex 	&& cd /usr/local/etc 	&& if [ -d php-fpm.d ]; then 		sed 's!=NONE/!=!g' php-fpm.conf.default | tee php-fpm.conf > /dev/null; 		cp php-fpm.d/www.conf.default php-fpm.d/www.conf; 	else 		mkdir php-fpm.d; 		cp php-fpm.conf.default php-fpm.d/www.conf; 		{ 			echo '[global]'; 			echo 'include=etc/php-fpm.d/*.conf'; 		} | tee php-fpm.conf; 	fi 	&& { 		echo '[global]'; 		echo 'error_log = /proc/self/fd/2'; 		echo; 		echo '[www]'; 		echo '; if we send this to /proc/self/fd/1, it never appears'; 		echo 'access.log = /proc/self/fd/2'; 		echo; 		echo 'clear_env = no'; 		echo; 		echo '; Ensure worker stdout and stderr are sent to the main error log.'; 		echo 'catch_workers_output = yes'; 	} | tee php-fpm.d/docker.conf 	&& { 		echo '[global]'; 		echo 'daemonize = no'; 		echo; 		echo '[www]'; 		echo 'listen = [::]:9000'; 	} | tee php-fpm.d/zz-docker.conf
# Fri, 24 Jun 2016 00:36:02 GMT
EXPOSE 9000/tcp
# Fri, 24 Jun 2016 00:36:02 GMT
CMD ["php-fpm"]
# Fri, 24 Jun 2016 02:18:25 GMT
RUN apt-get update && apt-get install -y libpng12-dev libjpeg-dev && rm -rf /var/lib/apt/lists/* 	&& docker-php-ext-configure gd --with-png-dir=/usr --with-jpeg-dir=/usr 	&& docker-php-ext-install gd mysqli opcache
# Fri, 24 Jun 2016 02:18:26 GMT
RUN { 		echo 'opcache.memory_consumption=128'; 		echo 'opcache.interned_strings_buffer=8'; 		echo 'opcache.max_accelerated_files=4000'; 		echo 'opcache.revalidate_freq=60'; 		echo 'opcache.fast_shutdown=1'; 		echo 'opcache.enable_cli=1'; 	} > /usr/local/etc/php/conf.d/opcache-recommended.ini
# Fri, 24 Jun 2016 02:18:27 GMT
VOLUME [/var/www/html]
# Fri, 24 Jun 2016 02:18:27 GMT
ENV WORDPRESS_VERSION=4.5.3
# Fri, 24 Jun 2016 02:18:28 GMT
ENV WORDPRESS_SHA1=835b68748dae5a9d31c059313cd0150f03a49269
# Fri, 24 Jun 2016 02:18:31 GMT
RUN curl -o wordpress.tar.gz -SL https://wordpress.org/wordpress-${WORDPRESS_VERSION}.tar.gz 	&& echo "$WORDPRESS_SHA1 *wordpress.tar.gz" | sha1sum -c - 	&& tar -xzf wordpress.tar.gz -C /usr/src/ 	&& rm wordpress.tar.gz 	&& chown -R www-data:www-data /usr/src/wordpress
# Fri, 24 Jun 2016 02:18:31 GMT
COPY file:28ccaf78edbf6e7811305e5409bbaa660f9992cad70c071c67cd040bfcb9057e in /entrypoint.sh
# Fri, 24 Jun 2016 02:18:32 GMT
ENTRYPOINT &{["/entrypoint.sh"]}
# Fri, 24 Jun 2016 02:18:32 GMT
CMD ["php-fpm"]
```

-	Layers:
	-	`sha256:5c90d4a2d1a8dfffd05ff2dd659923f0ca2d843b5e45d030e17abbcd06a11b5b`  
		Last Modified: Thu, 09 Jun 2016 21:30:47 GMT  
		Size: 51.4 MB (51352535 bytes)
	-	`sha256:357b76a4983822c380125e911928d20bf853d3a4ca869181c757d855408a9c90`  
		Last Modified: Tue, 14 Jun 2016 21:44:40 GMT  
		Size: 77.3 MB (77343405 bytes)
	-	`sha256:0e87614c69f0ba521d6a89ea9b82a5712ff209dfa89e14b1fef8be2056d5680d`  
		Last Modified: Tue, 14 Jun 2016 21:44:12 GMT  
		Size: 180.0 B
	-	`sha256:dca7b62ed238246a5a9fe201c16335c65abec3876ad66a39efa01991739f32e3`  
		Last Modified: Fri, 24 Jun 2016 01:03:34 GMT  
		Size: 26.5 MB (26520348 bytes)
	-	`sha256:5a5345ffe0a9c6653ef129eb8c276dd94885a8dc371f070f3430d59e708df90a`  
		Last Modified: Fri, 24 Jun 2016 01:03:23 GMT  
		Size: 1.8 KB (1755 bytes)
	-	`sha256:41df7d32ab4bc9e57df974c3c0e4646faaf6524fab6ded19c7524aecd9e73e91`  
		Last Modified: Fri, 24 Jun 2016 01:03:23 GMT  
		Size: 127.0 B
	-	`sha256:d051a6853807ad1601ea2f61f37967b7d0d1be26e02f31139fee8c1459f7c3da`  
		Last Modified: Fri, 24 Jun 2016 01:03:23 GMT  
		Size: 7.6 KB (7627 bytes)
	-	`sha256:a47801097c0eff1451a18810c67825a86f3803760acd6ef292c67736f143d211`  
		Last Modified: Fri, 24 Jun 2016 02:19:54 GMT  
		Size: 4.5 MB (4451586 bytes)
	-	`sha256:bc712271ff3fd8bef7e65646be777b3de7b395f5092c6e93945a58f1ebe58e6c`  
		Last Modified: Fri, 24 Jun 2016 02:19:55 GMT  
		Size: 332.0 B
	-	`sha256:da100891911cca941208b09a71d77eaa88f8118402c96cd97c98dd86c90efdbf`  
		Last Modified: Fri, 24 Jun 2016 02:19:55 GMT  
		Size: 7.6 MB (7611900 bytes)
	-	`sha256:8eb8484aa30bc7daed16c079e1f62a999a911115e617293c9c263326d6163e34`  
		Last Modified: Fri, 24 Jun 2016 02:19:53 GMT  
		Size: 2.5 KB (2492 bytes)

## `wordpress:4-fpm`

```console
$ docker pull wordpress@sha256:18bd4dba8ccd7daf9dd83965e12f3dfb697d2552379fe88ca19c1c18cb1e06f8
```

-	Platforms:
	-	linux; amd64

### `wordpress:4-fpm` - linux; amd64

-	Docker Version: 1.10.3
-	Manifest MIME: `application/vnd.docker.distribution.manifest.v2+json`
-	Total Size: **167.3 MB (167292287 bytes)**  
	(compressed transfer size, not on-disk size)
-	Image ID: `sha256:d8f3a1044fef60c2e4757feab64f2247948cf624efbaa8af3a6113087e0fe367`
-	Entrypoint: `["\/entrypoint.sh"]`
-	Default Command: `["php-fpm"]`

```dockerfile
# Thu, 09 Jun 2016 21:28:42 GMT
ADD file:76679eeb94129df23c99013487d6b6bd779d2107bf07d194a524fdbb6a961530 in /
# Thu, 09 Jun 2016 21:28:43 GMT
CMD ["/bin/bash"]
# Fri, 10 Jun 2016 02:34:30 GMT
ENV PHPIZE_DEPS=autoconf 		file 		g++ 		gcc 		libc-dev 		make 		pkg-config 		re2c
# Fri, 10 Jun 2016 02:35:57 GMT
RUN apt-get update && apt-get install -y 		$PHPIZE_DEPS 		ca-certificates 		curl 		libedit2 		libsqlite3-0 		libxml2 	--no-install-recommends && rm -r /var/lib/apt/lists/*
# Fri, 10 Jun 2016 02:35:58 GMT
ENV PHP_INI_DIR=/usr/local/etc/php
# Fri, 10 Jun 2016 02:35:59 GMT
RUN mkdir -p $PHP_INI_DIR/conf.d
# Fri, 10 Jun 2016 02:49:04 GMT
ENV PHP_EXTRA_CONFIGURE_ARGS=--enable-fpm --with-fpm-user=www-data --with-fpm-group=www-data
# Fri, 10 Jun 2016 03:14:30 GMT
ENV GPG_KEYS=0BD78B5F97500D450838F95DFE857D9A90D90EC1 6E4F6AB321FDC07F2C332E3AC2BF0BC433CFC8B3
# Fri, 24 Jun 2016 00:29:15 GMT
ENV PHP_VERSION=5.6.23
# Fri, 24 Jun 2016 00:29:16 GMT
ENV PHP_FILENAME=php-5.6.23.tar.xz
# Fri, 24 Jun 2016 00:29:16 GMT
ENV PHP_SHA256=39141e9a617af172aedbbacee7a63eb15502850f7cea20d759a9cffa7cfb0a1a
# Fri, 24 Jun 2016 00:35:59 GMT
RUN set -xe 	&& buildDeps=" 		$PHP_EXTRA_BUILD_DEPS 		libcurl4-openssl-dev 		libedit-dev 		libsqlite3-dev 		libssl-dev 		libxml2-dev 		xz-utils 	" 	&& apt-get update && apt-get install -y $buildDeps --no-install-recommends && rm -rf /var/lib/apt/lists/* 	&& curl -fSL "http://php.net/get/$PHP_FILENAME/from/this/mirror" -o "$PHP_FILENAME" 	&& echo "$PHP_SHA256 *$PHP_FILENAME" | sha256sum -c - 	&& curl -fSL "http://php.net/get/$PHP_FILENAME.asc/from/this/mirror" -o "$PHP_FILENAME.asc" 	&& export GNUPGHOME="$(mktemp -d)" 	&& for key in $GPG_KEYS; do 		gpg --keyserver ha.pool.sks-keyservers.net --recv-keys "$key"; 	done 	&& gpg --batch --verify "$PHP_FILENAME.asc" "$PHP_FILENAME" 	&& rm -r "$GNUPGHOME" "$PHP_FILENAME.asc" 	&& mkdir -p /usr/src/php 	&& tar -xf "$PHP_FILENAME" -C /usr/src/php --strip-components=1 	&& rm "$PHP_FILENAME" 	&& cd /usr/src/php 	&& ./configure 		--with-config-file-path="$PHP_INI_DIR" 		--with-config-file-scan-dir="$PHP_INI_DIR/conf.d" 		$PHP_EXTRA_CONFIGURE_ARGS 		--disable-cgi 		--enable-mysqlnd 		--enable-mbstring 		--with-curl 		--with-libedit 		--with-openssl 		--with-zlib 	&& make -j"$(nproc)" 	&& make install 	&& { find /usr/local/bin /usr/local/sbin -type f -executable -exec strip --strip-all '{}' + || true; } 	&& make clean 	&& apt-get purge -y --auto-remove -o APT::AutoRemove::RecommendsImportant=false -o APT::AutoRemove::SuggestsImportant=false $buildDeps
# Fri, 24 Jun 2016 00:36:00 GMT
COPY multi:a8819301efc7ce6569bcf183723931153c5b968224bce96498ddbabe72ce7eaa in /usr/local/bin/
# Fri, 24 Jun 2016 00:36:01 GMT
WORKDIR /var/www/html
# Fri, 24 Jun 2016 00:36:02 GMT
RUN set -ex 	&& cd /usr/local/etc 	&& if [ -d php-fpm.d ]; then 		sed 's!=NONE/!=!g' php-fpm.conf.default | tee php-fpm.conf > /dev/null; 		cp php-fpm.d/www.conf.default php-fpm.d/www.conf; 	else 		mkdir php-fpm.d; 		cp php-fpm.conf.default php-fpm.d/www.conf; 		{ 			echo '[global]'; 			echo 'include=etc/php-fpm.d/*.conf'; 		} | tee php-fpm.conf; 	fi 	&& { 		echo '[global]'; 		echo 'error_log = /proc/self/fd/2'; 		echo; 		echo '[www]'; 		echo '; if we send this to /proc/self/fd/1, it never appears'; 		echo 'access.log = /proc/self/fd/2'; 		echo; 		echo 'clear_env = no'; 		echo; 		echo '; Ensure worker stdout and stderr are sent to the main error log.'; 		echo 'catch_workers_output = yes'; 	} | tee php-fpm.d/docker.conf 	&& { 		echo '[global]'; 		echo 'daemonize = no'; 		echo; 		echo '[www]'; 		echo 'listen = [::]:9000'; 	} | tee php-fpm.d/zz-docker.conf
# Fri, 24 Jun 2016 00:36:02 GMT
EXPOSE 9000/tcp
# Fri, 24 Jun 2016 00:36:02 GMT
CMD ["php-fpm"]
# Fri, 24 Jun 2016 02:18:25 GMT
RUN apt-get update && apt-get install -y libpng12-dev libjpeg-dev && rm -rf /var/lib/apt/lists/* 	&& docker-php-ext-configure gd --with-png-dir=/usr --with-jpeg-dir=/usr 	&& docker-php-ext-install gd mysqli opcache
# Fri, 24 Jun 2016 02:18:26 GMT
RUN { 		echo 'opcache.memory_consumption=128'; 		echo 'opcache.interned_strings_buffer=8'; 		echo 'opcache.max_accelerated_files=4000'; 		echo 'opcache.revalidate_freq=60'; 		echo 'opcache.fast_shutdown=1'; 		echo 'opcache.enable_cli=1'; 	} > /usr/local/etc/php/conf.d/opcache-recommended.ini
# Fri, 24 Jun 2016 02:18:27 GMT
VOLUME [/var/www/html]
# Fri, 24 Jun 2016 02:18:27 GMT
ENV WORDPRESS_VERSION=4.5.3
# Fri, 24 Jun 2016 02:18:28 GMT
ENV WORDPRESS_SHA1=835b68748dae5a9d31c059313cd0150f03a49269
# Fri, 24 Jun 2016 02:18:31 GMT
RUN curl -o wordpress.tar.gz -SL https://wordpress.org/wordpress-${WORDPRESS_VERSION}.tar.gz 	&& echo "$WORDPRESS_SHA1 *wordpress.tar.gz" | sha1sum -c - 	&& tar -xzf wordpress.tar.gz -C /usr/src/ 	&& rm wordpress.tar.gz 	&& chown -R www-data:www-data /usr/src/wordpress
# Fri, 24 Jun 2016 02:18:31 GMT
COPY file:28ccaf78edbf6e7811305e5409bbaa660f9992cad70c071c67cd040bfcb9057e in /entrypoint.sh
# Fri, 24 Jun 2016 02:18:32 GMT
ENTRYPOINT &{["/entrypoint.sh"]}
# Fri, 24 Jun 2016 02:18:32 GMT
CMD ["php-fpm"]
```

-	Layers:
	-	`sha256:5c90d4a2d1a8dfffd05ff2dd659923f0ca2d843b5e45d030e17abbcd06a11b5b`  
		Last Modified: Thu, 09 Jun 2016 21:30:47 GMT  
		Size: 51.4 MB (51352535 bytes)
	-	`sha256:357b76a4983822c380125e911928d20bf853d3a4ca869181c757d855408a9c90`  
		Last Modified: Tue, 14 Jun 2016 21:44:40 GMT  
		Size: 77.3 MB (77343405 bytes)
	-	`sha256:0e87614c69f0ba521d6a89ea9b82a5712ff209dfa89e14b1fef8be2056d5680d`  
		Last Modified: Tue, 14 Jun 2016 21:44:12 GMT  
		Size: 180.0 B
	-	`sha256:dca7b62ed238246a5a9fe201c16335c65abec3876ad66a39efa01991739f32e3`  
		Last Modified: Fri, 24 Jun 2016 01:03:34 GMT  
		Size: 26.5 MB (26520348 bytes)
	-	`sha256:5a5345ffe0a9c6653ef129eb8c276dd94885a8dc371f070f3430d59e708df90a`  
		Last Modified: Fri, 24 Jun 2016 01:03:23 GMT  
		Size: 1.8 KB (1755 bytes)
	-	`sha256:41df7d32ab4bc9e57df974c3c0e4646faaf6524fab6ded19c7524aecd9e73e91`  
		Last Modified: Fri, 24 Jun 2016 01:03:23 GMT  
		Size: 127.0 B
	-	`sha256:d051a6853807ad1601ea2f61f37967b7d0d1be26e02f31139fee8c1459f7c3da`  
		Last Modified: Fri, 24 Jun 2016 01:03:23 GMT  
		Size: 7.6 KB (7627 bytes)
	-	`sha256:a47801097c0eff1451a18810c67825a86f3803760acd6ef292c67736f143d211`  
		Last Modified: Fri, 24 Jun 2016 02:19:54 GMT  
		Size: 4.5 MB (4451586 bytes)
	-	`sha256:bc712271ff3fd8bef7e65646be777b3de7b395f5092c6e93945a58f1ebe58e6c`  
		Last Modified: Fri, 24 Jun 2016 02:19:55 GMT  
		Size: 332.0 B
	-	`sha256:da100891911cca941208b09a71d77eaa88f8118402c96cd97c98dd86c90efdbf`  
		Last Modified: Fri, 24 Jun 2016 02:19:55 GMT  
		Size: 7.6 MB (7611900 bytes)
	-	`sha256:8eb8484aa30bc7daed16c079e1f62a999a911115e617293c9c263326d6163e34`  
		Last Modified: Fri, 24 Jun 2016 02:19:53 GMT  
		Size: 2.5 KB (2492 bytes)

## `wordpress:fpm`

```console
$ docker pull wordpress@sha256:18bd4dba8ccd7daf9dd83965e12f3dfb697d2552379fe88ca19c1c18cb1e06f8
```

-	Platforms:
	-	linux; amd64

### `wordpress:fpm` - linux; amd64

-	Docker Version: 1.10.3
-	Manifest MIME: `application/vnd.docker.distribution.manifest.v2+json`
-	Total Size: **167.3 MB (167292287 bytes)**  
	(compressed transfer size, not on-disk size)
-	Image ID: `sha256:d8f3a1044fef60c2e4757feab64f2247948cf624efbaa8af3a6113087e0fe367`
-	Entrypoint: `["\/entrypoint.sh"]`
-	Default Command: `["php-fpm"]`

```dockerfile
# Thu, 09 Jun 2016 21:28:42 GMT
ADD file:76679eeb94129df23c99013487d6b6bd779d2107bf07d194a524fdbb6a961530 in /
# Thu, 09 Jun 2016 21:28:43 GMT
CMD ["/bin/bash"]
# Fri, 10 Jun 2016 02:34:30 GMT
ENV PHPIZE_DEPS=autoconf 		file 		g++ 		gcc 		libc-dev 		make 		pkg-config 		re2c
# Fri, 10 Jun 2016 02:35:57 GMT
RUN apt-get update && apt-get install -y 		$PHPIZE_DEPS 		ca-certificates 		curl 		libedit2 		libsqlite3-0 		libxml2 	--no-install-recommends && rm -r /var/lib/apt/lists/*
# Fri, 10 Jun 2016 02:35:58 GMT
ENV PHP_INI_DIR=/usr/local/etc/php
# Fri, 10 Jun 2016 02:35:59 GMT
RUN mkdir -p $PHP_INI_DIR/conf.d
# Fri, 10 Jun 2016 02:49:04 GMT
ENV PHP_EXTRA_CONFIGURE_ARGS=--enable-fpm --with-fpm-user=www-data --with-fpm-group=www-data
# Fri, 10 Jun 2016 03:14:30 GMT
ENV GPG_KEYS=0BD78B5F97500D450838F95DFE857D9A90D90EC1 6E4F6AB321FDC07F2C332E3AC2BF0BC433CFC8B3
# Fri, 24 Jun 2016 00:29:15 GMT
ENV PHP_VERSION=5.6.23
# Fri, 24 Jun 2016 00:29:16 GMT
ENV PHP_FILENAME=php-5.6.23.tar.xz
# Fri, 24 Jun 2016 00:29:16 GMT
ENV PHP_SHA256=39141e9a617af172aedbbacee7a63eb15502850f7cea20d759a9cffa7cfb0a1a
# Fri, 24 Jun 2016 00:35:59 GMT
RUN set -xe 	&& buildDeps=" 		$PHP_EXTRA_BUILD_DEPS 		libcurl4-openssl-dev 		libedit-dev 		libsqlite3-dev 		libssl-dev 		libxml2-dev 		xz-utils 	" 	&& apt-get update && apt-get install -y $buildDeps --no-install-recommends && rm -rf /var/lib/apt/lists/* 	&& curl -fSL "http://php.net/get/$PHP_FILENAME/from/this/mirror" -o "$PHP_FILENAME" 	&& echo "$PHP_SHA256 *$PHP_FILENAME" | sha256sum -c - 	&& curl -fSL "http://php.net/get/$PHP_FILENAME.asc/from/this/mirror" -o "$PHP_FILENAME.asc" 	&& export GNUPGHOME="$(mktemp -d)" 	&& for key in $GPG_KEYS; do 		gpg --keyserver ha.pool.sks-keyservers.net --recv-keys "$key"; 	done 	&& gpg --batch --verify "$PHP_FILENAME.asc" "$PHP_FILENAME" 	&& rm -r "$GNUPGHOME" "$PHP_FILENAME.asc" 	&& mkdir -p /usr/src/php 	&& tar -xf "$PHP_FILENAME" -C /usr/src/php --strip-components=1 	&& rm "$PHP_FILENAME" 	&& cd /usr/src/php 	&& ./configure 		--with-config-file-path="$PHP_INI_DIR" 		--with-config-file-scan-dir="$PHP_INI_DIR/conf.d" 		$PHP_EXTRA_CONFIGURE_ARGS 		--disable-cgi 		--enable-mysqlnd 		--enable-mbstring 		--with-curl 		--with-libedit 		--with-openssl 		--with-zlib 	&& make -j"$(nproc)" 	&& make install 	&& { find /usr/local/bin /usr/local/sbin -type f -executable -exec strip --strip-all '{}' + || true; } 	&& make clean 	&& apt-get purge -y --auto-remove -o APT::AutoRemove::RecommendsImportant=false -o APT::AutoRemove::SuggestsImportant=false $buildDeps
# Fri, 24 Jun 2016 00:36:00 GMT
COPY multi:a8819301efc7ce6569bcf183723931153c5b968224bce96498ddbabe72ce7eaa in /usr/local/bin/
# Fri, 24 Jun 2016 00:36:01 GMT
WORKDIR /var/www/html
# Fri, 24 Jun 2016 00:36:02 GMT
RUN set -ex 	&& cd /usr/local/etc 	&& if [ -d php-fpm.d ]; then 		sed 's!=NONE/!=!g' php-fpm.conf.default | tee php-fpm.conf > /dev/null; 		cp php-fpm.d/www.conf.default php-fpm.d/www.conf; 	else 		mkdir php-fpm.d; 		cp php-fpm.conf.default php-fpm.d/www.conf; 		{ 			echo '[global]'; 			echo 'include=etc/php-fpm.d/*.conf'; 		} | tee php-fpm.conf; 	fi 	&& { 		echo '[global]'; 		echo 'error_log = /proc/self/fd/2'; 		echo; 		echo '[www]'; 		echo '; if we send this to /proc/self/fd/1, it never appears'; 		echo 'access.log = /proc/self/fd/2'; 		echo; 		echo 'clear_env = no'; 		echo; 		echo '; Ensure worker stdout and stderr are sent to the main error log.'; 		echo 'catch_workers_output = yes'; 	} | tee php-fpm.d/docker.conf 	&& { 		echo '[global]'; 		echo 'daemonize = no'; 		echo; 		echo '[www]'; 		echo 'listen = [::]:9000'; 	} | tee php-fpm.d/zz-docker.conf
# Fri, 24 Jun 2016 00:36:02 GMT
EXPOSE 9000/tcp
# Fri, 24 Jun 2016 00:36:02 GMT
CMD ["php-fpm"]
# Fri, 24 Jun 2016 02:18:25 GMT
RUN apt-get update && apt-get install -y libpng12-dev libjpeg-dev && rm -rf /var/lib/apt/lists/* 	&& docker-php-ext-configure gd --with-png-dir=/usr --with-jpeg-dir=/usr 	&& docker-php-ext-install gd mysqli opcache
# Fri, 24 Jun 2016 02:18:26 GMT
RUN { 		echo 'opcache.memory_consumption=128'; 		echo 'opcache.interned_strings_buffer=8'; 		echo 'opcache.max_accelerated_files=4000'; 		echo 'opcache.revalidate_freq=60'; 		echo 'opcache.fast_shutdown=1'; 		echo 'opcache.enable_cli=1'; 	} > /usr/local/etc/php/conf.d/opcache-recommended.ini
# Fri, 24 Jun 2016 02:18:27 GMT
VOLUME [/var/www/html]
# Fri, 24 Jun 2016 02:18:27 GMT
ENV WORDPRESS_VERSION=4.5.3
# Fri, 24 Jun 2016 02:18:28 GMT
ENV WORDPRESS_SHA1=835b68748dae5a9d31c059313cd0150f03a49269
# Fri, 24 Jun 2016 02:18:31 GMT
RUN curl -o wordpress.tar.gz -SL https://wordpress.org/wordpress-${WORDPRESS_VERSION}.tar.gz 	&& echo "$WORDPRESS_SHA1 *wordpress.tar.gz" | sha1sum -c - 	&& tar -xzf wordpress.tar.gz -C /usr/src/ 	&& rm wordpress.tar.gz 	&& chown -R www-data:www-data /usr/src/wordpress
# Fri, 24 Jun 2016 02:18:31 GMT
COPY file:28ccaf78edbf6e7811305e5409bbaa660f9992cad70c071c67cd040bfcb9057e in /entrypoint.sh
# Fri, 24 Jun 2016 02:18:32 GMT
ENTRYPOINT &{["/entrypoint.sh"]}
# Fri, 24 Jun 2016 02:18:32 GMT
CMD ["php-fpm"]
```

-	Layers:
	-	`sha256:5c90d4a2d1a8dfffd05ff2dd659923f0ca2d843b5e45d030e17abbcd06a11b5b`  
		Last Modified: Thu, 09 Jun 2016 21:30:47 GMT  
		Size: 51.4 MB (51352535 bytes)
	-	`sha256:357b76a4983822c380125e911928d20bf853d3a4ca869181c757d855408a9c90`  
		Last Modified: Tue, 14 Jun 2016 21:44:40 GMT  
		Size: 77.3 MB (77343405 bytes)
	-	`sha256:0e87614c69f0ba521d6a89ea9b82a5712ff209dfa89e14b1fef8be2056d5680d`  
		Last Modified: Tue, 14 Jun 2016 21:44:12 GMT  
		Size: 180.0 B
	-	`sha256:dca7b62ed238246a5a9fe201c16335c65abec3876ad66a39efa01991739f32e3`  
		Last Modified: Fri, 24 Jun 2016 01:03:34 GMT  
		Size: 26.5 MB (26520348 bytes)
	-	`sha256:5a5345ffe0a9c6653ef129eb8c276dd94885a8dc371f070f3430d59e708df90a`  
		Last Modified: Fri, 24 Jun 2016 01:03:23 GMT  
		Size: 1.8 KB (1755 bytes)
	-	`sha256:41df7d32ab4bc9e57df974c3c0e4646faaf6524fab6ded19c7524aecd9e73e91`  
		Last Modified: Fri, 24 Jun 2016 01:03:23 GMT  
		Size: 127.0 B
	-	`sha256:d051a6853807ad1601ea2f61f37967b7d0d1be26e02f31139fee8c1459f7c3da`  
		Last Modified: Fri, 24 Jun 2016 01:03:23 GMT  
		Size: 7.6 KB (7627 bytes)
	-	`sha256:a47801097c0eff1451a18810c67825a86f3803760acd6ef292c67736f143d211`  
		Last Modified: Fri, 24 Jun 2016 02:19:54 GMT  
		Size: 4.5 MB (4451586 bytes)
	-	`sha256:bc712271ff3fd8bef7e65646be777b3de7b395f5092c6e93945a58f1ebe58e6c`  
		Last Modified: Fri, 24 Jun 2016 02:19:55 GMT  
		Size: 332.0 B
	-	`sha256:da100891911cca941208b09a71d77eaa88f8118402c96cd97c98dd86c90efdbf`  
		Last Modified: Fri, 24 Jun 2016 02:19:55 GMT  
		Size: 7.6 MB (7611900 bytes)
	-	`sha256:8eb8484aa30bc7daed16c079e1f62a999a911115e617293c9c263326d6163e34`  
		Last Modified: Fri, 24 Jun 2016 02:19:53 GMT  
		Size: 2.5 KB (2492 bytes)
