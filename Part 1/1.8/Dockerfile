FROM ubuntu:20.04

WORKDIR /usr/src/app

COPY website.sh .

RUN chmod +x website.sh

RUN apt update

RUN apt -y install curl

CMD ./website.sh

