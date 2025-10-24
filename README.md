# Warehouse Service — E-Commerce Microservice

The **Warehouse Service** is part of a distributed **E-Commerce system** built using **Spring Boot** and **RabbitMQ**.  
It is responsible for **stock control and synchronization**, receiving product updates from the **Storefront Service** and maintaining inventory consistency across the platform.

---

## Tech & Tools
- **Java 21**
- **Spring Boot**
  - Spring Web
  - Spring Data JPA
  - Spring Validation
- **RabbitMQ** (asynchronous communication)
- **MySQL** (persistence layer)
- **Lombok**
- **ModelMapper**
- **Gradle** (project management)

---

## Architecture Overview
The system follows a **microservice architecture**, where each service is independent and communicates via **RabbitMQ** message queues.

**Warehouse responsibilities:**
- Listen for stock update messages from the Storefront through RabbitMQ.
- Update or validate product stock levels.
- Expose REST APIs for stock management and monitoring.
- Persist data in a dedicated MySQL database.

---

## 📁 Project Structure
```bash
src/
└── main/
├── java/br/com/dio/warehouse/
│   ├── config/        # RabbitMQ and environment configuration
│   ├── controller/    # REST controllers (API endpoints)
│   ├── dto/           # Data Transfer Objects
│   ├── entity/        # JPA entities
│   ├── mapper/        # Entity ↔ DTO mappers
│   ├── repository/    # Spring Data repositories
│   └── service/       # Business logic and message consumers
└── resources/
├── application.yml
└── application-dev.yml
```

---

## Getting Started

### Prerequisites
- Java 21+
- Gradle
- MySQL running locally 
- RabbitMQ running locally (default port **5672**)

### Build & Run
```bash
# clone the repository
git clone https://github.com/raphichos/warehouse.git
cd warehouse

# Configure your database and RabbitMQ credentials
src/main/resources/application.yml

# build and run
./gradlew bootRun

# access API endpoints at:
http://localhost:8081/storefront
```

---

## Communication Flow
Storefront Service --(Message: StockStatusMessage)--> [RabbitMQ Queue] --> [Warehouse Service]

---

Developer - Raphael Rios
