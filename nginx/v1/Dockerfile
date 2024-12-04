FROM alpine:3.16.9
ENV LANG=C.UTF-8
RUN echo -e "http://mirrors.aliyun.com/alpine/v3.16/main/\nhttp://mirrors.aliyun.com/alpine/v3.16/community/" > /etc/apk/repositories \
    && apk --update add --no-cache nginx curl busybox-extras bash tzdata \
    # 修改时区
    && cp /usr/share/zoneinfo/Asia/Shanghai /etc/localtime \
    && echo "Asia/Shanghai" > /etc/timezone \
    # 删除nginx的默认配置文件
    && rm -f /usr/share/nginx/html/index.html /etc/nginx/conf.d/default.conf /etc/nginx/nginx.conf \
    # 将日志输出到docker日志收集器
    && ln -sf /dev/stdout /var/log/nginx/access.log \
    && ln -sf /dev/stderr /var/log/nginx/error.log
