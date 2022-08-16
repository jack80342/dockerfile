FROM alpine:3.16.2
ENV LANG=C.UTF-8
RUN echo -e "http://mirrors.aliyun.com/alpine/v3.16/main/\nhttp://mirrors.aliyun.com/alpine/v3.16/community/" > /etc/apk/repositories \
    && apk --update add --no-cache nginx curl busybox-extras bash \
    && rm -f /usr/share/nginx/html/index.html /etc/nginx/conf.d/default.conf
