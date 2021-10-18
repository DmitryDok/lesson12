FROM tomcat:alpine
RUN mkdir /usr/local/tomcat/ROOT
COPY Config.properties /usr/local/tomcat/ROOT/Config.properties
EXPOSE 8080
CMD ["catalina.sh", "run"]