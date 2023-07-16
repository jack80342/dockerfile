FROM gcr.io/kaniko-project/executor:v1.12.1
FROM alpine:3.16.6
# 复制kaniko
COPY --from=0 /kaniko/executor /usr/local/bin/kaniko
ENV LANG=C.UTF-8 \
    JAVA_HOME=/usr/lib/jvm/java-1.8-openjdk \
    PATH=$PATH:/usr/lib/jvm/java-1.8-openjdk/jre/bin
# 安装minIO、helm
COPY package/* /usr/local/bin/
RUN echo -e "http://mirrors.aliyun.com/alpine/v3.16/main/\nhttp://mirrors.aliyun.com/alpine/v3.16/community/" > /etc/apk/repositories \
    && apk --update add --no-cache curl bash tzdata zip git npm maven openjdk8 \
    # 修改时区
    && cp /usr/share/zoneinfo/Asia/Shanghai /etc/localtime \
    && echo "Asia/Shanghai" > /etc/timezone \
    && npm install --registry https://registry.npm.taobao.org -g pnpm yarn \
    && helm init -c --stable-repo-url=https://mirror.azure.cn/kubernetes/charts/ \
    # 注释maven-default-http-blocker，159行到165行
    && sed -i '159i\<!--' /usr/share/java/maven-3/conf/settings.xml \
    && sed -i '166a\-->' /usr/share/java/maven-3/conf/settings.xml
COPY maven/settings.xml /root/.m2/
