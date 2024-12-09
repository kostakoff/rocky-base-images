# original source https://catalog.redhat.com/software/containers/ubi8/httpd-24/6065b844aee24f523c207943?container-tabs=dockerfile
FROM docker.io/kostakoff/rocky-base-images:8-default
LABEL layer=2
USER root

RUN dnf -y module reset httpd && \
    dnf -y module enable httpd:2.4 && \
    INSTALL_PKGS="gettext hostname nss_wrapper bind-utils httpd mod_ssl mod_ldap mod_session mod_security mod_auth_mellon sscg" && \
    dnf -y install --setopt=tsflags=nodocs $INSTALL_PKGS && \
    rpm -V $INSTALL_PKGS && \
    httpd -v && \
    yum -y clean all --enablerepo='*'

USER appuser

CMD exec httpd -D FOREGROUND

EXPOSE 8080
EXPOSE 8443

#draft