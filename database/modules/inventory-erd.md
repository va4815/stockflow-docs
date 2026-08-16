# Inventory ER Diagram

## Table Explanation

This section describes the purpose and relationships of each table in the Inventory schema.

### t_inventory

- Each `Inventory` can have multiple `Inventory Movement`
- Each `Inventory` can have multiple `Inventory Reservation`

### t_inventory_movement

- Each `Inventory Movement` belongs to one `Inventory`

### t_inventory_reservation

- Each `Inventory Reservation` belongs to one `Inventory`


```mermaid
---
title: Inventory Schema
---
erDiagram
    t_inventory {
        SERIAL id PK
        SERIAL organisation_id "Not Null"
        SERIAL shop_id "Not Null"
        SERIAL product_id "Not Null"

        decimal qty_on_hand
        decimal qty_reserved

        timestamp created_at
        timestamp updated_at
        SERIAL created_by
        SERIAL updated_by
    }

    t_inventory_movement {
        SERIAL id PK
        SERIAL organisation_id "Not Null"
        SERIAL shop_id "Not Null"
        SERIAL product_id "Not Null"

        decimal adjustment_qty
        varchar(100) adjustment_type
        varchar(255) remark

        decimal qty_before
        decimal qty_after

        timestamp created_at
        timestamp updated_at
        SERIAL created_by
        SERIAL updated_by
    }
    t_inventory ||--o{ t_inventory_movement : inventory_id

    t_inventory_reservation {
        SERIAL id PK

        SERIAL organisation_id "Not Null"
        SERIAL shop_id "Not Null"
        
        SERIAL order_id "Not Null"
        SERIAL order_item_id "Not Null"

        decimal qty_reserved
        varchat(20) status

        timestamp created_at
        timestamp updated_at
        SERIAL created_by
        SERIAL updated_by
    }
    t_inventory ||--o{ t_inventory_reservation : inventory_id
```