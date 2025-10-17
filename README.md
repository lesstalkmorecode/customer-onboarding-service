# Customer Onboarding Service (Sample Project)

## Overview
This repository provides the foundation for a **Customer Onboarding Service** in the banking domain.  
It demonstrates how a digital onboarding process can be implemented - including data collection, validation, and future extensions for identity verification and account creation.  
The project follows a modular, production-oriented structure using **Spring Boot 3** and **Java 21**.

---

## Architecture
```
customer-onboarding-service/
├── api/     → OpenAPI contract (
└── impl/    → Spring Boot implementation (REST controllers, services, etc.)
```

- **api** module → defines the OpenAPI contract and interface stubs
- **impl** module → contains the application logic, configuration, and REST entry points
- The structure is ready for later addition of `docker/`, `infra/`, or persistence layers.

---

## Tech Stack
- **Java 21**
- **Spring Boot 3.5.6**
- **Maven Wrapper**
- **Docker (OpenJDK 21 slim base image)**
- **JUnit 5**
- **Spotless** (code formatting)

> Note: This is a sample project; no real banking data or secrets are included.

---

## Build & Run (Local)

### Build
```bash
mvn clean verify
```

### Run
```bash
mvn -f impl\pom.xml spring-boot:run
```
The application starts on **http://localhost:8080** by default.

---

## Docker (Simple Runtime Image)

This project uses a **simple runtime Dockerfile** that expects a pre-built JAR under `target/`:

### Build the JAR, then build the image
```bash
mvn clean verify
docker build -t customer-onboarding-service:dev .
```

### Run the container
```bash
docker run --rm -p 8080:8080 customer-onboarding-service:dev
```
---

## Project Status

- Project skeleton compiles and runs.
- Business logic, persistence, and resilience patterns will be added iteratively.
- No secrets are stored in source control.

---

## Next Steps (Roadmap)
1. Introduce Docker and environment configuration
2. Integrate PostgreSQL as persistence layer
3. Implement REST APIs for customer onboarding
4. Add rate limiting, idempotency, and fault tolerance
5. Add authentication
6. Extend unit and integration test coverage

---