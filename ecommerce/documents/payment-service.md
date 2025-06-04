# 💳 payment-service PRD

## Purpose
Handles payment operations for orders using simulated external payment services.

## APIs
- `POST /api/payments/initiate` – Initiate payment for order
- `GET /api/payments/status/{orderId}` – Get payment status

## Database Tables
### payments
| Field       | Type      | Description         |
|-------------|-----------|---------------------|
| id          | UUID      | Payment ID          |
| order_id    | UUID      | FK to order         |
| amount      | Decimal   | Payment amount      |
| status      | Enum      | PENDING, SUCCESS... |
| method      | String    | Payment method      |
| created_at  | Timestamp | Payment time        |

## Dependencies
- Kafka (consume order events, emit payment events)