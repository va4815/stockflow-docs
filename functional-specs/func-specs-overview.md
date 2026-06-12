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

### Order Management

Order Management is responsible for creating and managing orders across multiple sales channels. It provides a shared order foundation for `POS`, `Retail Ordering`, and `Online Ordering` workflows while allowing each channel to follow its own ordering process.

Key capabilities include:

* Creating orders from `POS`, `Retail Ordering`, and `Online Ordering` channels
* Managing order items, quantities, and totals
* Supporting order confirmation, modification, and cancellation
* Tracking order status and order history
* Checking product and inventory availability during order creation
* Updating related inventory records when an order is confirmed or cancelled
* Maintaining a consistent order record across different sales channels

### Authentication and Access Control

Authentication and Access Control is responsible for managing user access to StockFlow. It ensures that users can only access functions that match their assigned roles and authorities.

Key capabilities include:

* Managing user accounts
* Supporting user authentication
* Managing roles such as `Platform Owner`, `Merchant`, `Merchant Manager`, and `Merchant Staff`
* Assigning authorities such as `PRODUCT_READ_PERMISSION`, `PRODUCT_DELETE_PERMISSION`, `INVENTORY_UPDATE_PERMISSION`, and `ORDER_CREATE_PERMISSION`
* Supporting user groups for organising users by business function or responsibility
* Protecting backend functions based on assigned roles and authorities
* Supporting different access levels between platform-level users, merchant users, and customers

### Gateway Workflows

Gateway Workflows define how external clients access the StockFlow backend through separate channel-specific entry points. Each gateway represents a specific workflow and forwards validated requests to the backend application.

Key capabilities include:

* Providing separate entry points for `POS`, `Retail Ordering`, and `Online Ordering` workflows
* Handling channel-specific request validation
* Applying authentication and access control checks before forwarding requests
* Routing requests to the appropriate backend functions
* Hiding the internal backend structure from external clients
* Supporting different API response formats or workflows for each channel
* Isolating external traffic from the core backend application

## Key Business Workflow

This section describes the main business workflows supported by StockFlow. These workflows explain how merchants, staff, and customers interact with the system across product management, inventory management, and order processing.


### Product Category Creation Workflow

The Product Category Creation Workflow allows a merchant or authorised user to create a product category for organising products in the system.

1. The merchant or authorised user logs in to the system.
2. The user creates a new product category with required details such as category name, description, and status.
3. The system validates the product category information.
4. The system saves the product category record.
5. The product category becomes available for product assignment.

Expected result:

* A new product category is created successfully.
* Products can be assigned to the category for product management, search, and catalogue organisation.


### Product Creation Workflow

The Product Creation Workflow allows a merchant or authorised user to create a new product that can be used across different ordering channels.

1. The merchant or authorised user logs in to the system.
2. The user creates a new product with required details such as product name, description, category, price, and status.
3. The user assigns the product to one or more catalogues or ordering channels if required.
4. The system validates the product information.
5. The system saves the product record.
6. The product becomes available for product lookup, catalogue management, and inventory tracking.

Expected result:

* A new product is created successfully.
* The product can be used by `POS`, `Retail Ordering`, or `Online Ordering` workflows based on its visibility settings.
* The product can be linked with inventory records for stock management.

### Inventory Update Workflow

The Inventory Update Workflow allows a merchant, manager, or authorised staff member to update stock levels when inventory is refilled, adjusted, or corrected.

1. The authorised user selects a product from the product catalogue.
2. The user enters the inventory update details, such as quantity, update type, and reason.
3. The system validates the product and inventory update request.
4. The system updates the inventory record.
5. The system records an inventory movement for traceability.
6. The updated stock availability becomes visible to all relevant ordering channels.

Expected result:

* Product stock levels are updated.
* Inventory movement history is recorded.
* `POS`, `Retail Ordering`, and `Online Ordering` workflows use the updated inventory data.

Example inventory update types:

* Stock refill
* Manual stock adjustment
* Damaged stock adjustment
* Returned stock adjustment

### POS Order Workflow

The POS Order Workflow allows merchant staff to create an in-store order through the POS channel.

1. Merchant staff accesses the POS workflow.
2. The staff member searches or selects products from the POS catalogue.
3. The staff member adds products to the order.
4. The system checks product availability and stock levels.
5. The staff member confirms the order.
6. The system creates the order record.
7. The system updates or reserves inventory based on the confirmed order.
8. The order is marked with the appropriate POS order status.

Expected result:

* A POS order is created successfully.
* Inventory is updated based on the ordered items.
* The order is recorded for future review and reporting.

