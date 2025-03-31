# Spring PetClinic Sample Application

### Modified By Lisa-Eileen Odinukwe

[![Java CI with Maven](https://github.com/spring-petclinic/spring-framework-petclinic/actions/workflows/maven-build.yml/badge.svg)](https://github.com/spring-petclinic/spring-framework-petclinic/actions/workflows/maven-build.yml)
[![Quality Gate Status](https://sonarcloud.io/api/project_badges/measure?project=spring-petclinic_spring-framework-petclinic&metric=alert_status)](https://sonarcloud.io/dashboard?id=spring-petclinic_spring-framework-petclinic)

## Overview
This is a **Spring Framework-based** web application following a **3-layer architecture (Presentation → Service → Repository).** It demonstrates how to build and deploy a **Spring Boot + Thymeleaf + MongoDB** application.

## Getting Started

### Clone the Repository
```sh
git clone https://github.com/Lisaeileen/Petclinic.git
cd Petclinic
```

### Run the Application
#### Using Maven
```sh
./mvnw spring-boot:run
```

#### Using Docker
```sh
docker run -p 8080:8080 lisaeileen/spring-petclinic
```
Access the application at: **[http://localhost:8080](http://localhost:8080)**

## Database Configuration
By default, the application runs with an **H2 in-memory database.** You can configure it for **MySQL or PostgreSQL** as follows:

### MySQL Setup
```sh
docker run -e MYSQL_ROOT_PASSWORD=root -e MYSQL_DATABASE=petclinic -p 3306:3306 mysql:5.7.8
./mvnw spring-boot:run -P MySQL
```

### PostgreSQL Setup
```sh
docker run -e POSTGRES_PASSWORD=petclinic -e POSTGRES_DB=petclinic -p 5432:5432 postgres:9.6.0
./mvnw spring-boot:run -P PostgreSQL
```

## Running with Kubernetes
Ensure **Docker & Kubernetes** are running:
```sh
docker build -t lisaeileen/spring-petclinic .
docker push lisaeileen/spring-petclinic
kubectl apply -f k8s-deployment.yml
```

## Deploying with CI/CD
This project supports **GitHub Actions + Docker + Kubernetes** for seamless deployment. To configure, update `.github/workflows/maven-build.yml`.
