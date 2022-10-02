FROM openjdk:17-jdk-alpine3.14 as builder
WORKDIR application
ARG JAR_FILE
COPY $JAR_FILE /application/
RUN java -Djarmode=layertools -jar $JAR_FILE extract

FROM openjdk:17-jdk-alpine3.14
WORKDIR application
COPY --from=builder application/dependencies/ ./
COPY --from=builder application/spring-boot-loader/ ./
COPY --from=builder application/snapshot-dependencies/ ./
COPY --from=builder application/application/ ./
EXPOSE 8080
ENTRYPOINT ["java", "-Xms32m", "-Xmx64m", "-XX:OnOutOfMemoryError='kill -9 %p'", "org.springframework.boot.loader.JarLauncher"]
