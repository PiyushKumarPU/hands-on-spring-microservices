# 📦 product-service PRD

## Purpose
Handles product catalog, filtering, and category management.

## APIs
- `GET /api/products` – List products (with filters/sorting)
- `GET /api/products/{id}` – Product details
- `POST /api/products` – Create a new product (Admin only)
- `PUT /api/products/{id}` – Update product details
- `DELETE /api/products/{id}` – Delete product

## Database Tables
### products
| Field       | Type      | Description         |
|-------------|-----------|---------------------|
| id          | UUID      | Product ID          |
| name        | String    | Product name        |
| description | String    | Full description    |
| price       | Decimal   | Price               |
| category_id | UUID      | Foreign key         |
| created_at  | Timestamp | Created timestamp   |
| updated_at  | Timestamp | Last modified       |

### categories
| Field      | Type    | Description     |
|------------|---------|-----------------|
| id         | UUID    | Primary key     |
| name       | String  | Category name   |

## Dependencies
- common-lib (DTOs)
- Kafka (send product created/updated for indexing)