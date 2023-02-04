FROM mcr.microsoft.com/dotnet/aspnet:6.0
ADD https://github.com/nopSolutions/nopCommerce/releases/download/release-4.50.3/nopCommerce_4.50.3_NoSource_linux_x64.zip .
RUN apt update && \
    apt install unzip -y && \
    unzip ./nopCommerce_4.50.3_NoSource_linux_x64.zip 
CMD [ "dotnet", "Nop.Web.dll", "run", "--server.urls=http://0.0.0.0:*" ]
EXPOSE 80


