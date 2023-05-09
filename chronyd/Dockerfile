FROM alpine:latest
RUN apk add --no-cache ca-certificates && update-ca-certificates
#定义时区
ENV TZ=Asia/Shanghai

RUN apk add --no-cache --update tzdata &&\
    cp /usr/share/zoneinfo/${TZ} /etc/localtime &&\
    echo $TZ > /etc/timezone

RUN apk add --no-cache --update chrony
VOLUME "/etc/chrony/"
EXPOSE 123/udp
CMD [ "/usr/sbin/chronyd", "-d", "-s" ]
