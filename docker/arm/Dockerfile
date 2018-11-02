FROM resin/raspberrypi3-node:slim

ENV TINI_VERSION=v0.18.0
ENV TINI_ARCH=armhf
EXPOSE 3000

WORKDIR /app

RUN apt-get update \
    && apt-get install -y curl \
    && npm i -g json-server \
    && curl -sL --output ./tini \
    https://github.com/krallin/tini/releases/download/${TINI_VERSION}/tini-${TINI_ARCH} \
    && chmod +x ./tini

COPY ./config/* ./

ENTRYPOINT [ \
    "/app/tini", "-s", "--", \
    "json-server", \
    "--host", "0.0.0.0" \
    ]
