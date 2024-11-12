FROM docker.io/kostakoff/rocky-base-images:8-default
LABEL layer=2
USER root

RUN dnf -y install python39 && \
    pip3 install virtualenv

USER appuser
