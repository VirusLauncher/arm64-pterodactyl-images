FROM        arm64v8/node:24-bookworm-slim

LABEL       author="Kris Dookharan" maintainer="krisdookharan15@gmail.com"

RUN         apt update \
    && apt-get install -y ffmpeg iproute2 git sqlite3 python3 ca-certificates tzdata dnsutils build-essential libcairo2-dev libpango1.0-dev libjpeg-dev libgif-dev librsvg2-dev \
    && npm -g install npm@latest \
    && useradd -m -d /home/container container

USER        container
ENV         USER=container HOME=/home/container
WORKDIR     /home/container

COPY        ./entrypoint.sh /entrypoint.sh
CMD         [ "/bin/bash", "/entrypoint.sh" ]
