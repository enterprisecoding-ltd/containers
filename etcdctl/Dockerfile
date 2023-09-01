FROM bash:5.2.15
LABEL maintainer="Fatih Boy <fatih.boy@enterprisecoding.com>"

WORKDIR /

ARG ETCD_VER=v3.4.27
ARG TARGETPLATFORM=linux/amd64
ARG DOWNLOAD_URL=https://github.com/etcd-io/etcd/releases/download

RUN apk update && \
    apk add curl && \
    apk add jq && \
    apk add bash

RUN if [ "$TARGETPLATFORM" = "linux/amd64" ]; then ARCHITECTURE=amd64; elif [ "$TARGETPLATFORM" = "linux/arm/v7" ]; then ARCHITECTURE=arm; elif [ "$TARGETPLATFORM" = "linux/arm64" ]; then ARCHITECTURE=aarch64; else ARCHITECTURE=amd64; fi && \
    mkdir -p /tmp/etcd/binaries && \
    curl -L ${DOWNLOAD_URL}/${ETCD_VER}/etcd-${ETCD_VER}-linux-${ARCHITECTURE}.tar.gz -o /tmp/etcd/etcd-${ETCD_VER}-linux-${ARCHITECTURE}.tar.gz && \
    tar xzvf /tmp/etcd/etcd-${ETCD_VER}-linux-${ARCHITECTURE}.tar.gz -C /tmp/etcd/binaries --strip-components=1 && \
    ls -al && \
    mv /tmp/etcd/binaries/etcdctl /usr/local/bin && \
    chmod +x /usr/local/bin/etcdctl

CMD ["bash"]