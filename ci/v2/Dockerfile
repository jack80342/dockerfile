FROM gcr.io/kaniko-project/executor:v1.23.2
FROM alpine:3.20.2
# 复制kaniko
COPY --from=0 /kaniko/executor /usr/local/bin/kaniko
ENV LANG=C.UTF-8 \
    JAVA_HOME=/usr/lib/jvm/java-17-openjdk \
    PATH=$PATH:/usr/lib/jvm/java-17-openjdk/jre/bin
# 安装minIO、helm
COPY package/* /usr/local/bin/
RUN echo -e "http://mirrors.aliyun.com/alpine/v3.20/main/\nhttp://mirrors.aliyun.com/alpine/v3.20/community/" > /etc/apk/repositories \
    && apk --update add --no-cache curl bash tzdata zip git nodejs npm maven openjdk17 \
    # 修改时区
    && cp /usr/share/zoneinfo/Asia/Shanghai /etc/localtime \
    && echo "Asia/Shanghai" > /etc/timezone \
    && npm install --registry https://registry.npmmirror.com -g pnpm yarn \
    && helm init -c --stable-repo-url=https://mirror.azure.cn/kubernetes/charts/ \
    # 注释maven-default-http-blocker，159行到165行
    && sed -i '159i\<!--' /usr/share/java/maven-3/conf/settings.xml \
    && sed -i '166a\-->' /usr/share/java/maven-3/conf/settings.xml
COPY maven/settings.xml /root/.m2/
