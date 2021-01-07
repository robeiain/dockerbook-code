FROM ubuntu:18.04
LABEL maintainer="tim@example.com"
ENV REFRESHED_AT 2021-01-03

RUN apt-get update -qq

RUN apt-get -qq install ruby-dev git libcurl4-openssl-dev curl build-essential python \ 
  uuid-dev libcap-dev libssl-dev libpcre3-dev zlib1g-dev uwsgi 

RUN gem install --no-ri --no-rdoc sinatra 

RUN mkdir -p /opt/distributed_app 
WORKDIR /opt/distributed_app 

RUN uwsgi --build-plugin  https://github.com/unbit/uwsgi-consul
ADD uwsgi-consul.ini /opt/distributed_app/ 

RUN chmod -x consul_plugin.so
RUN mv consul_plugin.so /usr/lib/uwsgi/plugins

ADD config.ru /opt/distributed_app/ 

ENTRYPOINT [ "uwsgi", "--ini", "uwsgi-consul.ini", "--ini", "uwsgi-consul.ini:server1", "--ini", "uwsgi-consul.ini:server2" ] 

CMD [] 
