FROM docker.io/kostakoff/rocky-base-images:8-python3.9
LABEL layer=3
USER root

RUN dnf -y install git rsync sshpass && \
    pip3 install ansible

USER appuser
