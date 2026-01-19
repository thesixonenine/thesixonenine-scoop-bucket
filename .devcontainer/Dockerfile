ARG TAG=trixie
FROM mcr.microsoft.com/devcontainers/base:${TAG}
LABEL authors="Simple"
ARG MY_PAT
ARG USERNAME=thesixonenine
ENV HTTP_PROXY=socks5://host.docker.internal:1080 HTTPS_PROXY=socks5://host.docker.internal:1080
ENV TZ=Asia/Shanghai DEBIAN_FRONTEND=noninteractive

RUN sed -i -e 's@deb.debian.org@mirrors.aliyun.com@;s@http:@https:@' /etc/apt/sources.list.d/debian.sources && \
    apt-get update > /dev/null && apt-get upgrade -y > /dev/null && \
    apt-get install -y ncat age expect > /dev/null && \
    sh -c "$(curl -fsLS get.chezmoi.io)" && \
    chsh -s /usr/bin/zsh vscode
USER vscode
RUN git config --global http.https://github.com.proxy $HTTP_PROXY && \
    chezmoi init https://$USERNAME:$MY_PAT@github.com/$USERNAME/dotfiles.git
