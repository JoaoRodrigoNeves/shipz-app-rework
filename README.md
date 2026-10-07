# Java Spring Boot Project

Projeto Java/Spring Boot pronto a correr com Docker.

## Arrancar ambiente

```bash
docker compose up -d --build
docker compose exec app bash
```

## Criar projeto Spring Boot

Podes criar o projeto pelo IntelliJ IDEA ou pelo Spring Initializr.

Configuração recomendada:

- Project: Maven
- Language: Java
- Sprint Boot: 4.1.1
- Java: 21
- Packaging: Jar
- Dependencies:
  - Spring Web
  - Spring Data JPA
  - PostgreSQL Driver
  - Flyway Migration
  - Spring Boot Actuator
  - Spring Boot DevTools
  - Validation
  - Lombok, opcional

Depois coloca o conteúdo gerado dentro desta pasta.

## Correr aplicação

Dentro do container:

```bash
mvn spring-boot:run
```

Se o projeto tiver Maven Wrapper:

```bash
./mvnw spring-boot:run
```

A aplicação fica disponível em:

```txt
http://localhost:8080
```

## Comandos úteis

```bash
mvn clean
mvn compile
mvn test
mvn spring-boot:run
mvn clean package
java -jar target/*.jar
```
