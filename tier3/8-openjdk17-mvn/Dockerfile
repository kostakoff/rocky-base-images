FROM docker.io/kostakoff/rocky-base-images:8-openjdk17
LABEL layer=3
USER root

# Add Maven
ENV MVN_VERSION 3.9.9
ADD https://dlcdn.apache.org/maven/maven-3/${MVN_VERSION}/binaries/apache-maven-${MVN_VERSION}-bin.tar.gz /tmp/
RUN mkdir -p /opt/mvn && \
    tar xzvf /tmp/apache-maven-${MVN_VERSION}-bin.tar.gz -C /opt/mvn --strip-components=1 && \
    rm /tmp/apache-maven-${MVN_VERSION}-bin.tar.gz && \
    chmod +x /opt/mvn/bin/mvn && \
    ln -s /opt/mvn/bin/mvn /usr/bin/mvn && \
    mvn --version

USER appuser
