FROM ubuntu
ENV TZ=Europe/Minsk
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone
RUN apt update && apt install git default-jdk maven tomcat9 -y
RUN git clone https://github.com/shephertz/App42PaaS-Java-MySQL-Sample.git
RUN grep 'app42.paas.db.username' -P -R -I -l  '/App42PaaS-Java-MySQL-Sample/WebContent/Config.properties' | xargs sed -i 's/app42.paas.db.username = "acp4pogynvaeidfj"/app42.paas.db.username = "user"/g'
RUN grep 'app42.paas.db.port' -P -R -I -l  '/App42PaaS-Java-MySQL-Sample/WebContent/Config.properties' | xargs sed -i 's/app42.paas.db.port = "8514"/app42.paas.db.port = "3306"/g'
RUN grep 'app42.paas.db.password' -P -R -I -l  '/App42PaaS-Java-MySQL-Sample/WebContent/Config.properties' | xargs sed -i 's/app42.paas.db.password = "jc31d2qyy7h9jv5jn1u9uosjksxzaizw"/app42.paas.db.password = "password"/g'
RUN grep 'app42.paas.db.ip' -P -R -I -l  '/App42PaaS-Java-MySQL-Sample/WebContent/Config.properties' | xargs sed -i 's/app42.paas.db.ip = "192.168.2.175"/app42.paas.db.ip = "project_db"/g'
RUN grep 'app42.paas.db.name' -P -R -I -l  '/App42PaaS-Java-MySQL-Sample/WebContent/Config.properties' | xargs sed -i 's/app42.paas.db.name = "dd"/app42.paas.db.name = "mydb"/g'
WORKDIR /App42PaaS-Java-MySQL-Sample
RUN mvn clean && mvn install
RUN cp /App42PaaS-Java-MySQL-Sample/target/*.war /var/lib/tomcat9/webapps/paas.war
EXPOSE 8080
CMD ["/bin/bash"]