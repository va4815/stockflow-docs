# Authentication ER Diagram

## Table Explanation

This section describes the purpose and relationships of each table in the Authentication and Access Control schema.

### t_user_account

- Each `User Account` is assigned one `Role`
- Each `User Account` can have multiple direct `Permission`
- Each `User Account` has one `User Setting`
- Each `User Account` can belong to multiple `User Account Group`

### t_user_account_group

- Each `User Account Group` can contain multiple `User Account`
- Each `User Account` can belong to multiple `User Account Group`
- Each `User Account Group` can be assigned multiple `Permission`, which are inherited by all group members

### t_role

- Each `Role` can be assigned to multiple `User Account`
- Each `Role` can be assigned multiple `Permission`

### t_permission

- A `Permission` can be assigned to multiple `Role`
- A `Permission` can be assigned to multiple `User Account Group`
- A `Permission` can be assigned directly to multiple `User Account`

### t_user_setting

- Each `User Setting` belongs to one `User Account`
- Each `User Setting` references one preferred `Locale`

### t_locale

- `code` stores the locale identifier
- `name` stores the locale description
- `enabled` indicates whether the locale is available for selection

Examples:

| code | name |
|---------|---------|
| `en-GB` | English (United Kingdom) |
| `zh-HK` | Traditional Chinese (Hong Kong) |


```mermaid
---
title: Authentication and Access Control Schema
---
erDiagram
    t_user_account {
        SERIAL id PK
        varchar(100) kc_id "Not Null"

        varchar(100) username UK "Not Null"
        varchar(255) email UK
        
        varchar(100) first_name
        varchar(100) last_name
        boolean is_enabled
        boolean is_email_verified
        
        timestamp last_login_at

        int role_id FK "Not Null"
        
        timestamp created_at
        timestamp updated_at
        SERIAL created_by
        SERIAL updated_by
    }
    t_user_account }o..|| t_role : role_id

    t_user_setting {
        SERIAL id PK
        SERIAL user_account_id FK, UK
        varchar(10) language_code FK
    }
    t_user_account ||..|| t_user_setting : user_account_id
    t_locale ||..o{ t_user_setting : language_code

    t_locale {
        int id PK
        varchar(10) code
        varchar(100) name
        boolean enabled
    }

    t_user_account_group {
        SERIAL id PK

        varchar(100) name
        varchar(255) description
        
        varchar(20) status

        timestamp created_at
        timestamp updated_at
        SERIAL created_by
        SERIAL updated_by
    }

    t_user_account_group_mapping {
        SERIAL user_account_id PK, FK
        SERIAL user_account_group_id PK, FK
    }

    t_user_account ||..o{ t_user_account_group_mapping : user_account_id
    t_user_account_group ||..o{ t_user_account_group_mapping : user_account_group_id


    t_role {
        int id PK

        varchar(100) code UK
        varchar(100) name
        varchar(255) description
    }

    t_permission {
        int id PK
        varchar(100) code UK
    }

    t_user_account_permission_mapping {
        SERIAL user_account_id PK, FK
        int permission_id PK, FK
    }
    t_user_account ||..o{ t_user_account_permission_mapping : user_account_id
    t_permission ||..o{ t_user_account_permission_mapping : permission_id

    t_role_permission_mapping {
        int role_id PK, FK
        int permission_id PK, FK
    }
    t_role ||..o{ t_role_permission_mapping : role_id
    t_permission ||..o{ t_role_permission_mapping : permission_id

    t_user_account_group_permission_mapping {
        SERIAL user_account_group_id PK, FK
        int permission_id PK, FK
    }
    t_user_account_group ||..o{ t_user_account_group_permission_mapping : user_account_group_id
    t_permission ||..o{ t_user_account_group_permission_mapping : permission_id
```
