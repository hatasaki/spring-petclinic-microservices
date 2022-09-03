FROM adoptopenjdk:11-jre-hotspot
ENV SPRING_PROFILES_ACTIVE docker
ARG JAR_FILE=target/*.jar
COPY ${JAR_FILE} app.jar
ARG PORT
EXPOSE ${PORT}
ENTRYPOINT ["java","-jar","/app.jar"]
