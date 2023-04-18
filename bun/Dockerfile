FROM        oven/bun:latest
LABEL       author="Kris Dookharan" maintainer="krisdookharan15@gmail.com"

RUN         install_packages ffmpeg iproute2 git sqlite3 python3 ca-certificates tzdata dnsutils build-essential libcairo2-dev libpango1.0-dev libjpeg-dev libgif-dev librsvg2-dev
RUN         npm -g install npm@latest
RUN         useradd -m -d /home/container container

USER        container
ENV         USER=container HOME=/home/container
WORKDIR     /home/container

COPY        ./entrypoint.sh /entrypoint.sh
CMD         [ "/bin/bash", "/entrypoint.sh" ]
