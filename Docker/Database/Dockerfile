# # Use the official MySQL image from Docker Hub
# FROM mysql:8.0

# ARG DB_USER
# ARG DB_PASS

# # Set environment variables
# ENV MYSQL_ROOT_PASSWORD=$DB_PASS
# ENV MYSQL_DATABASE=my_django_db
# ENV MYSQL_USER=$DB_USER
# ENV MYSQL_PASSWORD=$DB_PASS

# EXPOSE 3306



# Use the official MySQL image from Docker Hub
FROM mysql:8.0

# Set environment variables for MySQL
ENV MYSQL_ROOT_PASSWORD=123456789
ENV MYSQL_DATABASE=my_django_db


# Copy the .ibd files into the MySQL data directory
COPY ibd-files/ /var/lib/mysql/

# Set permissions for the MySQL data files
RUN chown -R mysql:mysql /var/lib/mysql && chmod -R 755 /var/lib/mysql

# Expose MySQL default port
EXPOSE 3306
