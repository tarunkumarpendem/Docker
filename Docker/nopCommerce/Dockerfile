FROM mcr.microsoft.com/dotnet/aspnet:6.0
ADD https://github.com/nopSolutions/nopCommerce/releases/download/release-4.50.3/nopCommerce_4.50.3_NoSource_linux_x64.zip .
RUN apt update && \
    apt install unzip -y && \
    unzip ./nopCommerce_4.50.3_NoSource_linux_x64.zip 
CMD [ "dotnet", "Nop.Web.dll", "run", "--server.urls=http://0.0.0.0:*" ]
EXPOSE 80







FROM mcr.microsoft.com/dotnet/sdk:7.0
LABEL author="tarun" organization="qt" project="learning"
ARG user=nopcommerce
ARG group=nopcommerce
ARG uid=1000
ARG gid=1000
ARG DOWNLOAD_URL=https://github.com/nopSolutions/nopCommerce/releases/download/release-4.60.2/nopCommerce_4.60.2_NoSource_linux_x64.zip
ARG HOME_DIR=/nop
RUN apt update && apt install unzip -y
# Create user nopcommerce
RUN groupadd -g ${gid} ${group} \
    && useradd -d "$HOME_DIR" -u ${uid} -g ${gid} -m -s /bin/bash ${user}
USER ${user}
WORKDIR ${HOME_DIR}
ADD --chown=${user}:${group} ${DOWNLOAD_URL} ${HOME_DIR}/nopCommerce_4.60.2_NoSource_linux_x64.zip
RUN unzip ${HOME_DIR}/nopCommerce_4.60.2_NoSource_linux_x64.zip && \
    mkdir ${HOME_DIR}/bin && mkdir ${HOME_DIR}/logs
EXPOSE 5000
ENV ASPNETCORE_URLS="http://0.0.0.0:5000"
CMD [ "dotnet", "Nop.Web.dll"]



# FROM ubuntu:20.04
# RUN apt update && \
#     apt install wget -y && \
#     apt install nginx -y && \
#     service nginx start && \
#     wget https://packages.microsoft.com/config/ubuntu/20.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb && \
#     dpkg -i packages-microsoft-prod.deb && \
#     apt update && \
#     apt-get install -y dotnet-sdk-7.0 && \
#     apt-get install -y apt-transport-https aspnetcore-runtime-7.0 && \
#     dotnet --list-runtimes 
# ADD https://nopcommercefile.s3.amazonaws.com/nginxfile.txt /etc/nginx/sites-available/default
# RUN mkdir /var/www/nopCommerce && \
#     cd /var/www/nopCommerce && \
#     wget https://github.com/nopSolutions/nopCommerce/releases/download/release-4.60.2/nopCommerce_4.60.2_NoSource_linux_x64.zip && \
#     apt install unzip -y && \
#     unzip nopCommerce_4.60.2_NoSource_linux_x64.zip && \
#     mkdir bin && \
#     mkdir logs && \
#     cd .. && \ 
#     chgrp -R www-data nopCommerce/ && \
#     chown -R www-data nopCommerce/
# ADD https://nopcommerce-bucket-25thapril.s3.amazonaws.com/nginxfile3.txt /etc/systemd/system/nopCommerce.service
# RUN service nginx restart
# EXPOSE 80 
# CMD [ "dotnet", "run", "--server.urls=http://0.0.0.0:*" ]






FROM ubuntu:20.04
RUN apt update && \
    apt install wget -y && \
    wget https://packages.microsoft.com/config/ubuntu/20.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb && \
    dpkg -i packages-microsoft-prod.deb && \
    apt-get update && \
    apt-get install -y apt-transport-https aspnetcore-runtime-7.0 && \
    dotnet --list-runtimes && \
    apt-get install nginx -y && \
    service nginx start && \
    service nginx status 
ADD https://nopcommercefile.s3.amazonaws.com/nginxfile.txt /etc/nginx/sites-available/default
RUN mkdir /var/www/nopCommerce && \
    cd /var/www/nopCommerce && \
    wget https://github.com/nopSolutions/nopCommerce/releases/download/release-4.60.2/nopCommerce_4.60.2_NoSource_linux_x64.zip && \
    apt-get install unzip -y && \
    unzip nopCommerce_4.60.2_NoSource_linux_x64.zip && \
    mkdir bin && \
    mkdir logs && \
    cd .. && \
    chgrp -R www-data nopCommerce/ && \
    chown -R www-data nopCommerce/
ADD https://nopcommercefile.s3.amazonaws.com/ngnix2.txt /etc/systemd/system/nopCommerce.service
RUN systemctl restart nginx
EXPOSE 80
CMD [ "dotnet", "run", "http://0.0.0.0:80" ]
    


