FROM gcr.io/kaniko-project/executor:v1.9.2
FROM alpine:3.16.5
# 复制kaniko
COPY --from=0 /kaniko/executor /usr/local/bin/kaniko
ENV LANG=C.UTF-8
RUN echo -e "http://mirrors.aliyun.com/alpine/v3.16/main/\nhttp://mirrors.aliyun.com/alpine/v3.16/community/" > /etc/apk/repositories \
    && apk --update add --no-cache curl bash tzdata zip npm docker \
    # 修改时区
    && cp /usr/share/zoneinfo/Asia/Shanghai /etc/localtime \
    && echo "Asia/Shanghai" > /etc/timezone \
    && npm install -g pnpm
    # 安装minIO客户端
    #&& wget -P /usr/local/bin https://dl.min.io/client/mc/release/linux-amd64/mc \
    #&& chmod +x /usr/local/bin/mc \
    # 安装helm客户端
    #&& tar -xvf https://get.helm.sh/helm-v2.17.0-linux-amd64.tar.gz \
    #&& cp linux-amd64/helm /usr/local/bin/helm \
    #&& rm -rf linux-amd64
#COPY package/mc /usr/local/bin/mc
COPY package/* /usr/local/bin/

