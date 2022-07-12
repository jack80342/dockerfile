FROM alpine:3.16.0
ENV LANG=C.UTF-8 \
    JAVA_HOME=/usr/lib/jvm/java-1.8-openjdk \
    PATH=$PATH:/usr/lib/jvm/java-1.8-openjdk/jre/bin \
    TESSDATA_PREFIX=/usr/share/tessdata/
RUN apk add --no-cache openjdk8 tesseract-ocr && wget -P $TESSDATA_PREFIX https://raw.githubusercontent.com/tesseract-ocr/tessdata/main/chi_sim.traineddata
