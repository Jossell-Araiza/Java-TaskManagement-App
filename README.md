# Java Task Management App

A full-stack task management application demonstrating Java, Spring Boot, React, and PostgreSQL for a Junior Java Software Engineer role.

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
