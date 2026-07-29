# Database Overview

## Purpose

The purpose of this document is to provide a high-level overview of the StockFlow database design and how data is organised across the platform.


### High-Level Database Structure

The diagram provides a high-level view of the StockFlow database structure and separates database schema to align with the backend modules. Each schema owns the tables responsible for its module, helping maintain clear ownership and separation of concerns.

```mermaid
flowchart LR

    PostgreSQL[("PostgreSQL Database")]

    subgraph AuthenticationSchema["Authentication Schema"]
        Role["role"]
        UserAccount["user_account"]
        Permission["permission"]
        RolePermission["role_permission"]
    end

    subgraph OrganisationSchema["Organisation Schema"]
        Organisation["organisation"]
        OrganisationUser["organisation_user"]
        OrganisationUserRole["organisation_user_role"]
        OrganisationSetting["organisation_setting"]
        Shop["shop"]
    end

    subgraph ProductSchema["Product Schema"]
        Category["category"]
        Product["product"]
        ProductCategory["product_category"]
        ProductPrice["product_price"]
        SalesChannel["sales_channel"]
        ProductChannelAvailability["product_channel_availability"]
    end

    subgraph InventorySchema["Inventory Schema"]
        Inventory["inventory"]
        InventoryMovement["inventory_movement"]
        InventoryReservation["inventory_reservation"]
    end

    subgraph OrderSchema["Order Schema"]
        CustomerOrder["customer_order"]
        OrderItem["order_item"]
        OrderHistory["order_history"]
    end

    PostgreSQL --> AuthenticationSchema
    PostgreSQL --> OrganisationSchema
    PostgreSQL --> ProductSchema
    PostgreSQL --> InventorySchema
    PostgreSQL --> OrderSchema

```

