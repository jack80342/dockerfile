FROM alpine:3.16.2
ENV LANG=C.UTF-8 \
    JAVA_HOME=/usr/lib/jvm/java-1.8-openjdk \
    PATH=$PATH:/usr/lib/jvm/java-1.8-openjdk/jre/bin
RUN echo -e "http://mirrors.aliyun.com/alpine/v3.16/main/\nhttp://mirrors.aliyun.com/alpine/v3.16/community/" > /etc/apk/repositories \
    && apk --update add --no-cache openjdk8 curl busybox-extras bash gcompat tzdata \
    && cp /usr/share/zoneinfo/Asia/Shanghai /etc/localtime \
    && echo "Asia/Shanghai" > /etc/timezone \
    && apk del tzdata
