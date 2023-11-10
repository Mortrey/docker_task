FROM nginx:alpine

COPY nginx.conf /etc/nginx/nginx.conf

ENTRYPOINT ["nginx", "-g", "daemon off;"]

#CMD ["/bin/sh"] может понадобится при настройке, но тогда нужно будет поменять и энтрипоинт
