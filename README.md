# Kotlin JWT Auth

Production-ready JWT authentication service built with Kotlin and Spring
Boot. Designed with clean architecture principles, secure defaults, and
extensibility in mind.

## Overview

This project implements stateless authentication using JSON Web Tokens
(JWT) with:

-   Secure login & registration flow
-   Role-based authorization
-   Token generation & validation
-   Spring Security configuration
-   Exception handling & API error responses
-   Layered architecture (Controller → Service → Repository)
-   DTO separation and validation

The goal is to demonstrate production-oriented backend practices, not
just JWT wiring.

## Tech Stack

-   Kotlin
-   Spring Boot
-   Spring Security
-   JWT (jjwt / auth0 / configurable)
-   JPA / Hibernate
-   PostgreSQL (configurable)
-   Gradle

## Architecture

The project follows a layered architecture:

controller/ service/ repository/ security/ config/ dto/ exception/
model/

## Key Design Decisions

-   Stateless authentication (no sessions)
-   Password hashing via BCrypt
-   JWT filter integrated into Spring Security filter chain
-   Custom authentication entry point
-   Centralized exception handling
-   Clean separation between domain and transport models

## Authentication Flow

1.  User registers → password hashed and stored
2.  User logs in → credentials validated
3.  JWT issued and returned
4.  Client sends token via Authorization header
5.  Security filter validates token and sets authentication context

## Running Locally

Clone repository:
```sh
      git clone https://github.com/yourusername/kotlin-jwt-auth.git
      cd kotlin-jwt-auth
```

Configure environment (application.yml):
```yaml
       spring: datasource: url: jdbc:postgresql://localhost:5432/authdb
       username: postgres password: postgres
       jwt: secret: your-secure-secret expiration: 3600000
```

Run:
```sh
     ./gradlew bootRun
```

App runs on: **http://localhost:8080**

## API Endpoints
```sh
      Register POST /api/auth/register
      Login POST /api/auth/login
      Protected Endpoint GET /api/users/me Authorization: Bearer
      `<token>`{=html}
```

## Example Request
```sh
      curl -X POST http://localhost:8080/api/auth/login\
           -H "Content-Type: application/json"\
           -d '{"email":"user@example.com","password":"password"}'
```

## Production Improvements (Next Steps)

-   Refresh token implementation
-   Email verification flow
-   Rate limiting
-   Audit logging
-   Dockerization
-   Test coverage (unit + integration)
-   CI pipeline (GitHub Actions)
-   OpenAPI / Swagger documentation

## What This Project Demonstrates

-   Strong understanding of Spring Security internals
-   Stateless authentication architecture
-   Clean code and maintainability
-   Backend security best practices
-   Production-aware configuration

> [!NOTE]
> This repository is part of my backend engineering portfolio and reflects production-oriented security design rather than tutorial-level implementation.
