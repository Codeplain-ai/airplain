# Airplain

Airplain is a messaging service built with ***plain that uses air to deliver messages between users.

## Overview

Airplain is a backend service that provides:
- Account Management – User registration, authentication, and profile management
- Messaging System – Send and receive messages between users
- Conversations – Organize messages into conversations between two accounts

## Features

### Authentication & Accounts

| Feature | Description |
|---------|-------------|
| Registration | Create a new account  |
| Login | Authenticate and receive a JWT access token  |
| Logout | Invalidate session  |
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


## Tech Stack

- Language: Java 21
- Framework: Spring Boot
- Authentication: JWT (JSON Web Tokens)
- Database: In-memory database
- Build Tool: Maven
- Libraries: Lombok (boilerplate reduction), Jakarta Validation

## API Endpoints

## Getting Started

### Prerequisites

- Java 21
- Maven 3.x
- codeplain 0.2.6

### Project Structure

```
airplain/
├── *.plain                    # Specification files
└── configs/              # Configuration and testing scripts
```

### Running *codeplain rendering

```bash
$ codeplain messages.plain
```

## License

This project is part of the Codeplain ecosystem.
