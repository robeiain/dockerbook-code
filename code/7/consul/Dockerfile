FROM ubuntu:18.04
LABEL maintainer="tim@example.com"
ENV REFRESHED_AT 2021-01-03

RUN apt-get -qq update
RUN apt-get -qq install curl unzip

ADD https://releases.hashicorp.com/consul/1.9.0/consul_1.9.0_linux_amd64.zip /tmp/consul.zip
RUN cd /usr/sbin && unzip /tmp/consul.zip && chmod +x /usr/sbin/consul && rm /tmp/consul.zip
ADD consul.json /config/

EXPOSE 8300 8301 8301/udp 8302 8302/udp 8400 8500 53/udp

VOLUME ["/data"]

ENTRYPOINT [ "/usr/sbin/consul", "agent", "-config-dir=/config" ]
CMD []
