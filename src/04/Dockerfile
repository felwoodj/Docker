FROM nginx
USER root
COPY server.c /home/
COPY nginx/nginx.conf /etc/nginx/
COPY run.sh /home/
RUN apt update && apt install -y gcc spawn-fcgi libfcgi-dev
WORKDIR /home/
ENTRYPOINT ["sh", "./run.sh"]