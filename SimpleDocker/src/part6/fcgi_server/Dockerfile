FROM nginx:latest
USER root
RUN apt-get update && apt-get install -y \
    gcc \
    libfcgi-dev \
    spawn-fcgi && rm -rf /var/lib/apt/lists
COPY server.c /home/
COPY run.sh /home/
WORKDIR /home/
RUN chmod 777 run.sh ; \
    gcc server.c -lfcgi ; \
    chmod 777 a.out ; \
    touch /var/run/nginx.pid ; \
    chown -R nginx:nginx /var/run/nginx.pid ;
RUN useradd arbokboe;
USER arbokboe

CMD [ "sh", "./run.sh" ]