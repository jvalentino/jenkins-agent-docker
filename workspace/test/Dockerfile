FROM jenkins/agent:latest-jdk11

USER root

RUN apt-get update 
RUN apt-get install -y gcc
RUN apt-get install -y curl
RUN curl -fsSL https://get.docker.com -o get-docker.sh
RUN sh get-docker.sh
COPY docker.service /lib/systemd/system/docker.service
RUN usermod -aG docker root
