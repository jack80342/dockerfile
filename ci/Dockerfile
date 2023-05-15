FROM gcr.io/kaniko-project/executor:v1.9.2
FROM alpine:3.16.5
# 复制kaniko
COPY --from=0 /kaniko/executor /usr/local/bin/kaniko
ENV LANG=C.UTF-8
# 安装minIO、helm
COPY package/* /usr/local/bin/
RUN echo -e "http://mirrors.aliyun.com/alpine/v3.16/main/\nhttp://mirrors.aliyun.com/alpine/v3.16/community/" > /etc/apk/repositories \
    && apk --update add --no-cache curl bash tzdata zip git npm \
    # 修改时区
    && cp /usr/share/zoneinfo/Asia/Shanghai /etc/localtime \
    && echo "Asia/Shanghai" > /etc/timezone \
    && npm install --registry https://registry.npm.taobao.org -g pnpm \
    && helm init -c --stable-repo-url=https://mirror.azure.cn/kubernetes/charts/

