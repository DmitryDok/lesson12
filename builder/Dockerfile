FROM ubuntu
ENV TZ=Europe/Minsk
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone
RUN apt update && apt install git default-jdk maven wget -y
RUN git clone https://github.com/shephertz/App42PaaS-Java-MySQL-Sample.git
RUN mvn package -f /App42PaaS-Java-MySQL-Sample/pom.xml
WORKDIR /home/tomcat
RUN wget https://dlcdn.apache.org/tomcat/tomcat-9/v9.0.54/bin/apache-tomcat-9.0.54.tar.gz
RUN tar zxvf apache-tomcat-*.tar.gz -C /home/tomcat --strip-components 1
RUN cp /App42PaaS-Java-MySQL-Sample/target/*.war webapps/
COPY Config.properties ROOT/Config.properties
CMD /home/tomcat/bin/startup.sh