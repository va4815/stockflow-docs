# Functional Specification

## Purpose

Many merchants operate across multiple sales channels, such as an online store, a retail shop, or a restaurant. As the business grows, they often need to manage products, inventory, and orders across separate systems.

StockFlow provides a centralised backend platform for merchants who want to manage products, inventory, and orders in one place. The system supports multiple ordering channels, including `Point of Sale (POS)`, `Retail`, and `Online`, allowing merchants to manage different sales workflows through a shared backend system.

The purpose of StockFlow is to reduce the complexity of managing separate platforms and provide a consistent foundation for multi-channel order and inventory management.

## Scope

The initial scope of StockFlow includes:

- Order creation through `POS`, `Retail`, and `Online` channels
- Merchant order confirmation, modification, and cancellation
- Product creation, modification, and deletion
- Product category creation, modification, and deletion
- Inventory refill and stock adjustment
- Shared inventory tracking across all ordering channels
- Basic user authentication and access control

## Problems Solved

Merchants often spend significant time managing separate systems for POS ordering, inventory management, and online ordering. This can lead to duplicated product data, inconsistent stock levels, manual updates, and a higher risk of overselling.

StockFlow addresses these problems by centralising product, inventory, and order management. All sales channels operate against the same inventory source, helping merchants maintain inventory consistency and reduce administrative work.

This allows merchants to focus more on business operations and customer service instead of maintaining the same data across multiple platforms.

## User Roles

StockFlow defines user roles to represent different levels of access across the platform, merchant businesses, and customer-facing ordering workflows.

### Initial Scope Roles

| Role | Description | Main Responsibilities |
|---|---|---|
| `Platform Owner` | Owner or operator of the StockFlow platform | Manage merchant accounts, platform-level configuration, and subscription-related administration |
| `Merchant` | Business owner using StockFlow to manage their sales channels | Manage business profile, products, inventory, orders, and staff access |
| `Merchant Manager` | Business manager responsible for daily operations | Manage products, categories, inventory updates, order reviews, and order changes |
| `Merchant Staff` | Operational user responsible for day-to-day order handling | Create orders, view product information, check stock availability, and support customer checkout workflows |
| `Customer` | External customer placing orders through online or retail/restaurant workflows | Browse products, add items to cart, place online orders, and complete checkout |

### Future Scope Roles

| Role | Description | Main Responsibilities |
|---|---|---|
| `Platform Admin` | Platform administrator responsible for supporting merchants | Handle merchant enquiries, operational issues, and platform support tasks |
| `Merchant Admin` | Business administrator responsible for account and settlement operations | Manage merchant account settings, staff access, settlement records, and administrative business tasks |


Access control is based on roles and authorities. Detailed role-permission mapping will be documented in [`authentication-access-control.md`](./authentication-access-control.md).


### Product Management

Product Management is responsible for maintaining the product catalogue used across StockFlow. Merchants can manage product details, categories and pricing from the backend system.

Key capabilities include:

- Creating new products
- Updating product details such as name, description, price and status
- Deleting or disabling products
- Creating and managing product categories
- Searching and retrieving product information
- Supporting product visibility across different ordering channels
- Linking products with inventory records for stock tracking

### Inventory Management

Inventory Management is responsible for maintaining stock availability across all ordering channels. It provides a shared inventory source so that `POS`, `Retail Ordering`, and `Online Ordering` workflows can operate against consistent stock data.

Key capabilities include:

* Tracking product stock availability
* Recording inventory refills and stock adjustments
* Maintaining inventory movement history
* Supporting inventory checks during order creation
* Preventing orders from being completed when stock is insufficient
* Updating inventory when orders are confirmed, modified, or cancelled
* Maintaining inventory consistency across concurrent ordering workflows

