## Writing Dockerfiles for setting up GitHub Packages

### Dockerfile for React Application

```Dockerfile
FROM    node:10-alpine 
WORKDIR /usr/src/app
COPY    . .
RUN     npm install
EXPOSE  3000
CMD     [ "npm", "start" ]
```

### Dockerfile for Maven Application

```Dockerfile
FROM ubuntu
WORKDIR /
RUN apt-get -y upgrade && apt-get -y update
RUN apt install -y openjdk-11-jre-headless
RUN apt install -y maven
ADD . .
RUN mvn clean install
RUN java /src/main/java/github/App.java
```