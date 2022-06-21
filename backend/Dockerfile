FROM maven:3.6.0-jdk-11-slim AS build

# ENV MYSQL_ALLOW_EMPTY_PASSWORD=devpass\
#   MYSQL_USER=ums\
#   MYSQL_PASSWORD=dev\
#   MYSQL_DATABASE=devpass

COPY scalable-ums-backend/src /home/app/src

COPY scalable-ums-backend/pom.xml /home/app

RUN mvn -f /home/app/pom.xml clean package

#
# Package stage
#
FROM openjdk:11-jre-slim

COPY --from=build /home/app/target/*.jar /usr/local/lib/demo.jar

EXPOSE 8080
ENTRYPOINT ["java","-jar","/usr/local/lib/demo.jar"]

#reference: https://stackoverflow.com/questions/27767264/how-to-dockerize-maven-project-and-how-many-ways-to-accomplish-it
