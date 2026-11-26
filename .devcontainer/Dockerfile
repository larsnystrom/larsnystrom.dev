FROM mcr.microsoft.com/devcontainers/base:ubuntu

ARG TARGETARCH

COPY .hugo-version /tmp/hugo-version

RUN set -eux; \
    apt-get update; \
    apt-get install -y --no-install-recommends ca-certificates curl; \
    install -d -m 755 /etc/apt/keyrings; \
    curl -fsSL https://cli.github.com/packages/githubcli-archive-keyring.gpg -o /etc/apt/keyrings/githubcli-archive-keyring.gpg; \
    chmod go+r /etc/apt/keyrings/githubcli-archive-keyring.gpg; \
    echo "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/githubcli-archive-keyring.gpg] https://cli.github.com/packages stable main" > /etc/apt/sources.list.d/github-cli.list; \
    apt-get update; \
    apt-get install -y --no-install-recommends gh; \
    version="$(cat /tmp/hugo-version)"; \
    curl -fsSL "https://github.com/gohugoio/hugo/releases/download/v${version}/hugo_extended_${version}_linux-${TARGETARCH}.tar.gz" -o /tmp/hugo.tar.gz; \
    tar -xzf /tmp/hugo.tar.gz -C /usr/local/bin hugo; \
    hugo version; \
    rm -f /tmp/hugo-version /tmp/hugo.tar.gz; \
    apt-get clean; \
    rm -rf /var/lib/apt/lists/*
