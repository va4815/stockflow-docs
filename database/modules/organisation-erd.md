# Organisation ER Diagram

## Table Explanation

This section describes the purpose and relationships of each table in the Organisation schema.

### t_organisation

- Each `Organisation` has one `Organisation Profile`
- Each `Organisation` can have multiple `Shop`
- Each `Organisation` can have multiple `Organisation Translation`
- Each `Organisation` belongs to one `Language`

### t_organisation_profile

- Each `Organisation Profile` belongs to one `Organisation`

### t_organisation_translation

- Each `Organisation Translation` belongs to one `Organisation`

### t_shop

- Each `Shop` belongs to one `Organisation`
- Each `Shop` has one `Shop Profile`
- Each `Shop` has one `Shop Setting`
- Each `Shop` can have multiple `Shop Translation`
- Each `Shop` belongs to one `Currency`

### t_shop_profile

- Each `Shop Profile` belongs to one `Shop`

### t_shop_setting

- Each `Shop Setting` belongs to one `Shop`

### t_shop_translation

- Each `Shop Translation` belongs to one `Shop`
- Each `Shop Translation` belongs to one `Language`

### t_currency

- Each `Currency` can have multiple `Shop`

### t_language

- Each `Language` can have multiple `Organisation`
- Each `Language` can have multiple `Shop Translation`

```mermaid
---
title: Organisation Schema
---
erDiagram

    t_organisation {
        SERIAL id PK

        varchar(100) code UK "Not Null"        
        varchar(255) legal_name
        varchar(255) email

        varchar(20) status
        date established_date

        timestamp created_at
        timestamp updated_at
        SERIAL created_by
        SERIAL updated_by
    }

    t_organisation_translation {
        SERIAL id PK
        SERIAL organisation_id FK "Not Null"
        varchar(10) language_code FK "Not Null"

        varchar(255) name "Not Null"

        timestamp created_at
        timestamp updated_at
        SERIAL created_by
        SERIAL updated_by        
    }
    t_organisation ||--o{ t_organisation_translation : organisation_id
    t_language ||--o{ t_organisation_translation : language_code

    t_organisation_profile {
        SERIAL id PK
        SERIAL organisation_id FK, UK "Not Null"

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
        SERIAL created_by
        SERIAL updated_by
    }
    t_currency ||..o{ t_shop : currency_code

    t_language {
        varchar(10) code PK

        varchar(100) name "Not Null"
        boolean active "Not Null"

        timestamp created_at
        timestamp updated_at
        SERIAL created_by
        SERIAL updated_by
    }

    t_shop {
        SERIAL id PK
        SERIAL organisation_id FK "Not Null"

        varchar(100) code "Not Null"
        varchar(20) status "Not Null"

        varchar(3) currency_code FK "Not Null"

        timestamp created_at
        timestamp updated_at
        SERIAL created_by
        SERIAL updated_by
    }
    t_organisation ||--o{ t_shop : organisation_id

    t_shop_translation {
        SERIAL id PK
        SERIAL shop_id FK "Not Null"

        SERIAL organisation_id FK "Not Null"

        varchar(10) language_code "Not Null"

        varchar(255) name "Not Null"

        timestamp created_at
        timestamp updated_at
        SERIAL created_by
        SERIAL updated_by
    }
    t_shop ||--o{ t_shop_translation : shop_id
    t_language ||--o{ t_shop_translation : language_code

    t_shop_profile {
        int id PK
        SERIAL shop_id FK, UK "Not Null"

        varchar(10) phone_country_code
        varchar(30) phone_number

        varchar(100) country
        varchar(100) city
        varchar(20) postcode

        varchar(255) address_line_1
        varchar(255) address_line_2

        timestamp created_at
        timestamp updated_at
        SERIAL created_by
        SERIAL updated_by
    }
    t_shop ||--|| t_shop_profile : shop_id

    t_shop_setting {
        int id PK
        SERIAL shop_id FK, UK "Not Null"

        varchar(10) default_language_code FK "Not Null"
        varchar(20) order_prefix "Not Null"

        timestamp created_at
        timestamp updated_at
        SERIAL created_by
        SERIAL updated_by
    }
    t_shop ||--|| t_shop_setting : shop_id
    t_language ||..o{ t_shop_setting : language_code
```