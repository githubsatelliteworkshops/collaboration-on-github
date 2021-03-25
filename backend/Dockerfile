FROM ubuntu
WORKDIR /
RUN apt-get -y upgrade && apt-get -y update
RUN apt install -y openjdk-11-jre-headless
RUN apt install -y maven
ADD . .
RUN mvn clean install
RUN java /src/main/java/github/App.java
