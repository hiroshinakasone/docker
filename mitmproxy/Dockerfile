FROM ubuntu:20.04

ENV LANG=en_US.UTF-8

ARG MITMPROXY_VERSION=7.0.4
ARG MITMPROXY_PATH=/usr/local/mitmproxy/${MITMPROXY_VERSION}

RUN \
    apt-get update && \
    apt-get upgrade -y && \
    apt-get install -y curl && \
    mkdir -p ${MITMPROXY_PATH} && \
    cd ${MITMPROXY_PATH} && \
    curl -O https://snapshots.mitmproxy.org/${MITMPROXY_VERSION}/mitmproxy-${MITMPROXY_VERSION}-linux.tar.gz && \
    tar zxfv mitmproxy-${MITMPROXY_VERSION}-linux.tar.gz && \
    rm mitmproxy-${MITMPROXY_VERSION}-linux.tar.gz && \
    ln -s ${MITMPROXY_PATH}/mitmweb /usr/local/bin && \
    ln -s ${MITMPROXY_PATH}/mitmdump /usr/local/bin && \
    ln -s ${MITMPROXY_PATH}/mitmproxy /usr/local/bin

EXPOSE 8080 8081

CMD ["mitmweb", "--web-host", "0.0.0.0"]
