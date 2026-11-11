
# ADR-0003: Order-Driven Fulfillment

- Status: Accepted
- Date: 2026-11-11

## Context

ForgeFlow targets order-driven manufacturing and trading
businesses where customer orders may be accepted before
all required items are available in inventory.

Requiring sufficient inventory at order creation would
prevent these businesses from following their natural
business process.

## Decision

- Sales orders can be created regardless of current stock.
- Physical on-hand inventory must not become negative
  due to order creation.
- Inventory availability must account for existing reservations.
- Inventory shortages must be identifiable per order item.
- Shortages can be fulfilled through purchasing or production.
- Fulfillment decisions can be manual or automated.

## Consequences

### Positive

- Supports order-driven business processes.
- Sales is not tightly coupled to stock availability.
- Purchasing and Production can fulfill shortages independently.
- Inventory remains an accurate representation of physical stock.

### Negative

- Order fulfillment requires additional states and workflows.
- Cross-module coordination becomes more complex.
- Reservation and concurrency rules must be carefully designed.
