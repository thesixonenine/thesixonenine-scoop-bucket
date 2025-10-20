FROM mcr.microsoft.com/devcontainers/base:trixie
LABEL authors="Simple"
ARG GITHUB_PAT
ENV GITHUB_USERNAME=thesixonenine GITHUB_PAT=${GITHUB_PAT}
ENV HTTP_PROXY=socks5://host.docker.internal:1080 HTTPS_PROXY=socks5://host.docker.internal:1080
ENV DEBIAN_FRONTEND=noninteractive TZ=Asia/Shanghai

RUN sed -i -e 's@deb.debian.org@mirrors.aliyun.com@;s@http:@https:@' /etc/apt/sources.list.d/debian.sources && \
    apt-get update > /dev/null && apt-get upgrade -y > /dev/null && \
    apt-get install -y ncat > /dev/null && \
    sh -c "$(curl -fsLS get.chezmoi.io)"
USER vscode
RUN git config --global http.https://github.com.proxy $HTTP_PROXY && \
    chezmoi init https://$GITHUB_USERNAME:$GITHUB_PAT@github.com/$GITHUB_USERNAME/dotfiles.git
