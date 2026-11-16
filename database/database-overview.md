# Database Overview

## Purpose

The purpose of this document is to provide a high-level overview of the StockFlow database design and how data is organised across the platform.


### High-Level Database Structure

The diagram provides a high-level view of the StockFlow database structure and separates database schema to align with the backend modules. Each schema owns the tables responsible for its module, helping maintain clear ownership and separation of concerns.

```mermaid
flowchart TB

    PostgreSQL[("PostgreSQL Database")]

    AuthenticationSchema["Authentication Schema"]
    ProductSchema["Product Schema"]
    InventorySchema["Inventory Schema"]
    OrderSchema["Order Schema"]

    PostgreSQL --> AuthenticationSchema
    PostgreSQL --> ProductSchema
    PostgreSQL --> InventorySchema
    PostgreSQL --> OrderSchema

```

## Module Database Designs

### Authentication
- Owns `user account`, `profile`, `user group`, `role`, and `permission` tables
- Link to [`modules/authentication-erd.md`](./modules/authentication-erd.md)

### Product
- Owns `category`, `product`, `shop`, `currency` and `language` tables
- Link to [`modules/product-erd.md`](./modules/product-erd.md)

### Inventory
- Owns `inventory`, `inventory reservation` and `inventory movement` tables
- Link to [`modules/inventory-erd.md`](./modules/inventory-erd.md)

### Order
- Owns `order`, `order item` and `order history` tables
- Link to [`modules/order-erd.md`](./modules/order-erd.md)

