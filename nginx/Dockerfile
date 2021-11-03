FROM nginx
COPY file* /usr/share/nginx/html/
COPY default.conf /etc/nginx/conf.d
RUN rm -f /usr/share/nginx/html/index.html 
RUN chown nginx:nginx /usr/share/nginx/html/*
