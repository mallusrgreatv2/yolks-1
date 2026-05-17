FROM        eclipse-temurin:25-jdk-noble

LABEL       author="Michael Parker" maintainer="parker@pterodactyl.io"

LABEL       org.opencontainers.image.source="https://github.com/pterodactyl/yolks"
LABEL       org.opencontainers.image.licenses=MIT

# hadolint ignore=DL3015
RUN         apt-get update -y \
            && apt-get upgrade -y \
            && apt-get install -y \
                curl \
                lsof \
                ca-certificates \
                openssl \
                git \
                tar \
                sqlite3 \
                fontconfig \
                tzdata \
                iproute2 \
                libfreetype6 \
                tini \
				zip \
				unzip \
				libargon2-0-dev \
			&& rm -rf /var/lib/apt/lists/*
			&& ln -s /usr/lib/x86_64-linux-gnu/libargon2.so /usr/lib/libargon2.so

## Setup working directory and environment
ENV         USER=container HOME=/home/container
WORKDIR     /home/container

STOPSIGNAL SIGINT

COPY        --chown=root:root --chmod=755 ./../entrypoint.sh /entrypoint.sh
ENTRYPOINT    ["/usr/bin/tini", "-g", "--", "/entrypoint.sh"]
