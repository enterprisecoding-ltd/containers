
ARG WEBHOOK_VER=2.8.1
ARG SHELL_VER=v0.1.21
ARG TARGETPLATFORM=linux/amd64
ARG DOWNLOAD_URL=https://github.com/adnanh/webhook/releases/download

FROM alpine as downloader

ARG WEBHOOK_VER
ARG TARGETPLATFORM
ARG DOWNLOAD_URL

RUN apk --no-cache add curl
RUN if [ "$TARGETPLATFORM" = "linux/amd64" ]; then ARCHITECTURE=amd64; elif [ "$TARGETPLATFORM" = "linux/arm/v7" ]; then ARCHITECTURE=arm; elif [ "$TARGETPLATFORM" = "linux/arm64" ]; then ARCHITECTURE=aarch64; else ARCHITECTURE=amd64; fi && \
    mkdir -p /tmp/webhook && \
    curl -L ${DOWNLOAD_URL}/${WEBHOOK_VER}/webhook-linux-${ARCHITECTURE}.tar.gz -o /tmp/webhook/webhook.tar.gz  && \
    ls -al /tmp/webhook/ && \
    tar xzvf /tmp/webhook/webhook.tar.gz -C /tmp/webhook/ --strip-components=1 && \
    chmod +x /tmp/webhook/webhook


FROM rancher/shell:${SHELL_VER}
LABEL maintainer="Fatih Boy <fatih.boy@enterprisecoding.com>"

WORKDIR /

COPY --from=downloader /tmp/webhook/webhook /usr/local/bin/webhook

EXPOSE 9000
ENTRYPOINT  ["/usr/local/bin/webhook"]