FROM docker.io/kostakoff/rocky-base-images:8-nodejs20
LABEL layer=3
USER root

# Add docker-cli
RUN dnf -y install docker-ce-cli && \
    groupadd -g 127 github-runner && \
    usermod -aG github-runner appuser

USER appuser
