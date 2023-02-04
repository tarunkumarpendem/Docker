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