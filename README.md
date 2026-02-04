# Airplain

***plain specs for a RESTful API for messaging between user accounts.

## Overview

Airplain is a backend service that provides:
- Account Management – User registration, authentication, and profile management
- Messaging System – Send and receive messages between users
- Conversations – Organize messages into conversations between two accounts

## Features

### Authentication & Accounts

| Feature | Description |
|---------|-------------|
| Registration | Create a new account via `POST /register` |
| Login | Authenticate and receive a JWT access token via `POST /login` |
| Logout | Invalidate session via `POST /logout` |
| Account CRUD | View, edit, and delete your account |

All account endpoints (except registration and login) require authentication via JWT tokens.

### Messaging

| Feature | Description |
|---------|-------------|
| Messages | Send and manage messages between accounts |
| Conversations | Automatically created when two accounts exchange messages |
| Message History | Fetch all messages in a conversation you're a participant of |

- A conversation is associated with exactly two accounts
- Only conversation participants can access their messages
- Full CRUD operations available for messages and conversations

### Health Check

| Endpoint | Description |
|----------|-------------|
| `GET /healthcheck` | Returns `200 OK` if the service is running |

## Tech Stack

- Language: Java 21
- Framework: Spring Boot
- Authentication: JWT (JSON Web Tokens)
- Database: In-memory database
- Build Tool: Maven
- Libraries: Lombok (boilerplate reduction), Jakarta Validation

## API Endpoints

### Authentication
```
POST /register    – Register a new account
POST /login       – Login and receive access token
POST /logout      – Logout from account
```

### Accounts (Authenticated)
```
GET    /accounts/{id}    – View account details
PUT    /accounts/{id}    – Update account
DELETE /accounts/{id}    – Delete account
```

### Messages (Authenticated)
```
GET    /messages         – List messages
POST   /messages         – Send a message
GET    /messages/{id}    – Get message details
PUT    /messages/{id}    – Update message
DELETE /messages/{id}    – Delete message
```

### Conversations (Authenticated)
```
GET    /conversations         – List conversations
POST   /conversations         – Create conversation
GET    /conversations/{id}    – Get conversation details
PUT    /conversations/{id}    – Update conversation
DELETE /conversations/{id}    – Delete conversation
```

## Getting Started

### Prerequisites

- Java 21
- Maven 3.x

### Project Structure

```
airplain/
├── *.plain                    # Specification files
├── config.yaml                # Configuration
└── test_scripts/              # Build and test automation
```

### Configuration

Key configuration options (in `application.yml`):

| Setting | Value |
|---------|-------|
| Logging Level (root) | `DEBUG` |
| Logging Level (Spring/Apache) | `WARN` |
| Unknown fields | Ignored in data models |
| Null fields | Skipped in JSON serialization |
| Unknown endpoints | Return `404` with empty body |

### Setup

1. Set Java 21 as your runtime:
   ```bash
   export JAVA_HOME=$(/usr/libexec/java_home -v 21)
   ```

2. Build the project:
   ```bash
   mvn clean install -DskipTests
   ```

3. Run the application:
   ```bash
   mvn spring-boot:run
   ```

The API will be available at `http://127.0.0.1:5000` by default.

## License

This project is part of the Codeplain ecosystem.
