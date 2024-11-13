FROM docker.io/rockylinux:8
LABEL layer=1
USER root

# default env
ENV JAVA_HOME /etc/alternatives/jre_openjdk

RUN groupadd -g 1001 appuser && \
    useradd -m -u 1001 -g 1001 appuser && \
    mkdir /{app,data,etc/secrets} && \
    chown appuser:appuser /app && \
    chown appuser:appuser /data && \
    chown appuser:appuser /etc/secrets && \
    dnf --enablerepo=powertools -y install ca-certificates

# Add Tini
ENV TINI_VERSION v0.19.0
ADD https://github.com/krallin/tini/releases/download/${TINI_VERSION}/tini /usr/bin/tini
RUN chmod +x /usr/bin/tini

# Add docker-ce repo
ADD https://download.docker.com/linux/centos/docker-ce.repo /etc/yum.repos.d/docker-ce.repo

USER appuser
WORKDIR /app

ENTRYPOINT ["/usr/bin/tini", "--"]
CMD /bin/bash