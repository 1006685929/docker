# base image
FROM eduosi/jdk:1.8.0_202

# maintainer
MAINTAINER Yong.Teng eduosi@163.com

COPY zookeeper-3.4.13 usr/local/zookeeper
COPY zookeeper usr/sbin/zookeeper

RUN addgroup -g 1001 -S zookeeper 2> /dev/null \
    && adduser zookeeper -u 1001 -D -H -S -s /sbin/nologin -G zookeeper 2> /dev/null

RUN chown zookeeper:zookeeper -fR /usr/local/zookeeper \
	&& chmod 0755 -fR /usr/local/zookeeper \
	&& chown zookeeper:zookeeper /usr/sbin/zookeeper \
	&& chmod 0755 /usr/sbin/zookeeper \
	&& mkdir /data \
	&& chown zookeeper:zookeeper /data \
	&& mkdir /var/log/zookeeper \
	&& chown zookeeper:zookeeper /var/log/zookeeper

VOLUME /data

EXPOSE 2181 2888 3888

USER zookeeper