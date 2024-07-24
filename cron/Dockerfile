FROM alpine:3.16

ENV DOCKER_COMPOSE_VERSION 1.29.2

RUN apk update && \
    apk add --no-cache docker-cli curl && \
    curl -L "https://github.com/docker/compose/releases/download/${DOCKER_COMPOSE_VERSION}/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose && \
    chmod +x /usr/local/bin/docker-compose

COPY renew_certs.sh /etc/periodic/daily/renew_certs
RUN chmod +x /etc/periodic/daily/renew_certs

WORKDIR /workdir

CMD ["crond", "-f", "-l", "0"]