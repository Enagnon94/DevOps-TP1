# our base image
FROM postgres:11.6-alpine 

ENV POSTGRES_DB=db POSTGRES_USER=usr POSTGRES_PASSWORD=pwd
#COPY docker-entrypoint-initdb.d /home/enagnon/Bureau/DevOps-TP1/
COPY docker-entrypoint-initdb.d/*.sql /docker-entrypoint-initdb.d/

