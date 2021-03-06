<!-- THIS FILE IS GENERATED VIA '.template-helpers/generate-tag-details.pl' -->

# Tags of `aerospike`

-	[`aerospike:3.8.4`](#aerospike384)
-	[`aerospike:latest`](#aerospikelatest)

## `aerospike:3.8.4`

```console
$ docker pull aerospike@sha256:55c3aa7cadce113562a5c7b57a6717ea1745a5756b5bd31cbda90b6e3a352c13
```

-	Platforms:
	-	linux; amd64

### `aerospike:3.8.4` - linux; amd64

-	Docker Version: 1.10.3
-	Manifest MIME: `application/vnd.docker.distribution.manifest.v2+json`
-	Total Size: **60.0 MB (59972861 bytes)**  
	(compressed transfer size, not on-disk size)
-	Image ID: `sha256:9e749e98506f0fbe5be4fc25e96c4ecf88485dbadbef86411b9a1f11f4352abc`
-	Entrypoint: `["\/entrypoint.sh"]`
-	Default Command: `["asd"]`

```dockerfile
# Fri, 08 Jul 2016 18:39:36 GMT
ADD file:49ae6eed5178a2866c5023c4e7a9ae303f4828a5586569106aff27a8ce9cadf6 in /
# Fri, 08 Jul 2016 18:39:39 GMT
RUN set -xe 		&& echo '#!/bin/sh' > /usr/sbin/policy-rc.d 	&& echo 'exit 101' >> /usr/sbin/policy-rc.d 	&& chmod +x /usr/sbin/policy-rc.d 		&& dpkg-divert --local --rename --add /sbin/initctl 	&& cp -a /usr/sbin/policy-rc.d /sbin/initctl 	&& sed -i 's/^exit.*/exit 0/' /sbin/initctl 		&& echo 'force-unsafe-io' > /etc/dpkg/dpkg.cfg.d/docker-apt-speedup 		&& echo 'DPkg::Post-Invoke { "rm -f /var/cache/apt/archives/*.deb /var/cache/apt/archives/partial/*.deb /var/cache/apt/*.bin || true"; };' > /etc/apt/apt.conf.d/docker-clean 	&& echo 'APT::Update::Post-Invoke { "rm -f /var/cache/apt/archives/*.deb /var/cache/apt/archives/partial/*.deb /var/cache/apt/*.bin || true"; };' >> /etc/apt/apt.conf.d/docker-clean 	&& echo 'Dir::Cache::pkgcache ""; Dir::Cache::srcpkgcache "";' >> /etc/apt/apt.conf.d/docker-clean 		&& echo 'Acquire::Languages "none";' > /etc/apt/apt.conf.d/docker-no-languages 		&& echo 'Acquire::GzipIndexes "true"; Acquire::CompressionTypes::Order:: "gz";' > /etc/apt/apt.conf.d/docker-gzip-indexes
# Fri, 08 Jul 2016 18:39:41 GMT
RUN rm -rf /var/lib/apt/lists/*
# Fri, 08 Jul 2016 18:39:43 GMT
RUN sed -i 's/^#\s*\(deb.*universe\)$/\1/g' /etc/apt/sources.list
# Fri, 08 Jul 2016 18:39:43 GMT
CMD ["/bin/bash"]
# Fri, 08 Jul 2016 18:44:57 GMT
ENV AEROSPIKE_VERSION=3.8.4
# Fri, 08 Jul 2016 18:44:57 GMT
ENV AEROSPIKE_SHA256=d9d78eafd7905d521646591d242f6dcf2ef9ca90f1187eb00f46e9613fee189f
# Fri, 08 Jul 2016 18:45:24 GMT
RUN apt-get update -y   &&  apt-get install -y wget logrotate ca-certificates   && wget "https://www.aerospike.com/artifacts/aerospike-server-community/${AEROSPIKE_VERSION}/aerospike-server-community-${AEROSPIKE_VERSION}-ubuntu16.04.tgz" -O aerospike-server.tgz   && echo "$AEROSPIKE_SHA256 *aerospike-server.tgz" | sha256sum -c -   && mkdir aerospike   && tar xzf aerospike-server.tgz --strip-components=1 -C aerospike   && dpkg -i aerospike/aerospike-server-*.deb   && mkdir -p /var/log/aerospike/   && mkdir -p /var/run/aerospike/   && rm -rf aerospike-server.tgz aerospike /var/lib/apt/lists/*
# Fri, 08 Jul 2016 18:45:25 GMT
COPY file:59f374b27ea4d0d2d9576cccc7c2a2a8893a36c2b0498759af9fde54286c59e8 in /etc/aerospike/aerospike.conf
# Fri, 08 Jul 2016 18:45:26 GMT
COPY file:ae9470d86ba973bb1d9911d608b000e6da810777ec7bb4e93d778fdbdeae4501 in /entrypoint.sh
# Fri, 08 Jul 2016 18:45:27 GMT
VOLUME [/opt/aerospike/data]
# Fri, 08 Jul 2016 18:45:28 GMT
EXPOSE 3000/tcp 3001/tcp 3002/tcp 3003/tcp
# Fri, 08 Jul 2016 18:45:28 GMT
ENTRYPOINT &{["/entrypoint.sh"]}
# Fri, 08 Jul 2016 18:45:29 GMT
CMD ["asd"]
```

-	Layers:
	-	`sha256:90d6565b970a2a27b197806e3a2bd19cc0fd1fc9241f7c00ae2f1295b3cac38d`  
		Last Modified: Thu, 07 Jul 2016 12:52:32 GMT  
		Size: 49.3 MB (49257890 bytes)
	-	`sha256:40553bdb84743dd9a3216ab110d274a01e309b916b3c628525a255969c6bdd61`  
		Last Modified: Fri, 08 Jul 2016 18:42:37 GMT  
		Size: 21.6 KB (21556 bytes)
	-	`sha256:c3129e7479abf3d666ac61caefdb62d03bfbd0f322f01d1f8bf30633a98c1bb8`  
		Last Modified: Fri, 08 Jul 2016 18:42:37 GMT  
		Size: 445.0 B
	-	`sha256:091663bd70db6ceba4405547c1e143f8ef676910aa914fe9edd87340cd3742b4`  
		Last Modified: Fri, 08 Jul 2016 18:42:37 GMT  
		Size: 679.0 B
	-	`sha256:e46cf7fb0c6655b63d338d9400ed27cb990c3f2bce5d7f09d6d718f97560afd4`  
		Last Modified: Fri, 08 Jul 2016 18:45:42 GMT  
		Size: 10.7 MB (10691016 bytes)
	-	`sha256:f35be25cc3034c7ebf781e1d66eb790e247f6576cac50f09edef6e27eeb821a7`  
		Last Modified: Fri, 08 Jul 2016 18:45:37 GMT  
		Size: 966.0 B
	-	`sha256:19bf2e73da5a6f68fdfeb33e44aa3da94e3bae2529c057d19fd1e3fbcba9570a`  
		Last Modified: Fri, 08 Jul 2016 18:45:38 GMT  
		Size: 309.0 B

## `aerospike:latest`

```console
$ docker pull aerospike@sha256:55c3aa7cadce113562a5c7b57a6717ea1745a5756b5bd31cbda90b6e3a352c13
```

-	Platforms:
	-	linux; amd64

### `aerospike:latest` - linux; amd64

-	Docker Version: 1.10.3
-	Manifest MIME: `application/vnd.docker.distribution.manifest.v2+json`
-	Total Size: **60.0 MB (59972861 bytes)**  
	(compressed transfer size, not on-disk size)
-	Image ID: `sha256:9e749e98506f0fbe5be4fc25e96c4ecf88485dbadbef86411b9a1f11f4352abc`
-	Entrypoint: `["\/entrypoint.sh"]`
-	Default Command: `["asd"]`

```dockerfile
# Fri, 08 Jul 2016 18:39:36 GMT
ADD file:49ae6eed5178a2866c5023c4e7a9ae303f4828a5586569106aff27a8ce9cadf6 in /
# Fri, 08 Jul 2016 18:39:39 GMT
RUN set -xe 		&& echo '#!/bin/sh' > /usr/sbin/policy-rc.d 	&& echo 'exit 101' >> /usr/sbin/policy-rc.d 	&& chmod +x /usr/sbin/policy-rc.d 		&& dpkg-divert --local --rename --add /sbin/initctl 	&& cp -a /usr/sbin/policy-rc.d /sbin/initctl 	&& sed -i 's/^exit.*/exit 0/' /sbin/initctl 		&& echo 'force-unsafe-io' > /etc/dpkg/dpkg.cfg.d/docker-apt-speedup 		&& echo 'DPkg::Post-Invoke { "rm -f /var/cache/apt/archives/*.deb /var/cache/apt/archives/partial/*.deb /var/cache/apt/*.bin || true"; };' > /etc/apt/apt.conf.d/docker-clean 	&& echo 'APT::Update::Post-Invoke { "rm -f /var/cache/apt/archives/*.deb /var/cache/apt/archives/partial/*.deb /var/cache/apt/*.bin || true"; };' >> /etc/apt/apt.conf.d/docker-clean 	&& echo 'Dir::Cache::pkgcache ""; Dir::Cache::srcpkgcache "";' >> /etc/apt/apt.conf.d/docker-clean 		&& echo 'Acquire::Languages "none";' > /etc/apt/apt.conf.d/docker-no-languages 		&& echo 'Acquire::GzipIndexes "true"; Acquire::CompressionTypes::Order:: "gz";' > /etc/apt/apt.conf.d/docker-gzip-indexes
# Fri, 08 Jul 2016 18:39:41 GMT
RUN rm -rf /var/lib/apt/lists/*
# Fri, 08 Jul 2016 18:39:43 GMT
RUN sed -i 's/^#\s*\(deb.*universe\)$/\1/g' /etc/apt/sources.list
# Fri, 08 Jul 2016 18:39:43 GMT
CMD ["/bin/bash"]
# Fri, 08 Jul 2016 18:44:57 GMT
ENV AEROSPIKE_VERSION=3.8.4
# Fri, 08 Jul 2016 18:44:57 GMT
ENV AEROSPIKE_SHA256=d9d78eafd7905d521646591d242f6dcf2ef9ca90f1187eb00f46e9613fee189f
# Fri, 08 Jul 2016 18:45:24 GMT
RUN apt-get update -y   &&  apt-get install -y wget logrotate ca-certificates   && wget "https://www.aerospike.com/artifacts/aerospike-server-community/${AEROSPIKE_VERSION}/aerospike-server-community-${AEROSPIKE_VERSION}-ubuntu16.04.tgz" -O aerospike-server.tgz   && echo "$AEROSPIKE_SHA256 *aerospike-server.tgz" | sha256sum -c -   && mkdir aerospike   && tar xzf aerospike-server.tgz --strip-components=1 -C aerospike   && dpkg -i aerospike/aerospike-server-*.deb   && mkdir -p /var/log/aerospike/   && mkdir -p /var/run/aerospike/   && rm -rf aerospike-server.tgz aerospike /var/lib/apt/lists/*
# Fri, 08 Jul 2016 18:45:25 GMT
COPY file:59f374b27ea4d0d2d9576cccc7c2a2a8893a36c2b0498759af9fde54286c59e8 in /etc/aerospike/aerospike.conf
# Fri, 08 Jul 2016 18:45:26 GMT
COPY file:ae9470d86ba973bb1d9911d608b000e6da810777ec7bb4e93d778fdbdeae4501 in /entrypoint.sh
# Fri, 08 Jul 2016 18:45:27 GMT
VOLUME [/opt/aerospike/data]
# Fri, 08 Jul 2016 18:45:28 GMT
EXPOSE 3000/tcp 3001/tcp 3002/tcp 3003/tcp
# Fri, 08 Jul 2016 18:45:28 GMT
ENTRYPOINT &{["/entrypoint.sh"]}
# Fri, 08 Jul 2016 18:45:29 GMT
CMD ["asd"]
```

-	Layers:
	-	`sha256:90d6565b970a2a27b197806e3a2bd19cc0fd1fc9241f7c00ae2f1295b3cac38d`  
		Last Modified: Thu, 07 Jul 2016 12:52:32 GMT  
		Size: 49.3 MB (49257890 bytes)
	-	`sha256:40553bdb84743dd9a3216ab110d274a01e309b916b3c628525a255969c6bdd61`  
		Last Modified: Fri, 08 Jul 2016 18:42:37 GMT  
		Size: 21.6 KB (21556 bytes)
	-	`sha256:c3129e7479abf3d666ac61caefdb62d03bfbd0f322f01d1f8bf30633a98c1bb8`  
		Last Modified: Fri, 08 Jul 2016 18:42:37 GMT  
		Size: 445.0 B
	-	`sha256:091663bd70db6ceba4405547c1e143f8ef676910aa914fe9edd87340cd3742b4`  
		Last Modified: Fri, 08 Jul 2016 18:42:37 GMT  
		Size: 679.0 B
	-	`sha256:e46cf7fb0c6655b63d338d9400ed27cb990c3f2bce5d7f09d6d718f97560afd4`  
		Last Modified: Fri, 08 Jul 2016 18:45:42 GMT  
		Size: 10.7 MB (10691016 bytes)
	-	`sha256:f35be25cc3034c7ebf781e1d66eb790e247f6576cac50f09edef6e27eeb821a7`  
		Last Modified: Fri, 08 Jul 2016 18:45:37 GMT  
		Size: 966.0 B
	-	`sha256:19bf2e73da5a6f68fdfeb33e44aa3da94e3bae2529c057d19fd1e3fbcba9570a`  
		Last Modified: Fri, 08 Jul 2016 18:45:38 GMT  
		Size: 309.0 B
