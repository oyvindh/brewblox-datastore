FROM node:slim

ENV TINI_VERSION=v0.18.0
ENV TINI_ARCH=amd64
EXPOSE 3000

WORKDIR /app

RUN npm i -g json-server \
    && curl -sL --output ./tini \
    https://github.com/krallin/tini/releases/download/${TINI_VERSION}/tini-${TINI_ARCH} \
    && chmod +x ./tini

COPY ./config/* ./

ENTRYPOINT [ \
    "./tini", "-s", "--", \
    "json-server", \
    "--host", "0.0.0.0", \
    "--routes", "routes.json" \
    ]
