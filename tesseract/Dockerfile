FROM alpine:3.16.5
ENV LANG=C.UTF-8 \
    JAVA_HOME=/usr/lib/jvm/java-1.8-openjdk \
    PATH=$PATH:/usr/lib/jvm/java-1.8-openjdk/jre/bin \
    TESSDATA_PREFIX=/usr/share/tessdata/
RUN echo -e "http://mirrors.aliyun.com/alpine/v3.16/main/\nhttp://mirrors.aliyun.com/alpine/v3.16/community/" > /etc/apk/repositories \
    && apk --update add --no-cache openjdk8 tesseract-ocr curl busybox-extras bash tzdata \
    # 修改时区
    && cp /usr/share/zoneinfo/Asia/Shanghai /etc/localtime \
    && echo "Asia/Shanghai" > /etc/timezone \
    # 下载训练好的简体中文模型
    && wget -P $TESSDATA_PREFIX https://raw.githubusercontent.com/tesseract-ocr/tessdata/main/chi_sim.traineddata
