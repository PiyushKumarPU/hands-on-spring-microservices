# 📢 notification-service PRD

## Purpose
Sends email, SMS, or in-app notifications based on business events.

## Kafka Listeners
- `OrderCreated` – Send order confirmation
- `PaymentCompleted` – Send payment receipt
- `OrderShipped` – Send shipping update

## Implementation
- Pluggable channels (email, SMS)
- Retry & dead-letter topic support
- Can use Redis Queue optionally for retry

## Dependencies
- Kafka (primary source)
- common-lib (shared event structures)