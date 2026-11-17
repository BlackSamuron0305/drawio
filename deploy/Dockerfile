# Self-hosted draw.io: serves the prebuilt web app in src/main/webapp with nginx.
# Build from the repository root: docker build -f deploy/Dockerfile .
FROM nginx:1.27-alpine
COPY deploy/nginx.conf /etc/nginx/conf.d/default.conf
COPY src/main/webapp /usr/share/nginx/html
# Java servlet metadata is not used by the static app and should not be served.
RUN rm -rf /usr/share/nginx/html/WEB-INF /usr/share/nginx/html/META-INF
EXPOSE 80
HEALTHCHECK --interval=30s --timeout=5s CMD wget -q -O /dev/null http://127.0.0.1/ || exit 1
