FROM docker:latest
MAINTAINER Florian Dhaussy <florian.dhaussy@elosi.com>

ENV CONSUL_TEMPLATE_VERSION 0.16.0

RUN apk --no-cache --update add curl bash \
    && cd /tmp \
    && curl -fOSL https://releases.hashicorp.com/consul-template/${CONSUL_TEMPLATE_VERSION}/consul-template_${CONSUL_TEMPLATE_VERSION}_SHA256SUMS \
    && curl -fOSL https://releases.hashicorp.com/consul-template/${CONSUL_TEMPLATE_VERSION}/consul-template_${CONSUL_TEMPLATE_VERSION}_linux_amd64.zip \
    && sha256sum -c consul-template_${CONSUL_TEMPLATE_VERSION}_SHA256SUMS 2>&1 | grep OK \
    && unzip consul-template_${CONSUL_TEMPLATE_VERSION}_linux_amd64.zip \
    && mv consul-template /bin/consul-template \
    && rm -rf /tmp/* \
    && rm -rf /var/cache/apk/*

ENTRYPOINT ["/bin/consul-template"]
