# 🌟 review-service PRD

## Purpose
Allows users to rate and review products after purchase.

## APIs
- `POST /api/reviews` – Submit review
- `GET /api/reviews/product/{productId}` – Get reviews for product

## Database Tables
### reviews
| Field       | Type      | Description       |
|-------------|-----------|-------------------|
| id          | UUID      | Review ID         |
| user_id     | UUID      | Reviewer ID       |
| product_id  | UUID      | Reviewed product  |
| rating      | Integer   | 1-5 stars         |
| comment     | String    | Optional feedback |
| created_at  | Timestamp | Review date       |

## Dependencies
- order-service (validate product was purchased)
- common-lib (DTOs)