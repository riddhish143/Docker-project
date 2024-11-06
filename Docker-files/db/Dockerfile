# Use MySQL 8.0.33 as the base image
FROM mysql:8.0.33

# Add metadata labels
LABEL "Project"="Application"
LABEL "Author"="Riddhish"

# Set environment variables for MySQL configuration
ENV MYSQL_ROOT_PASSWORD="vprodbpass"
ENV MYSQL_DATABASE="accounts"

# Add the database backup file to the MySQL initialization directory
ADD db_backup.sql /docker-entrypoint-initdb.d/db_backup.sql
