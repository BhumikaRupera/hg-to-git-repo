FROM alpine:3.15

RUN apk update
RUN apk add python3
RUN apk add mercurial git ca-certificates
RUN rm -rf /var/lib/apt/lists/*
RUN mkdir /app
RUN cd /app && git clone https://github.com/BhumikaRupera/hg-to-git-repo.git
RUN cd /app/hg-to-git-repo/ && ls && git checkout

VOLUME /hg
VOLUME /git

ARG sourceUrl
ARG targetUrl
ARG gitUser
ARG hgUser
ARG gitPat
ARG hgPass
ARG copyHash

ENV hgUser=$1 hgPass=$2 gitUser=$3 gitPat=$4 sourceUrl=$5 targetUrl=$6 copyHash=$7

ENTRYPOINT ["python3", "/app/hg-to-git-repo/exporter.py", hgUser, hgPass, gitUser, gitPat, sourceUrl, targetUrl, copyHash]



