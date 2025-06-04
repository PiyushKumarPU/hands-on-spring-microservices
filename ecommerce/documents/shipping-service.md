# 🚚 shipping-service PRD

## Purpose
Handles delivery assignment, shipping status updates, and tracking.

## APIs
- `GET /api/shipping/{orderId}` – Get shipping status
- `POST /api/shipping/track/{trackingId}` – Track delivery

## Database Tables
### shipping
| Field        | Type      | Description             |
|--------------|-----------|-------------------------|
| order_id     | UUID      | FK to order             |
| status       | Enum      | INITIATED, SHIPPED...   |
| tracking_id  | String    | Tracking code           |
| courier_name | String    | e.g. FedEx, BlueDart    |
| updated_at   | Timestamp | Status update time      |

## Dependencies
- Kafka (consume `PaymentCompleted` to initiate shipping)