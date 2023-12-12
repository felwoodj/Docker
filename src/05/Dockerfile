FROM nginx
USER root
WORKDIR /home/
COPY server.c /home/
COPY nginx/nginx.conf /etc/nginx/nginx.conf
COPY run.sh /home/
RUN apt-get update && apt-get install -y gcc spawn-fcgi libfcgi-dev \
    && rm -rf /var/lib/apt/lists \
    && chmod +x run.sh \
    && service nginx start

RUN useradd dockle; \
    && chown -R dockle:dockle /etc/nginx/nginx.conf \
    && chown -R dockle:dockle /var/cache/nginx \
    && chown -R dockle:dockle /home \
    && touch /var/run/nginx.pid \
    && chown -R dockle:dockle /var/run/nginx.pid

USER dockle

ENTRYPOINT ["sh", "./run.sh"]