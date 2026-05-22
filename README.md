# StockFlow

StockFlow is a multi-channel order and inventory management platform built with a modular monolith architecture. The system supports `Point of Sale (POS)`, `Retail Ordering`, and `Online Ordering` workflows through a shared backend domain model. Centralised inventory and order management enable multiple channels to process transactions simultaneously while maintaining inventory consistency across the platform.

## Project Goals

- Build a scalable multi-channel backend platform
- Centralise inventory and order management
- Support future migration toward microservices
- Explore event-driven architecture patterns
- Practise Kubernetes and cloud-native deployment workflows

## Architecture Overview

StockFlow is designed as a multi-channel backend platform using modular monolith architecture. The system exposes separate channel gateways for `Point of Sale (POS)`, `Retail Ordering`, and `Online Ordering` workflows.

Each gateway acts as an entry point to the system and is responsible for functions such as authentication, request validation and API response handling. The `StockFlow Backend` owns the core business logic, including inventory management, order management and product management.

```mermaid
  flowchart TD;
    POS_Client --> POS_Gateway;
    Retail_Client --> Retail_Gateway;
    Online_Store --> Online_Gateway;

    POS_Gateway --> StockFlow_Backend;
    Retail_Gateway --> StockFlow_Backend;
    Online_Gateway --> StockFlow_Backend;
    StockFlow_Backend --> Database;
```

## Functional Overview

StockFlow provides a shared backend platform for managing orders and inventory across multiple sales channels, including `Point of Sale (POS)`, `Retail Ordering`, and `Online Ordering`.

The platform centralise product, inventory, and order data to ensure that all channels operate against a consistent inventory source. This allows different ordering workflows to process transactions concurrently while maintaining inventory accuracy across the system.

#### Inventory Management

- Track product inventory and stock availability
- Maintain shared inventory across multiple sales channels
- Record inventory movements and stock adjustments
- Support inventory reservation during order processing

#### Order Management

- Create and manage orders from multiple channels
- Support different order workflows and statuses
- Maintain order history and transaction records
- Handle order cancellations and inventory updates

#### Product Management

- Manage products, categories, and pricing
- Support product lookup and product search

#### Authentication and Access Control

- Manage user accounts and authentication
- Support user roles such as `Manager` and `Admin`
- Assign permissions to roles such as `PRODUCT_READ_PERMISSION` and `PRODUCT_DELETE_PERMISSION`
- Protect backend functions based on assigned roles and authorities

#### Gateways

- Provide separate entry points for `POS`, `Retail`, and `Online` workflows
- Support channel specific request handling and validation
- Isolate external traffic from the core backend application