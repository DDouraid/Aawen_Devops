# Aawen DevOps

Simple Maven project configured for DevOps pipelines.

## Prerequisites

- Java 11+
- Maven 3.6+
- Docker (optional)
- Jenkins (optional)

## Build

```bash
./mvnw clean package
```

## Run

```bash
java -jar target/Aawen_Devops-1.0-SNAPSHOT.jar
```

## Docker

Build and run with Docker:

```bash
docker build -t aawen-devops-app .
docker run -p 8080:8080 aawen-devops-app
```

Or use docker-compose:

```bash
docker-compose up
```

## CI/CD

This project includes a `Jenkinsfile` for Jenkins CI/CD pipeline.

