FROM tomcat:latest

LABEL maintainer="Adria Juan de Leon"

COPY ./target/LoginWebApp.war /usr/local/tomcat/webapps/

EXPOSE 8080

CMD ["catalina.sh", "run"]