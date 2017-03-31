FROM centos:6.8

MAINTAINER Haesung Hwang <suhoag@naver.com>

RUN yum -y update && yum -y install gcc make wget openssl-devel && yum -y clean all

ENV HTTPD_PREFIX /usr/local/apache
RUN mkdir -p "$HTTPD_PREFIX"

WORKDIR "$HTTPD_PREFIX"

RUN mkdir -p src \
        && wget -O httpd.tar.gz http://mirror.navercorp.com/apache/httpd/httpd-2.2.32.tar.gz \
        && tar -xvf httpd.tar.gz -C src --strip-components=1 \
        && rm -f httpd.tar.gz \
        && cd src \
        && ./configure --prefix="$HTTPD_PREFIX" --enable-mods-shared=most --enable-ssl \
        && make \
        && make install \
        && cd .. \
        && rm -r src man manual

EXPOSE 80