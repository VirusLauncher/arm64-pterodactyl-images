# https://github.com/oven-sh/bun/issues/211#issuecomment-1180644348
FROM        arm64v8/debian:buster-slim as get

WORKDIR     /tmp

RUN         apt update
RUN         apt-get install curl unzip -y
RUN         curl -LO https://github.com/oven-sh/bun/releases/download/bun-v0.5.9/bun-linux-aarch64.zip \
    && unzip bun-linux-aarch64.zip

# Image from here
FROM        arm64v8/debian:buster-slim
LABEL       author="Kris Dookharan" maintainer="krisdookharan15@gmail.com"

RUN         apt update \
    && apt-get install -y ffmpeg ca-certificates tzdata dnsutils build-essential \
    && npm -g install npm@latest \
    && useradd -m -d /home/container container

COPY --from=get /tmp/bun-linux-aarch64/bun /usr/local/bin/bun

USER        container
ENV         USER=container HOME=/home/container
WORKDIR     /home/container


COPY        ./entrypoint.sh /entrypoint.sh
CMD         [ "/bin/bash", "/entrypoint.sh" ]
