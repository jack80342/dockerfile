FROM alpine:3.16.6
ENV LANG=C.UTF-8 \
    JAVA_HOME=/usr/lib/jvm/java-1.8-openjdk \
    PATH=$PATH:/usr/lib/jvm/java-1.8-openjdk/jre/bin \
    TESSDATA_PREFIX=/usr/share/tessdata/
RUN echo -e "http://mirrors.aliyun.com/alpine/v3.16/main/\nhttp://mirrors.aliyun.com/alpine/v3.16/community/" > /etc/apk/repositories \
    && apk --update add --no-cache openjdk8 tesseract-ocr curl busybox-extras bash gcompat tzdata tini \
    # 修改时区
    && cp /usr/share/zoneinfo/Asia/Shanghai /etc/localtime \
    && echo "Asia/Shanghai" > /etc/timezone \
    # 新建data目录
    && mkdir data tongweb arthas \
    # arthas
    && curl -O --output-dir /arthas https://arthas.aliyun.com/arthas-boot.jar
# 添加字体：微软雅黑
COPY font/* /usr/share/fonts/
# 添加简体中文模型
COPY tesseract/* /usr/share/tessdata/
