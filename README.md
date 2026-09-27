# Student Management API

A small Spring Boot application for student management, built as a course and DevOps practice project. The repository includes a Maven build, Dockerfile, and Jenkins pipeline.

## Requirements

- Java 17 and Maven, or the included Maven wrapper
- MySQL available at `localhost:3306` for the default local configuration

The default database is `studentdb`, with local username `root` and an empty password. Adjust `src/main/resources/application.properties` or supply Spring environment variables for your own MySQL setup. Do not commit database passwords.

## Run

```bash
./mvnw clean verify
./mvnw spring-boot:run
```

The application is configured on port `8089` with context path `/student`. The exact API routes are defined in the source controllers.

## Docker and Jenkins

After `./mvnw package`, build the image with `docker build -t student-management:local .`. The Dockerfile uses Java 17 and exposes port 8089. The image still needs access to a MySQL instance; the default `localhost` database address inside a container refers to that container, so override the datasource URL for your environment.

The Jenkinsfile checks out the configured repository, runs Maven verification, and builds an image. It does not publish the image or deploy the app. Jenkins needs configured Java, Maven, and Docker access.

## Status

This is a learning project. Verify the application's endpoints, database migrations, and tests locally before using it as a deployment example.
