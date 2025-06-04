# 🔍 search-service PRD

## Purpose
Provides fast product lookup with full-text search capabilities.

## APIs
- `GET /api/search?q=keyword` – Search products by keyword

## Storage
- Elasticsearch index: `products-index`

## Implementation
- Listen to product-service events
- Index product name, description, category

## Dependencies
- product-service (via Kafka or REST)
- Elasticsearch