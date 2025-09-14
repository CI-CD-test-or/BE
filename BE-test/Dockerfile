# 1. Java 17 이미지를 기반으로 사용
FROM openjdk:17-jdk-slim

# 2. Jar 파일 경로 지정 (Gradle은 build/libs/*.jar)
ARG JAR_FILE=build/libs/*.jar

# 3. Jar 파일을 컨테이너 안으로 복사
COPY ${JAR_FILE} app.jar

# 4. 컨테이너 실행 시 실행할 명령어
ENTRYPOINT ["java", "-jar", "/app.jar"]
