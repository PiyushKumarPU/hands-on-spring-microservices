# 🛒 cart-service PRD

## Purpose
Manages user's shopping cart including product addition, removal, and quantity updates.

## APIs
- `GET /api/cart/{userId}` – Get current cart for user
- `POST /api/cart/add` – Add item to cart
- `POST /api/cart/remove` – Remove item from cart
- `POST /api/cart/update` – Update quantity of a cart item

## Data Storage (Redis)
- Key: `cart:{userId}`
- Value: JSON structure with list of productId and quantity

## Dependencies
- product-service (for product details/validation)
- common-lib (DTOs)