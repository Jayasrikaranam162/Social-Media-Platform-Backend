# Karanam Jayasri, Roll No. 23

# Social Media Backend

Spring Boot backend for a social media application with authentication, user profiles, posts, comments, and likes.

## Tech Stack

- Java 17
- Spring Boot 4
- Spring Web, Spring Security, Spring Data JPA
- PostgreSQL
- JWT authentication
- Maven

## Features

- User registration and login
- Email verification flow
- JWT-based authentication
- User listing and profile fetch
- Create/list/delete posts
- Add/list comments for posts
- Like posts
- Health check endpoints

## Project Structure

- `src/main/java/com/socialmedia/socialmediabackend` - main application code
- `src/main/resources/application.properties` - application config
- `src/test/java/com/socialmedia/socialmediabackend` - tests

## Prerequisites

- Java 17 or higher
- Maven 3.9+ (or use `mvnw` / `mvnw.cmd`)
- PostgreSQL running locally

## Environment Configuration

Copy values from `.env.example` or set environment variables directly.

Key variables used by `src/main/resources/application.properties`:

- `DB_URL` (default: `jdbc:postgresql://localhost:5432/social_media`)
- `DB_USERNAME` (default: `postgres`)
- `DB_PASSWORD` (default: `postgres`)
- `APP_JWT_SECRET` (set a strong secret, at least 32 bytes)
- `APP_JWT_EXPIRATION_MS` (default: `86400000`)
- `MAIL_HOST`, `MAIL_PORT`, `MAIL_USERNAME`, `MAIL_PASSWORD`
- `APP_BASE_URL` (default: `http://localhost:8081`)
- `NOTIFICATION_SERVICE_URL`
- `ANALYTICS_SERVICE_URL`
- `PROFILE_SERVICE_URL`
- `MODERATION_SERVICE_URL`
- `APP_BOOTSTRAP_ADMIN_ENABLED`
- `APP_BOOTSTRAP_ADMIN_EMAIL`
- `APP_BOOTSTRAP_ADMIN_PASSWORD`

## Run Locally

### Windows (PowerShell)

```powershell
./mvnw.cmd spring-boot:run
```

### Linux/macOS

```bash
./mvnw spring-boot:run
```

App default URL: `http://localhost:8081`

## Build and Test

```bash
./mvnw clean test
./mvnw clean package
```

On Windows use `mvnw.cmd` instead of `./mvnw`.

## API Endpoints

### Health

- `GET /` - root message
- `GET /api/health` - service health

### Authentication (`/api/auth`)

- `POST /register`
- `GET /verify?token=...`
- `POST /login`
- `POST /resend-verification`

### Users (`/api/users`)

- `GET /{id}` - get user by ID
- `GET /` - list users (supports `keyword`, `status`, pageable params)

### Posts (`/api/posts`)

- `POST /` - create post (authenticated)
- `GET /` - list posts (optional `userId`, pageable params)
- `GET /popular` - list popular posts
- `DELETE /{postId}` - delete post (owner/admin)

### Comments (`/api/comments`)

- `POST /posts/{postId}` - add comment (authenticated)
- `GET /posts/{postId}` - list comments for post

### Likes (`/api/likes`)

- `POST /posts/{postId}` - like post (authenticated)

