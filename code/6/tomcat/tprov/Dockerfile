FROM ubuntu:18.04
LABEL maintainer="tim@example.com"
ENV REFRESHED_AT 2021-12-05

RUN apt-get -yqq update
RUN apt-get -qqy install ruby make ruby-dev build-essential sudo
RUN apt-get install -y apt-transport-https ca-certificates curl gnupg-agent software-properties-common

RUN curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -

RUN add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"

RUN apt-get update -y

RUN apt-get install -y docker-ce docker-ce-cli containerd.io git nano

RUN gem install tprov

EXPOSE 4567/tcp

CMD ["/usr/local/bin/tprov"]

