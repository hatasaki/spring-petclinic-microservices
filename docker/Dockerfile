FROM openjdk:11-jre as builder
WORKDIR application
COPY target/. .
RUN java -Djarmode=layertools -jar application.jar extract

# wget is not installed on adoptopenjdk:11-jre-hotspot
FROM adoptopenjdk:11-jre-hotspot

WORKDIR application

ENV SPRING_PROFILES_ACTIVE docker

COPY --from=builder application/dependencies/ ./
COPY --from=builder application/spring-boot-loader/ ./
COPY --from=builder application/snapshot-dependencies/ ./
COPY --from=builder application/application/ ./
ENTRYPOINT ["java", "org.springframework.boot.loader.JarLauncher"]
