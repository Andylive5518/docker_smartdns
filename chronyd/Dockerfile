FROM alpine:latest

LABEL build_info="alex5518/chronyd"

ENV TZ=Asia/Shanghai
# install chrony
RUN apk add --no-cache chrony tzdata &&\
    cp /usr/share/zoneinfo/${TZ} /etc/localtime &&\
    echo $TZ > /etc/timezone

# script to configure/startup chrony (ntp)
COPY startup.sh /opt/startup.sh

# ntp port
EXPOSE 123/udp

VOLUME "/etc/chrony/"

# let docker know how to test container health
HEALTHCHECK CMD chronyc tracking || exit 1

# start chronyd in the foreground
ENTRYPOINT [ "/bin/sh", "/opt/startup.sh" ]
