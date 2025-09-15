# Gradle과 JDK 17이 포함된 이미지를 빌드 전용으로 사용
FROM gradle:8.5-jdk17-jammy AS builder

# 작업 디렉터리 설정
WORKDIR /home/gradle/src

# 소스 코드 전체를 이미지 안으로 복사
COPY . .

# Gradle을 사용하여 프로젝트를 빌드하고, 불필요한 -plain.jar 파일을 삭제
# --no-daemon 옵션은 CI/CD 환경에서 권장됩니다.
RUN gradle build --no-daemon && rm build/libs/*-plain.jar

# 최종 이미지는 애플리케이션 실행에 필요한 최소한의 환경만 포함
FROM openjdk:17-jdk-slim

# 작업 디렉터리 설정
WORKDIR /app

# 빌드 스테이지에서 생성된 실행 가능한 JAR 파일만 복사
COPY --from=builder /home/gradle/src/build/libs/*.jar app.jar

# 컨테이너 실행 명령어
ENTRYPOINT ["java", "-jar", "app.jar"]
