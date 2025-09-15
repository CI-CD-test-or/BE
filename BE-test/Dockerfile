# 최종 실행에 필요한 최소한의 환경만 구성
FROM openjdk:17-jdk-slim

# 작업 디렉터리 설정
WORKDIR /app

# Jenkins 빌드 단계에서 생성된 JAR 파일의 경로를 인자로 받음
ARG JAR_FILE=build/libs/*.jar

# 해당 JAR 파일을 컨테이너 안으로 복사
COPY ${JAR_FILE} app.jar

# 컨테이너 실행 명령어
ENTRYPOINT ["java", "-jar", "app.jar"]
