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
        uuid id PK
        uuid organisation_id "Not Null"
        uuid shop_id "Not Null"
        uuid product_id "Not Null"

        decimal qty_on_hand
        decimal qty_reserved

        timestamp created_at
        timestamp updated_at
        uuid created_by
        uuid updated_by
    }

    t_inventory_movement {
        uuid id PK
        uuid organisation_id "Not Null"
        uuid shop_id "Not Null"
        uuid product_id "Not Null"

        decimal adjustment_qty
        varchar(100) adjustment_type
        varchar(255) remark

        decimal qty_before
        decimal qty_after

        timestamp created_at
        timestamp updated_at
        uuid created_by
        uuid updated_by
    }
    t_inventory ||--o{ t_inventory_movement : inventory_id

    t_inventory_reservation {
        uuid id PK

        uuid organisation_id "Not Null"
        uuid shop_id "Not Null"
        
        uuid order_id "Not Null"
        uuid order_item_id "Not Null"

        decimal qty_reserved
        varchat(20) status

        timestamp created_at
        timestamp updated_at
        uuid created_by
        uuid updated_by
    }
    t_inventory ||--o{ t_inventory_reservation : inventory_id
```