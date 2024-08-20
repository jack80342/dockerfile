FROM gcr.io/kaniko-project/executor:v1.12.1
FROM debian:11.10-slim
# 复制kaniko
COPY --from=0 /kaniko/executor /usr/local/bin/kaniko
RUN apt-get update \
    && apt-get -y install curl git bash \
    # 清理缓存
    && rm -rf /var/lib/apt/lists/*
