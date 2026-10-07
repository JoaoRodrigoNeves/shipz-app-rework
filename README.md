# Shipz — Spring Boot + Angular

A full-stack application built with **Spring Boot, Angular, and PostgreSQL**, configured for development using Docker and Dev Containers.

## Technology Stack

- **Backend:** Java 21 + Spring Boot 4.1.1
- **Frontend:** Angular 22 + TypeScript
- **Database:** PostgreSQL 18
- **Build tools:** Maven + npm
- **Development environment:** Docker + Docker Compose

## Start the Development Environment

```bash
docker compose up -d --build
docker compose exec app bash
```

## Create the Spring Boot Project

You can generate the project using IntelliJ IDEA or Spring Initializr.

Recommended configuration:

- **Project:** Maven
- **Language:** Java
- **Spring Boot:** 4.1.1
- **Java:** 21
- **Packaging:** Jar
- **Dependencies:**
  - Spring Web
  - Spring Data JPA
  - PostgreSQL Driver
  - Flyway Migration
  - Spring Boot Actuator
  - Spring Boot DevTools
  - Validation
  - Lombok (optional)

Place the generated project inside the `shipz-api/` directory.

## Create the Angular Project

Inside the Dev Container:

```bash
cd /workspace

npx @angular/cli@22 new frontend \
  --routing \
  --style=scss \
  --standalone \
  --ssr=false \
  --strict \
  --skip-git
```

The Angular application will be created inside the `frontend/` directory.

## Project Structure

```text
shipz/
├── .devcontainer/
│   └── devcontainer.json
├── shipz-api/
│   ├── src/
│   ├── pom.xml
│   └── mvnw
├── frontend/
│   ├── src/
│   ├── angular.json
│   └── package.json
├── docker-compose.yml
├── Dockerfile
├── .env
└── README.md
```

## Run the Application

### Backend — Spring Boot

Inside the Dev Container:

```bash
cd /workspace/shipz-api
./mvnw spring-boot:run
```

Alternatively:

```bash
mvn spring-boot:run
```

The backend will be available at:

`http://localhost:8080`

### Frontend — Angular

Open a second terminal inside the Dev Container:

```bash
cd /workspace/frontend
npm install
npm start -- --host 0.0.0.0
```

The frontend will be available at:

`http://localhost:4200`

## Angular ↔ Spring Boot Communication

The Angular frontend communicates with the Spring Boot backend through a REST API.

During development, using an Angular proxy is recommended to forward `/api` requests to `http://localhost:8080`, avoiding unnecessary CORS configuration.

## Useful Commands

### Maven

```bash
mvn clean
mvn compile
mvn test
mvn spring-boot:run
mvn clean package
java -jar target/*.jar
```

### Angular

```bash
npm install
npm start -- --host 0.0.0.0
npm run build
npm test
npx ng generate component component-name
npx ng generate service service-name
```

### Docker

```bash
docker compose up -d --build
docker compose ps
docker compose logs -f
docker compose exec app bash
docker compose down
```

## Service Ports

| Service | Port |
|---|---|
| Spring Boot | 8080 |
| Angular | 4200 |
| PostgreSQL | 5432 |

Ports 8080 and 4200 must be exposed in `docker-compose.yml` and configured in `devcontainer.json`.

## Development Workflow

Both the backend and frontend are developed inside the same Dev Container, sharing the tools installed in the development environment.

PostgreSQL runs in a separate container managed by Docker Compose.

This setup provides a reproducible full-stack development environment without requiring Java, Maven, Node.js, or PostgreSQL to be installed directly on the host machine.