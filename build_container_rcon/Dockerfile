FROM almalinux:8
USER root:root

ARG minecraft_server_config_rcon_host
ARG minecraft_server_config_rcon_port
ARG minecraft_server_config_rcon_password

RUN set -x && \
    dnf update -y --security

RUN set -x && \
    dnf install -y curl

RUN set -x && \
    dnf install -y wget

RUN set -x && \
    dnf install -y git

RUN set -x && \
    dnf install -y gcc

RUN set -x && \
    dnf install -y make

WORKDIR /var/minecraft/

RUN set -x && \
    git clone https://github.com/Tiiffi/mcrcon.git

WORKDIR /var/minecraft/mcrcon/

RUN set -x && \
    make

RUN set -x && \
    make install

RUN set -x && \
    mcrcon -v

WORKDIR /var/minecraft/

ENV MCRCON_HOST ${minecraft_server_config_rcon_host}
ENV MCRCON_PORT ${minecraft_server_config_rcon_port}
ENV MCRCON_PASS ${minecraft_server_config_rcon_password}

RUN echo 'alias ll="ls -l"' >> /etc/bashrc
RUN echo '' >> /etc/bashrc
RUN echo 'mcrcon -h' >> /etc/bashrc

ENTRYPOINT ["sh"]
