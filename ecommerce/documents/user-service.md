# 🧾 user-service PRD

## Purpose
Manages user registration, authentication, and profile management.

## APIs
- `POST /api/users/register` – Register a new user
- `POST /api/users/login` – Authenticate and generate JWT
- `GET /api/users/me` – Get current logged-in user's profile

## Database Tables
### users
| Field         | Type        | Description               |
|---------------|-------------|---------------------------|
| id            | UUID        | Primary key               |
| email         | String      | Unique email              |
| name          | String      | Full name                 |
| password_hash | String      | Hashed password           |
| role          | Enum        | USER / ADMIN              |
| created_at    | Timestamp   | Registration date         |
| updated_at    | Timestamp   | Last updated time         |

## Dependencies
- common-lib (DTOs)
- Kafka (optional login event)
- JWT + Spring Security