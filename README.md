# Job Portal - Spring Boot REST API

A ready-to-open IntelliJ IDEA backend project for a Job Portal.

## Tech Stack
- Java 21
- Spring Boot 3.4.5
- Spring Web
- Spring Data JPA
- MySQL
- Maven
- Lombok

## Run in IntelliJ IDEA

1. Install JDK 21.
2. Install MySQL 8.x and make sure MySQL Server is running.
3. Open this folder in IntelliJ IDEA.
4. Open `src/main/resources/application.properties`.
5. Change:
   `spring.datasource.password=YOUR_MYSQL_PASSWORD`
   to your MySQL root password.
6. IntelliJ will load Maven dependencies automatically.
7. Run `JobPortalApplication.java`.
8. API base URL: `http://localhost:8080`

The database `job_portal` is created automatically by the JDBC URL.

## Sample Data

The application inserts sample data only when the recruiters table is empty.

Recruiters:
- Rahul Kumar / rahul@technova.com / password123
- Priya Sharma / priya@codecraft.com / password123

Candidates:
- Haritheswari Bheemireddy / haritha@example.com / password123
- Anjali Reddy / anjali@example.com / password123

Jobs:
- Java Backend Developer
- Frontend Developer

## API Endpoints

### Candidates
GET    `/api/candidates`
GET    `/api/candidates/{id}`
POST   `/api/candidates/register`
PUT    `/api/candidates/{id}`

Example registration JSON:
```json
{
  "name": "John Doe",
  "email": "john@example.com",
  "password": "pass123",
  "phone": "9999999999",
  "skills": "Java, SQL",
  "resumeUrl": "https://example.com/resume/john"
}
```

### Recruiters
GET    `/api/recruiters`
GET    `/api/recruiters/{id}`
POST   `/api/recruiters/register`

### Jobs
GET    `/api/jobs`
GET    `/api/jobs/{id}`
GET    `/api/jobs?keyword=Java`
POST   `/api/jobs/recruiter/{recruiterId}`
PUT    `/api/jobs/{id}`
DELETE `/api/jobs/{id}`

Example create job JSON:
```json
{
  "title": "Spring Boot Developer",
  "description": "Build backend services and REST APIs.",
  "location": "Chennai",
  "jobType": "Full Time",
  "salary": "₹5-9 LPA",
  "skills": "Java, Spring Boot, MySQL"
}
```

### Applications
POST `/api/applications/candidate/{candidateId}/job/{jobId}`
GET  `/api/applications/candidate/{candidateId}`
GET  `/api/applications/job/{jobId}`
PATCH `/api/applications/{id}/status?status=SHORTLISTED`

Allowed statuses:
- APPLIED
- SHORTLISTED
- REJECTED
- HIRED

## Important
This is an educational backend project. Authentication is intentionally simplified; passwords are stored as plain text for demo purposes. For a production application, use Spring Security, BCrypt password hashing, JWT/session authentication, DTOs, validation, exception handling, and role-based authorization.
