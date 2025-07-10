# Java Task Management App

A full-stack web application for managing tasks, built with Java (Spring Boot), React, and PostgreSQL.

Overview

This project is a task management application that allows users to register, log in, and perform CRUD operations on tasks. It includes secure authentication with password hashing and user-specific task management.

<<<<<<< HEAD
Tech Stack





Backend: Java, Spring Boot, Spring Security, Spring Data JPA



Frontend: React (JavaScript)



Database: PostgreSQL



Build Tool: Maven



Other: Git for version control

Features





User authentication (register and login) with hashed passwords (AuthController.java, SecurityConfig.java).



Task CRUD operations (create, read, update, delete) restricted to authenticated users (TaskController.java).



User and task entities with database persistence (User.java, Task.java).



Global exception handling for better error management (GlobalExceptionHandler.java).



Basic frontend interface with mock data (frontend/src/App.js).



Database schema setup (schema.sql).

Setup Instructions

Prerequisites





Java 17



Maven



Node.js and npm (for the frontend)



PostgreSQL (or another compatible database)

Backend Setup





Clone the repository:

git clone https://github.com/Jossell-Araiza/Java-TaskManagement-App.git
cd task-management-app



Configure the database:





Create a PostgreSQL database named taskdb.



Run the provided schema.sql to set up tables:

psql -U postgres -d taskdb -f schema.sql



Update src/main/resources/application.properties with your database credentials:

spring.datasource.url=jdbc:postgresql://localhost:5432/taskdb
spring.datasource.username=postgres
spring.datasource.password=${DB_PASSWORD}
spring.jpa.hibernate.ddl-auto=update
server.port=8082



Build the project:

mvn clean install



Run the backend:

mvn spring-boot:run





Note: The server is configured to run on port 8082 to avoid conflicts. If issues arise, check for port availability or update server.port.

Frontend Setup





Navigate to the frontend directory:

cd frontend



Install dependencies:

npm install



Start the frontend:

npm start





The frontend runs on http://localhost:3000 and currently uses mock data.

Database Setup





Ensure schema.sql is executed to create users and tasks tables with sample data:

CREATE TABLE users (
    id BIGSERIAL PRIMARY KEY,
    username VARCHAR(255) NOT NULL,
    password VARCHAR(255) NOT NULL
);

CREATE TABLE tasks (
    id BIGSERIAL PRIMARY KEY,
    title VARCHAR(255) NOT NULL,
    description TEXT,
    due_date DATE,
    status VARCHAR(50),
    user_id BIGINT,
    FOREIGN KEY (user_id) REFERENCES users(id)
);

INSERT INTO users (username, password) VALUES ('testuser', 'password123');
INSERT INTO tasks (title, description, due_date, status, user_id)
VALUES ('Sample Task', 'Do something', '2025-07-15', 'PENDING', 1);

Usage





API Endpoints:





/api/auth/register: Register a new user (POST).



/api/auth/login: Log in a user (POST).



/api/tasks: Get tasks for the authenticated user (GET).



/api/tasks: Create a new task (POST).



/api/tasks/{id}: Update or delete a task (PUT, DELETE).



Frontend: Displays a mock task list at http://localhost:3000. Integration with the backend API is in progress.

Project Status





Backend: Implemented with secure authentication and task management. Not yet fully tested due to port conflicts.



Frontend: Basic React app with mock data, ready for API integration.



Database: Schema and sample data set up.



Testing: Basic test included (TaskManagementApplicationTests.java).

Contributing





Fork the repository.



Create a feature branch: git checkout -b feature/your-feature.



Commit changes: git commit -m "Add your feature".



Push to your fork: git push origin feature/your-feature.



Submit a pull request.

License

MIT License (update if applicable).

Next Steps





Resolve port conflicts for full backend testing.



Integrate the frontend with the backend API using Axios.



Add unit and integration tests for controllers.



Deploy the application to a cloud platform (e.g., Heroku, AWS).
=======
## Tech Stack
- **Backend**: Java 17, Spring Boot, Spring Security, Spring Data JPA, Maven
- **Frontend**: React, JavaScript, Tailwind CSS
- **Database**: PostgreSQL
- **Cloud**: AWS SDK for S3 (planned), Heroku-ready configuration

## Setup
1. **Backend**:
    ```bash
    git clone https://github.com/Jossell-Araiza/Java-TaskManagement-App.git
    cd task-management-app
    psql -U postgres -d taskdb -f src/main/resources/schema.sql
    ```

    Update `src/main/resources/application.properties`:
    ```properties
    spring.datasource.url=jdbc:postgresql://localhost:5432/taskdb
    spring.datasource.username=postgres
    spring.datasource.password=${DB_PASSWORD}
    spring.jpa.hibernate.ddl-auto=update
    server.port=8082
    ```

    Build and run the backend:
    ```bash
    mvn clean install
    mvn spring-boot:run
    ```

2. **Frontend**:
    ```bash
    cd frontend
    npm install
    npm start
    ```

3. Open `http://localhost:3000`.

## Features
- Secure user authentication with password hashing (`AuthController.java`).
- CRUD operations for user-specific tasks (`TaskController.java`).
- Persistent data storage with PostgreSQL (`User.java`, `Task.java`).
- Robust error handling (`GlobalExceptionHandler.java`).
- Responsive React UI with mock data (`frontend/src/App.js`).

## AWS Integration
- **AWS SDK**: Planned integration with `software.amazon.awssdk.s3` for file uploads (to be implemented in `TaskController.java`).
- **Local Fallback**: Tasks stored in PostgreSQL without file attachments.
- **Heroku / AWS**:
  - Backend deployable via `Procfile` (Heroku) or `.ebextensions/options.config` (Elastic Beanstalk).
  - Frontend planned for deployment on Netlify or AWS S3.
  - PostgreSQL database hosted on Heroku or AWS RDS.
  - Use environment variables or `application.properties` to configure `DB_PASSWORD` and AWS credentials.

## Skills Demonstrated
- **Java/Spring Boot**: RESTful API with Spring Security and JPA.
- **SQL**: PostgreSQL schema design and queries.
- **JavaScript/React**: Dynamic UI with mock task data.
- **Tools**: Maven for builds, Git for version control, Heroku/AWS for deployment.

## Notes
- Developed on July 10, 2025, by Jossell Araiza.
- Open-source under MIT License.
- Backend currently running on port `8082` (changeable in `application.properties`).
- Planned enhancements:
  - Connect frontend to backend using Axios.
  - Add unit and integration tests with JUnit and Mockito.
  - Complete cloud deployment to Heroku or AWS.
>>>>>>> f89ae34 (Updated README.md for professional GitHub rendering)
