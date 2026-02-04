Logger-Generate: Spring Boot CRUD API with SLF4J
A robust Java-based backend service designed to demonstrate professional Logging (SLF4J/Logback), RESTful CRUD operations, and PostgreSQL integration. This project focuses on observability and persistence, ensuring every database transaction is tracked and archived.

🛠️ **Tech Stack**
Language: Java 17

Framework: Spring Boot 3.x

Database: PostgreSQL

ORM: Spring Data JPA (Hibernate)

Logging: SLF4J with Logback (Rolling File Appender)

Utilities: Lombok, Maven

✨ **Features**
Full CRUD Logic: Create, Read, Update, and Delete tasks with permanent storage in PostgreSQL.

Advanced Logging:

Logs are printed to the Console and saved to Rolling Files (./logs).

Profile-based logging: Different log levels for dev (DEBUG) and prod (WARN).

Automated Archiving: Old logs are compressed into .zip files daily to save disk space.

SQL Observability: Real-time Hibernate SQL queries are captured in the logs.

📂** Project Structure**

src/main/java/com/web/logger/
├── controller/    # API Endpoints (TaskController)
├── entity/        # Database Models (Task)
├── repository/    # JPA Data Access (TaskRepository)
└── resources/     
    ├── logback-spring.xml   # Professional Logging Config
    └── application.properties # Environment Configuration


🚀 **Getting Started**
1. Prerequisites
JDK 17 or higher

PostgreSQL installed and running

Maven

2. Database Setup
Create a database in PostgreSQL:

SQL
CREATE DATABASE logger_db;

3. Configuration
Update your src/main/resources/application.properties:

Properties
spring.datasource.url=jdbc:postgresql://localhost:5432/logger_db
spring.datasource.username=your_postgres_user
spring.datasource.password=your_password
spring.profiles.active=dev

4. Run the Application

🚦** API Endpoints** (Testing in Postman)

Method,Endpoint,Description
GET,/api/tasks,Fetch all tasks from DB
POST,/api/tasks,Create a new task (Saves to DB & Logs)
PUT,/api/tasks/{id},Update task status
DELETE,/api/tasks/{id},Remove task (Logs error level)

Sample POST Body:
JSON
{
    "title": "Build a Git Portfolio",
    "completed": false
}

📜 **Logging Example**
The project generates a log file at ./logs/dev-application.log.

Plaintext
2026-02-04 14:26:19 [nio-8080-exec-2] INFO  TaskController - DB OPERATION: Saving new task: Complete Java Logger
2026-02-04 14:26:19 [nio-8080-exec-2] DEBUG org.hibernate.SQL - insert into tasks (completed, title) values (?, ?)

