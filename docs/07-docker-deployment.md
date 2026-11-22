
# 7. Docker Containerization

## 7.1 Introduction

Docker is used to package the application and its runtime dependencies into portable container images.

Containerization provides consistency across development, testing, and production environments.

## 7.2 Objectives

- Package applications into Docker images.
- Standardize application runtime environments.
- Simplify application deployment.
- Improve portability.
- Support automated container delivery.

## 7.3 Dockerfile

The Dockerfile defines how the application container image is built.

A simplified Java application example:

```dockerfile
FROM eclipse-temurin:17-jre

WORKDIR /app

COPY target/*.jar app.jar

EXPOSE 8080

ENTRYPOINT ["java", "-jar", "app.jar"]
```

The example assumes that the Maven build produces an executable JAR. Adjust it if your application produces a WAR file or requires Tomcat.

## 7.4 Build Docker Image

```bash
docker build -t end-to-end-devops-platform:1.0 .
```

## 7.5 List Docker Images

```bash
docker images
```

## 7.6 Run Docker Container

```bash
docker run -d \
  --name devops-platform \
  -p 8080:8080 \
  end-to-end-devops-platform:1.0
```

## 7.7 Verify Running Containers

```bash
docker ps
```

## 7.8 View Container Logs

```bash
docker logs devops-platform
```

## 7.9 Stop Container

```bash
docker stop devops-platform
```

## 7.10 Remove Container

```bash
docker rm devops-platform
```

## 7.11 Container Image Publishing

The application image is tagged and pushed to Amazon ECR for deployment to AWS ECS.

## 7.12 Conclusion

Docker provides a consistent and portable way to package applications and simplifies the deployment process across different environments.
