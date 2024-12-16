# Use the official MySQL image from Docker Hub
FROM mysql:8.0

ARG DB_USER
ARG DB_PASS

# Set environment variables
ENV MYSQL_ROOT_PASSWORD=$DB_PASS
ENV MYSQL_DATABASE=my_django_db
ENV MYSQL_USER=$DB_USER
ENV MYSQL_PASSWORD=$DB_PASS

COPY my_django_db.sql /docker-entrypoint-initdb.d/

EXPOSE 3306

