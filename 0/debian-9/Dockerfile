FROM bitnami/minideb:stretch
LABEL maintainer "Bitnami <containers@bitnami.com>"

# Install required system packages and dependencies
RUN install_packages ca-certificates libc6 wget
RUN wget -nc -P /tmp/bitnami/pkg/cache/ https://downloads.bitnami.com/files/stacksmith/zookeeper-exporter-0.1.2-0-linux-amd64-debian-9.tar.gz && \
    echo "3dc4262425407f0ab497524bea8ebab9314e82c3dce6642890db224a0b2d221a  /tmp/bitnami/pkg/cache/zookeeper-exporter-0.1.2-0-linux-amd64-debian-9.tar.gz" | sha256sum -c - && \
    tar -zxf /tmp/bitnami/pkg/cache/zookeeper-exporter-0.1.2-0-linux-amd64-debian-9.tar.gz -P --transform 's|^[^/]*/files|/opt/bitnami|' --wildcards '*/files' && \
    rm -rf /tmp/bitnami/pkg/cache/zookeeper-exporter-0.1.2-0-linux-amd64-debian-9.tar.gz
RUN ln -sf /opt/bitnami/zookeeper-exporter/bin/zookeeper-exporter /usr/local/bin/zookeeper-exporter

ENV BITNAMI_APP_NAME="zookeeper-exporter" \
    BITNAMI_IMAGE_VERSION="0.1.2-debian-9-r23" \
    PATH="/opt/bitnami/zookeeper-exporter/bin:$PATH"

EXPOSE 8080

WORKDIR /opt/bitnami/zookeeper-exporter
USER 1001
ENTRYPOINT [ "zookeeper-exporter" ]
