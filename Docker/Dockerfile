# postgre db
FROM postgres:15
LABEL Author = Tarun
LABEL Version = 15
ENV POSTGRES_USER = postgres 
ENV POSTGRES_PASSWORD = postgres 
ENV POSTGRES_DB = postgres
EXPOSE 5432   
CMD [ "postgres" ]

# mysql db
FROM mysql:8.0.31
LABEL Author = Tarun
LABEL Version = 15
EXPOSE 3306
ENV MYSQL_ROOT_PASSWORD = mysql
ENV MYSQL_DATABASE = mysql_db
ENV MYSQL_USER = mysql_user
ENV MYSQL_PASSWORD = mysql_password
CMD ["mysqld"]

# Game of life
FROM tomcat:8-jdk8
EXPOSE 8080
ADD https://referenceapplicationskhaja.s3.us-west-2.amazonaws.com/gameoflife.war /usr/local/tomcat/webapps/gameoflife.war 
CMD ["catalina.sh", "run"]

#nopCommerce
FROM mcr.microsoft.com/dotnet/aspnet:6.0
ADD https://github.com/nopSolutions/nopCommerce/releases/download/release-4.50.3/nopCommerce_4.50.3_NoSource_linux_x64.zip .
RUN apt update && \
    apt install unzip -y && \
    unzip ./nopCommerce_4.50.3_NoSource_linux_x64.zip 
CMD [ "dotnet", "Nop.Web.dll", "run", "--server.urls=http://0.0.0.0:*" ]
EXPOSE 80

#openmrs
FROM tomcat:8.5.84-jdk11
RUN apt update \
    && apt install git maven -y \
    && git clone https://github.com/openmrs/openmrs-core.git \
    && cd openmrs-core \
    && mvn clean package \
    && cp /home/ubuntu/openmrs-core/webapp/target/openmrs.war /usr/local/tomcat/webapps/openmrs.war   
EXPOSE 8080
CMD ["catalina.sh", "run"]

FROM tomcat:8.5.84-jdk11
RUN apt update \
    && apt install git maven -y \
    && git clone https://github.com/openmrs/openmrs-core.git \
    && cd openmrs-core \
    && mvn clean package 
WORKDIR /home/ubuntu/openmrs-core/webapp/target 
ADD /home/ubuntu/openmrs-core/webapp/target/openmrs.war /usr/local/tomcat/webapps/openmrs.war   
EXPOSE 8080
CMD ["catalina.sh", "run"]


# spring petclinic
FROM ubuntu:20.04
RUN apt update \
    && apt install openjdk-11-jdk wget -y \
    && wget https://referenceapplicationskhaja.s3.us-west-2.amazonaws.com/spring-petclinic-2.4.2.jar 
EXPOSE 8080
CMD ["java", "-jar", "/spring-petclinic-2.4.2.jar"]
#ENTRYPOINT ["java", "-jar", "/spring-petclinic-2.4.2.jar"]

FROM amazoncorretto:11
ADD https://referenceapplicationskhaja.s3.us-west-2.amazonaws.com/spring-petclinic-2.4.2.jar .
EXPOSE 8080
CMD ["java", "-jar", "/spring-petclinic-2.4.2.jar"]











