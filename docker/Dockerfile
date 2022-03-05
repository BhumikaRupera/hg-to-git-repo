FROM ubuntu:eoan

ENV HG_FAST_EXPORT_VERSION=v200213

RUN sed -i -e 's%http://\(archive\|security\)%mirror://mirrors%' -e 's%/ubuntu/%/mirrors.txt%' /etc/apt/sources.list \
    && apt update \
    && apt install -y --no-install-recommends \
        mercurial git ca-certificates \
    && rm -rf /var/lib/apt/lists/* \
    \
    && mkdir /app \
    && cd /app \
    && git clone https://github.com/chrisjbillington/hg-export-tool.git . \
    && git checkout

VOLUME /hg
VOLUME /git

WORKDIR /git

ENTRYPOINT ["/app/exporter.py", "-r", "/hg"]