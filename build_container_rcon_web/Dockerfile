FROM php:7.4.8-apache

ARG minecraft_server_config_rcon_host
ARG minecraft_server_config_rcon_port
ARG minecraft_server_config_rcon_password

RUN set -x && \
    apt-get update && apt-get -y upgrade

RUN set -x && \
    apt-get install -y curl

RUN set -x && \
    apt-get install -y wget

RUN set -x && \
    apt-get install -y git

RUN set -x && \
    apt-get install -y gcc

RUN set -x && \
    apt-get install -y make

RUN set -x && \
    apt-get install -y libonig-dev

RUN set -x && \
    docker-php-ext-install pdo_mysql mysqli

WORKDIR /var/minecraft/

RUN set -x && \
    git clone https://github.com/Rauks/Minecraft-RCON.git

WORKDIR /var/minecraft/Minecraft-RCON/

ENV MCRCON_HOST ${minecraft_server_config_rcon_host}
ENV MCRCON_PORT ${minecraft_server_config_rcon_port}
ENV MCRCON_PASS ${minecraft_server_config_rcon_password}

RUN echo 'alias ll="ls -l"' >> /etc/bashrc
RUN echo '' >> /etc/bashrc

ENTRYPOINT ["sh"]
