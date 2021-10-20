FROM ubuntu
ENV TZ=Europe/Minsk
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone
RUN apt update && apt install git default-jdk maven -y
RUN git clone https://github.com/shephertz/App42PaaS-Java-MySQL-Sample.git
WORKDIR /App42PaaS-Java-MySQL-Sample
RUN sed -i 's/5.1.8/8.0.27/g' pom.xml
RUN mvn package