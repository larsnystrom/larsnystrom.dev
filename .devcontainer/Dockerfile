FROM mcr.microsoft.com/devcontainers/base:ubuntu

ARG TARGETARCH

COPY .hugo-version /tmp/hugo-version

RUN set -eux; \
    apt-get update; \
    apt-get install -y --no-install-recommends ca-certificates curl; \
    version="$(cat /tmp/hugo-version)"; \
    curl -fsSL "https://github.com/gohugoio/hugo/releases/download/v${version}/hugo_extended_${version}_linux-${TARGETARCH}.tar.gz" -o /tmp/hugo.tar.gz; \
    tar -xzf /tmp/hugo.tar.gz -C /usr/local/bin hugo; \
    hugo version; \
    rm -f /tmp/hugo-version /tmp/hugo.tar.gz; \
    apt-get clean; \
    rm -rf /var/lib/apt/lists/*
