FROM alpine:3.15
RUN apk update
RUN apk add git

RUN apk update \
    && apk get install -y --no-install-recommends python:3.8.2-alpine
    && apk add git \
    && apk install -y --no-install-recommends \
        mercurial git ca-certificates \
    && rm -rf /var/lib/apt/lists/* \
    \
    && mkdir /app \
    && cd /app \
    && git clone https://github.com/BhumikaRupera/hg-to-git-repo.git . \
    && git checkout

VOLUME /hg
VOLUME /git

WORKDIR /git

python exporter.py --bash="C:\\Program Files\\Git\\bin\\bash.exe" --hg-user="t0251371" --hg-pass="t025@Thales" --git-user="BhumikaRupera"
 --git-token="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" --hg-repo="https://sin1hg.gemalto.com/hg/TelcoSoft/Training/ota-emp-management" --git-repo="https://github.com/BhumikaRupera/repo-test.git" --hg-hash
ENV hgUser=$1 hgPass=$2 gitUser=$3 gitPat=$4 sourceUrl=$5 targetUrl=$6 copyHash=$7

ARG sourceUrl = '--hg-repo='
ARG targetUrl
ARG gitUser
ARG hgUser
ARG gitPat
ARG hgPass
ARG copyHash
ARG bash = '--bash="C:\\Program Files\\Git\\bin\\bash.exe"'

CMD ["python", "exporter.py", "bash", ]




FROM alpine:3.15
RUN apk update
RUN apk add git



COPY git2gitMigration.sh $APP_BIN

ENV sourcepat=$1 sourceUrl=$2 projectName=$3 targetPatName=$4 targetpat=$5 targetUrl=$6



CMD ["./git2gitMigration.sh"]