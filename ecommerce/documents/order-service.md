# 📄 order-service PRD

## Purpose
Handles order placement, cancellation, and status tracking.

## APIs
- `POST /api/orders` – Place an order
- `GET /api/orders/{id}` – Get order details
- `GET /api/orders/user/{userId}` – Get all orders for user
- `POST /api/orders/cancel/{id}` – Cancel an order

## Database Tables
### orders
| Field       | Type      | Description           |
|-------------|-----------|-----------------------|
| id          | UUID      | Order ID              |
| user_id     | UUID      | Buyer ID              |
| status      | Enum      | CREATED, CANCELLED... |
| total_price | Decimal   | Total order amount    |
| created_at  | Timestamp | Order creation time   |

### order_items
| Field       | Type    | Description     |
|-------------|---------|-----------------|
| order_id    | UUID    | FK to orders    |
| product_id  | UUID    | FK to product   |
| quantity    | Integer | Ordered qty     |
| price       | Decimal | Price per unit  |

## Dependencies
- inventory-service (reserve stock)
- payment-service (initiate payment)
- Kafka (emit `OrderCreated`, `OrderCancelled`)