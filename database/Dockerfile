#How can i write a dockerfile for mysql/mysql-server:5.7 with high security and low size?
FROM mysql/mysql-server:5.7
# Set environment variables for MySQL
ENV MYSQL_ROOT_PASSWORD=root
ENV MYSQL_USER=root
# Reduce image size by removing unnecessary files
RUN apt-get clean && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*
# Set MySQL configuration for enhanced security

COPY my.cnf /etc/mysql/conf.d/my.cnf
RUN chmod 644 /etc/mysql/conf.d/my.cnf
# Expose only necessary ports
EXPOSE 3306
COPY database.sql /docker-entrypoint-initdb.d/database.sql 
# Use a non-root user to run MySQL
USER mysql
# Start MySQL server
CMD ["mysqld"]
# Note: Ensure to create a secure my.cnf file with appropriate security settings.
# Example my.cnf settings could include:
# [mysqld]      
# skip-symbolic-links
# sql-mode=STRICT_ALL_TABLES            
# local-infile=0
# bind-address= 
#   
# Remember to replace placeholder values with secure and appropriate ones for your use case.                
