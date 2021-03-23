# contruccion:
# docker build . -t www.planetaguru.com.ar/cacher

# ejecucion:
# docker run -d -p 3142:3142 --name cacher www.planetaguru.com.ar/cacher

# en los clientes ubuntu:
# sed 's/unix/linux/g' /etc/apt/sources.list

# para el armado de imagenes docker usando un cache
# ejemplo de comando:
# docker build . -t www.planetaguru.com.ar/apache-credi --no-cache --build-arg CACHE_APT="192.168.1.55:3142"

# en Dockerfile's
# ARG CACHE_APT
# RUN if [ "$CACHE_APT" != "" ]; then sed -i "s/archive.ubuntu.com\|ar.archive.ubuntu.com\|archive.canonical.com\|security.ubuntu.com/$CACHE_APT/g" /etc/apt/sources.list; else echo "sin variable CACHE_APT"; fi

# FROM ubuntu:20.04
FROM debian:stable-slim

RUN apt-get update && apt-get install -y apt-cacher-ng && apt-get -y clean && rm -rf /var/lib/apt/lists/* 

EXPOSE 3142

CMD chmod 777 /var/cache/apt-cacher-ng && /etc/init.d/apt-cacher-ng start && tail -f /var/log/apt-cacher-ng/*

