FROM nginx:alpine

COPY conf.d /etc/nginx/conf.d

LABEL maintainer="NGINX Docker Maintainers <docker-maint@nginx.com>"

ENV TZ "Asia/Shanghai"

ENV NGINX_VERSION   1.19.1

EXPOSE 80 443

CMD ["nginx", "-g", "daemon off;"]
