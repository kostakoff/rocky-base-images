FROM docker.io/rocky-base-images:8-default
LABEL layer=2
USER root

RUN dnf -y module reset nginx && \
    dnf -y module enable nginx 1.22 && \
    dnf install nginx

# https://github.com/nginxinc/docker-nginx-unprivileged/blob/main/stable/alpine-slim/Dockerfile#L111
RUN ln -sf /dev/stdout /var/log/nginx/access.log && \
    ln -sf /dev/stderr /var/log/nginx/error.log && \
    chown -R appuser:appuser /var/cache/nginx && \
    chmod -R g+w /var/cache/nginx && \
    chown -R appuser:appuser /etc/nginx && \
    chmod -R g+w /etc/nginx

USER appuser

CMD ["nginx", "-g", "daemon off;"]

EXPOSE 8080