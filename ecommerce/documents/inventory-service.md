# 📦 inventory-service PRD

## Purpose
Handles product stock tracking, reservations, and adjustments.

## APIs
- `GET /api/inventory/{productId}` – Get current stock
- `POST /api/inventory/reserve` – Reserve stock for an order
- `POST /api/inventory/release` – Release reserved stock

## Database Tables
### inventory
| Field             | Type    | Description                  |
|-------------------|---------|------------------------------|
| product_id        | UUID    | Linked product               |
| available_quantity| Integer | Units available              |
| reserved_quantity | Integer | Units reserved               |
| updated_at        | Timestamp | Last updated timestamp     |

## Dependencies
- common-lib (DTOs)
- Kafka (consume `OrderCreated`, `OrderCancelled` events)