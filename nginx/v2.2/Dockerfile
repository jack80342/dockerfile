FROM nginx:1.27.4-alpine3.21-slim
ENV LANG=C.UTF-8
RUN echo -e "http://mirrors.aliyun.com/alpine/v3.21/main/\nhttp://mirrors.aliyun.com/alpine/v3.21/community/" > /etc/apk/repositories \
    && apk --update add --no-cache curl busybox-extras bash \
    # 修改时区
    && cp /usr/share/zoneinfo/Asia/Shanghai /etc/localtime \
    && echo "Asia/Shanghai" > /etc/timezone \
    # 删除nginx的默认配置文件
    && rm -f /usr/share/nginx/html/index.html /etc/nginx/conf.d/default.conf /etc/nginx/nginx.conf
