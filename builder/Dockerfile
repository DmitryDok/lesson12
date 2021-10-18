FROM ubuntu
ENV TZ=Europe/Minsk
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone
RUN apt update && apt install git default-jdk maven tomcat9 -y
RUN git clone https://github.com/shephertz/App42PaaS-Java-MySQL-Sample.git
WORKDIR /App42PaaS-Java-MySQL-Sample
COPY Config.properties /WebContent/Config.properties
RUN mvn clean && mvn install
RUN cp target/*.war /var/lib/tomcat9/webapps/
CMD ["/bin/sh"]