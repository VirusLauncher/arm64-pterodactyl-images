FROM        arm64v8/openjdk:17-slim-buster

LABEL       author="Kris Dookharan" maintainer="krisdookharan15@gmail.com"

RUN apt-get update -y \
 && apt-get install -y curl ca-certificates openssl git tar sqlite3 fontconfig tzdata iproute2 \
 && useradd -d /home/container -m container

USER        container
ENV         USER=container HOME=/home/container

WORKDIR     /home/container

COPY        ./entrypoint.sh /entrypoint.sh

CMD         ["/bin/bash", "/entrypoint.sh"]