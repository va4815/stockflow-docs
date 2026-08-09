# Organisation ER Diagram

## Table Explanation

This section describes the purpose and relationships of each table in the Organisation schema.

### t_organisation

- Each `Organisation` has one `Organisation Profile`
- Each `Organisation` can have multiple `Shop`

### t_organisation_profile

- Each `Organisation Profile` belongs to one `Organisation`

### t_shop

- Each `Shop` belongs to one `Organisation`
- Each `Shop` has one `Shop Profile`
- Each `Shop` has one `Shop Setting`

### t_shop_profile

- Each `Shop Profile` belongs to one `Shop`

### t_shop_setting

- Each `Shop Setting` belongs to one `Shop`

```mermaid
---
title: Organisation Schema
---
erDiagram

    t_organisation {
        uuid id PK

        varchar(100) code UK "Not Null"
        varchar(255) name "Not Null"
        varchar(255) legal_name
        varchar(255) email

        varchar(20) status
        date established_date

        timestamp created_at
        timestamp updated_at
        uuid created_by
        uuid updated_by
    }

    t_organisation_profile {
        uuid id PK
        uuid organisation_id FK, UK "Not Null"

        varchar(100) business_registration_number
        varchar(50) tax_registration_number

        varchar(10) phone_country_code
        varchar(30) phone_number

        varchar(100) country
        varchar(100) city
        varchar(20) postcode

        varchar(255) address_line_1
        varchar(255) address_line_2
    }
    t_organisation ||..|| t_organisation_profile : organisation_id

    t_currency {
        varchar(3) code PK

        varchar(100) name "Not Null"
        varchar(10) symbol
        smallint decimal_places "Not Null"
        boolean active "Not Null"

        timestamp created_at
        timestamp updated_at
        uuid created_by
        uuid updated_by
    }
    t_currency ||..o{ t_shop : currency_code

    t_shop {
        uuid id PK
        uuid organisation_id FK "Not Null"

        varchar(100) code "Not Null"
        varchar(255) name "Not Null"
        varchar(20) status "Not Null"

        varchar(3) currency_code FK "Not Null"

        timestamp created_at
        timestamp updated_at
        uuid created_by
        uuid updated_by
    }
    t_organisation ||--o{ t_shop : organisation_id

    t_shop_profile {
        int id PK
        uuid shop_id FK, UK "Not Null"

        varchar(10) phone_country_code
        varchar(30) phone_number

        varchar(100) country
        varchar(100) city
        varchar(20) postcode

        varchar(255) address_line_1
        varchar(255) address_line_2

        timestamp created_at
        timestamp updated_at
        uuid created_by
        uuid updated_by
    }
    t_shop ||--|| t_shop_profile : shop_id

    t_shop_setting {
        int id PK
        uuid shop_id FK, UK "Not Null"

        varchar(10) default_language_code "Not Null"
        varchar(20) order_prefix "Not Null"

        timestamp created_at
        timestamp updated_at
        uuid created_by
        uuid updated_by
    }
    t_shop ||--|| t_shop_setting : shop_id
```