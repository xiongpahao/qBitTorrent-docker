# https://hub.docker.com/r/linuxserver/qbittorrent

FROM linuxserver/qbittorrent:latest
MAINTAINER EXP

ENV PUID=1000
ENV PGID=1000
ENV TZ=Aisa/Shanghai
ENV UMASK_SET=022
ENV WEBUI_PORT=8088

RUN mkdir -p /downloads/incomplete/ && \
    mkdir -p /config/qBittorrent/
    
# qBittorrent 会读取 qBittorrent_new.conf 并生成对应的 qBittorrent.conf
# 因为会引起权限问题，不能直接挂载为 qBittorrent.conf
ADD ./qBittorrent.conf /config/qBittorrent/qBittorrent_new.conf

EXPOSE 8088
EXPOSE 9000
EXPOSE 6881
EXPOSE 6881/udp
WORKDIR /config

# 此镜像服务会自启，再启动会因为端口冲突导致镜像无限重启
# CMD [ "/usr/bin/qbittorrent-nox", "--webui-port=8088" ]
