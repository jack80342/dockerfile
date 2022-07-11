FROM amd64/alpine:3.15.4
ENV LANG=C.UTF-8 \
    JAVA_HOME=/usr/lib/jvm/java-1.8-openjdk \
    PATH=$PATH:/usr/lib/jvm/java-1.8-openjdk/jre/bin
RUN apk add --no-cache openjdk8 && rm -f /etc/apk/repositories