### Retail Order Workflow

The Retail Order Workflow allows a merchant, staff member, or retail customer to create an order through the retail ordering channel.

1. The user accesses the retail ordering workflow.
2. The user searches or selects products from the retail catalogue.
3. The user adds products to the order.
4. The system checks product availability and inventory levels.
5. The user submits the order request.
6. The merchant or authorised user reviews the order if confirmation is required.
7. The system creates or confirms the order.
8. The system updates or reserves inventory based on the confirmed order.

Expected result:

* A retail order is created or submitted for confirmation.
* Inventory availability is checked before the order is confirmed.
* The order status is tracked through the retail order lifecycle.

### Online Order Workflow

The Online Order Workflow allows a customer to browse products, add items to a cart, and place an order through the online ordering channel.

1. The customer accesses the online ordering workflow.
2. The customer browses or searches products from the online catalogue.
3. The customer adds products to the cart.
4. The system checks product visibility and basic stock availability.
5. The customer reviews the cart and proceeds to checkout.
6. The customer submits the order.
7. The system validates the order request and checks inventory availability.
8. The system creates the order record.
9. The system updates or reserves inventory based on the order.
10. The customer receives order confirmation or order status information.

Expected result:

* A customer order is created through the online channel.
* Inventory is updated or reserved to prevent overselling.
* The order can be reviewed and managed by the merchant.

### Order Cancellation Workflow

The Order Cancellation Workflow allows an authorised user to cancel an order and restore or release affected inventory where appropriate.

1. The authorised user selects an existing order.
2. The system checks whether the order can be cancelled based on its current status.
3. The user submits the cancellation request.
4. The system updates the order status to cancelled.
5. The system restores or releases inventory affected by the cancelled order.
6. The system records the cancellation action for history and traceability.

Expected result:

* The order is cancelled successfully.
* Related inventory is restored or released where applicable.
* The order history records the cancellation event.

Cancellation rules may depend on the order status. For example, an order that has already been completed may require a return or refund workflow instead of a normal cancellation.

## Business Rules

This section defines the high-level business rules that guide the behaviour of StockFlow across product management, inventory management, order processing, authentication, and gateway workflows.

Detailed business rules for each functional area will be documented in separate functional specification files.

### Product Management Rules

* A product must belong to a merchant.
* A product must have required information such as name, category, price, and status before it can be used for ordering.
* A product can be active, inactive, or disabled.
* Disabled products should not be available for new orders.
* Deleting a product should not remove historical order records.
* Product information should be shared consistently across `POS`, `Retail Ordering`, and `Online Ordering` workflows.
* A product can be linked with inventory records for stock tracking.

### Product Category Rules

* A product category must belong to a merchant.
* A product category should have a unique name within the same merchant account.
* A product can be assigned to one or more product categories if required.
* A product category should not be deleted if active products are still assigned to it, unless the products are reassigned or the category is disabled.

### Inventory Management Rules

* Inventory records must be linked to valid products.
* Available stock should not become negative.
* Inventory updates must be recorded with a reason, such as refill, adjustment, damage, return, or correction.
* All stock changes should create an inventory movement record for traceability.
* Inventory availability should be shared across all ordering channels.
* When an order is confirmed, the related inventory should be reduced or reserved based on the order workflow.
* When an order is cancelled, related inventory should be restored or released where applicable.

### Order Management Rules

* An order must be created through a valid ordering channel: `POS`, `Retail Ordering`, or `Online Ordering`.
* An order must contain at least one valid order item.
* The system should check product availability and inventory availability before confirming an order.
* Orders should have a clear status, such as `Pending`, `Confirmed`, `Cancelled`, or `Completed`.
* Order modification should only be allowed when the order is in an editable status.
* Order cancellation should only be allowed when the order has not reached a final or completed status.
* Order history should be maintained for tracking and audit purposes.

### Authentication and Access Control Rules

* Users must be authenticated before accessing protected backend functions.
* User access should be controlled by assigned roles and authorities.
* Platform-level users should only access platform administration functions.
* Merchant users should only access data belonging to their own merchant account.
* Customers should only access their own account, cart, and order information.
* Sensitive operations, such as deleting products, updating inventory, or managing users, should require appropriate permissions.

### Gateway Workflow Rules

* External clients should access the system through the appropriate channel gateway.
* `POS`, `Retail Ordering`, and `Online Ordering` workflows should use separate gateway entry points.
* Gateways should validate incoming requests before forwarding them to the backend application.
* Gateways should not contain core business logic such as inventory deduction, order state management, or product rules.
* The internal backend application and database should not be exposed directly to external clients.
