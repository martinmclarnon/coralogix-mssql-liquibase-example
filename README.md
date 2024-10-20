# Demo Blog Service

This project demonstrates a simple blog service using Kotlin, Spring Boot, and JPA. It includes a REST API for retrieving blog posts from a database, with pagination support. The project also includes configuration for testing with Cucumber, JUnit, and Mockito.

## Table of Contents
- [Getting Started](#getting-started)
- [Requirements](#requirements)
- [API Overview](#api-overview)
- [Running the Application](#running-the-application)
- [Tiltfile Setup](#to-use-the-tiltfile)
- [Testing](#testing)
- [License](#license)

## Getting Started

This project uses Kotlin, Spring Boot, and JPA to create a simple blog service. The application exposes a REST API to list blog posts, and it is configured for local development and testing.

### Requirements

- Java 17 or later
- Kotlin 1.9.25 or later
- Spring Boot 3.3.4
- A running instance of a SQL Server database
- Maven Central for dependency management

### Installing Dependencies

The required dependencies are listed in the `build.gradle.kts` file and include the following key libraries:

- Spring Boot Starter Data JPA
- Spring Boot Starter Web
- Jackson Module Kotlin
- Microsoft SQL Server JDBC Driver
- Cucumber for BDD testing
- JUnit for unit testing
- Mockito for mocking in tests

You can build the project and install dependencies with:

```bash
./gradlew build
```

### API Overview

```bash
GET /v1/vqjc110wa0tel38k75lw
```

This API endpoint returns a paginated list of blogs.

Parameters:
size (optional): Number of blog entries to return (default is 10).
page (optional): Page number to return (default is 0).

Response:
HTTP Status: 200 OK
Response Body: JSON object containing the list of blog posts.

```json
{
  "code": 200,
  "status": "OK",
  "data": [
    {
      "id": "12345",
      "post": "Sample blog post content"
    }
  ]
}
```


### Tiltfile Setup

Utilising Tilt, this example will connect to an Azure MSSQL DB and then update using Liquibase Scripts.

#### Tilt Prerequisites

To run local Kubernetes cluster in Docker:
```bash
$ brew install kind
```

To define your dev environment as code:
```bash
$ brew install tilt
```
#### Local CICD

Run the following commands:
```bash
$ kind create cluster
```

At the root of the Tiltfile. The argument --stream will output logs
```bash
tilt up --stream
```
To view Tilt dashboard, navigate to;
```bash
http://localhost:10350
```


```shell
curl http://localhost:8081/q824phylj42i77kdpvrq/v1/vqjc110wa0tel38k75lw
```


### Testing

This project is configured for behaviour-driven development (BDD) using Cucumber and unit testing with JUnit. Mocking is handled by Mockito.

Running Unit Tests
To run the unit tests, use the following command:

```bash
./gradlew test
```

Running BDD Tests
To execute the Cucumber tests, use:

```bash
./gradlew execute-bdd-tests
```
This will run all feature files located in src/test/resources/features.

### License
This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.