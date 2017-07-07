FROM alpine:3.6

RUN apk update \
	&& apk add mariadb \
	&& rm -rf /var/cache/apk/*

COPY libgalera_smm.so /lib/
COPY my.cnf /etc/mysql/

RUN deluser mysql \
	&& addgroup -S -g 101 mysql \
	&& adduser -h /var/lib/mysql -u 100 -s /bin/sh -S -g mysql -G mysql mysql

#USER mysql

VOLUME /data

ENTRYPOINT ["sh", "-i"]
