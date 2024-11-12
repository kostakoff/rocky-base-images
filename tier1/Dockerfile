FROM docker.io/rockylinux:8
LABEL layer=1
USER root

# default env
ENV JAVA_HOME /etc/alternatives/jre_openjdk

RUN groupadd -g 1001 appuser && \
    useradd -m -u 1001 -g 1001 appuser && \
    mkdir /{app,data} && \
    chown appuser:appuser /app && \
    chown appuser:appuser /data && \
    dnf --enablerepo=powertools -y install ca-certificates

# Add Tini
ENV TINI_VERSION v0.19.0
ADD https://github.com/krallin/tini/releases/download/${TINI_VERSION}/tini /usr/bin/tini
RUN chmod +x /usr/bin/tini

USER appuser
WORKDIR /app

ENTRYPOINT ["/usr/bin/tini", "--"]
CMD /bin/bash