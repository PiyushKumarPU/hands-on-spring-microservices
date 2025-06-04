# 🏗️ Phase 1: Foundational Setup PRD

## 🎯 Objective
Establish the foundational infrastructure required for a Spring Boot microservices ecosystem. This includes centralized configuration, service discovery, gateway routing, and containerized deployment.

---

## 🧱 Components

### 1. Git Multi-Module Repository Structure

#### Goal
Organize services as independent Gradle modules within a single Git repository.

#### Structure
```
ecommerce-microservices/
├── build.gradle (parent)
├── settings.gradle
├── config-server/
├── discovery-server/
├── api-gateway/
└── (other services added later)
```

---

### 2. Spring Cloud Config Server

#### Goal
Externalize configuration using Git as a configuration source.

#### Features
- Bootstrap config from Git
- YAML-based profiles (e.g. `application-dev.yml`, `application-prod.yml`)
- `@RefreshScope` support for runtime updates

#### Example Git config repo
```
config-repo/
├── application.yml
├── user-service.yml
├── product-service.yml
└── api-gateway.yml
```

---

### 3. Eureka Service Registry

#### Goal
Enable service discovery and dynamic routing for all microservices.

#### Features
- Register all services with Eureka
- Each service is configured with `eureka.client.service-url.defaultZone`

---

### 4. Spring Cloud Gateway

#### Goal
Acts as the entry point and intelligent router for all client requests.

#### Features
- Auto route to Eureka-registered services
- Configuration fetched from Config Server
- Enable route filters, predicates

#### Example Route Configuration
```yaml
spring:
  cloud:
    gateway:
      routes:
        - id: user-service
          uri: lb://user-service
          predicates:
            - Path=/api/users/**
```

---

### 5. Dockerization

#### Goal
Enable consistent local and remote deployment using Docker.

#### Components Dockerized:
- config-server
- discovery-server
- api-gateway

#### Sample Docker Compose Skeleton
```yaml
version: '3.8'
services:
  config-server:
    build: ./config-server
    ports:
      - "8888:8888"

  discovery-server:
    build: ./discovery-server
    ports:
      - "8761:8761"

  api-gateway:
    build: ./api-gateway
    ports:
      - "8080:8080"
```

---

## ✅ Deliverables

- Git repo structure initialized with `settings.gradle` and module includes.
- Config Server setup to pull from a Git-based config repo.
- Eureka Server is up and running with service registration enabled.
- Gateway fetches configuration from Config Server and dynamically routes using Eureka.
- All three foundational services are Dockerized and available via Docker Compose.
- One dummy route is configured and working end-to-end (e.g., `GET /api/dummy` → returns test response).

---

## 🛠️ Tools & Frameworks

| Area              | Tech                        |
|-------------------|-----------------------------|
| Config Management | Spring Cloud Config         |
| Service Discovery | Spring Cloud Eureka         |
| Gateway Routing   | Spring Cloud Gateway        |
| Build Tool        | Gradle                      |
| Containerization  | Docker, Docker Compose      |
| Git Repo for Config | Spring Config Server + Git |