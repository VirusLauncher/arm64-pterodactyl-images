FROM        node:16-buster-slim

LABEL       author="Kris Dookharan" maintainer="krisdookharan15@gmail.com"

RUN         apt update \
            && apt -y install ffmpeg iproute2 git sqlite3 python3 ca-certificates tzdata dnsutils build-essential wget \
            && wget -q -O - https://dl-ssl.google.com/linux/linux_signing_key.pub | apt-key add - \
            && sh -c 'echo "deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main" >> /etc/apt/sources.list.d/google.list' \
            && apt-get update \
            && apt-get install -y google-chrome-stable fonts-ipafont-gothic fonts-wqy-zenhei fonts-thai-tlwg fonts-kacst fonts-freefont-ttf libxss1 libcairo2-dev libpango1.0-dev libjpeg-dev libgif-dev librsvg2-dev ffmpeg iproute2 git sqlite3 python3 ca-certificates tzdata dnsutils build-essential \
            && rm -rf /var/lib/apt/lists/* \
            && useradd -m -d /home/container container

USER        container
ENV         USER=container HOME=/home/container
WORKDIR     /home/container

COPY        ./entrypoint.sh /entrypoint.sh
CMD         ["/bin/bash", "/entrypoint.sh"]