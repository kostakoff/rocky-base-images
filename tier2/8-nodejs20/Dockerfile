FROM docker.io/kostakoff/rocky-base-images:8-default
LABEL layer=2
USER root

RUN dnf -y module reset nodejs && \
    dnf -y module enable nodejs:20 && \
    dnf -y install nodejs

USER appuser
