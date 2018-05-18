FROM alpine:3.5

MAINTAINER Alejandro Torres <info@alejandrotorres.xyz>

RUN echo "http://dl-4.alpinelinux.org/alpine/v3.3/main" >> /etc/apk/repositories && \
    apk add --update nginx=1.8.1-r2 && \
    rm -rf /var/cache/apk/* && \
    chown -R nginx:www-data /var/lib/nginx

COPY root /

EXPOSE 80

CMD ["/usr/sbin/nginx"]
