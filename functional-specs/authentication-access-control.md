# Authentication and Access Control

## Purpose

The purpose of Authentication and Access Control is to ensure that users can access the platform securely and only perform actions that match their assigned responsibilities. StockFlow supports different types of users, including platform-level users, merchants, merchant staff, and customers, each with different access requirements.

## Scope

Authentication and Access Control provides the following capabilities for StockFlow.

### Initial Scope

- User account creation and management
- User group creation and management
- User login and logout
- Password reset and password change workflows
- Role-based access control
- Authority-based permission checks
- Assignment of roles to users
- Assignment of authorities to roles
- Merchant data isolation to prevent unauthorised access to another merchant’s data

### Future Scope

- User account activation and deactivation


## Access Control

StockFlow uses `Users`, `Roles`, `Authorities`, and `User Groups` to manage access across the platform and individual merchant organisations. These components define who can access the system, what actions they are permitted to perform, and which organisation or business data they are allowed to access.


### Users

A user represents an individual who can access StockFlow.

Users may include platform operators, merchant owners, merchant employees, and customers. Each user has an account and may be assigned roles, authorities through roles, and user group memberships.

Key user capabilities include:

- Creating and managing user accounts
- Assigning users to a merchant where applicable
- Assigning one or more roles to a user
- Adding users to one or more user groups
- Updating user account information
- Preventing users from accessing data outside their permitted scope


### User Groups

A user group represents a collection of users who share a common business function, team, department, location, or operational responsibility.

User groups help merchants organise users and apply common access settings more efficiently.

Examples of user groups include:

- Store Managers
- POS Staff
- Customer Support

Key user group capabilities include:

- Creating and maintaining user groups
- Adding users to a user group
- Removing users from a user group
- Associating a user group with a merchant

### Roles

Role management groups related authorities under a named business responsibility such as 'Store Manager'. Roles could be reused by assigning them to multiple users with similar responsibilities.

Initial roles include:

- `Platform Owner`
- `Merchant`
- `Merchant Manager`
- `Merchant Staff`
- `Customer`

Key Role management capabilities include:

- Creating and maintaining roles
- Assigning roles to users
- Removing roles from users
- Assigning authorities to roles
- Preventing users from assigning roles above their own permitted access level

### Authorities

Authorities represent specific actions that a user is permitted to perform within StockFlow. They can be grouped by business capability to make access control easier to organise and maintain.

Authorities are normally assigned to roles, and users receive the relevant permissions through their assigned roles.

Authority categories include:

- Product management
- Inventory management
- Order management
- User and role management
- Merchant administration

Initial authorities include:

- `PRODUCT_CREATE`
- `PRODUCT_READ`
- `PRODUCT_UPDATE`
- `PRODUCT_DISABLE`
- `INVENTORY_READ`
- `INVENTORY_UPDATE`
- `ORDER_CREATE`
- `ORDER_READ`
- `ORDER_CANCEL`
- `USER_CREATE`
- `ROLE_ASSIGN`


## User Roles

StockFlow defines user roles for both platform-level users and users within merchant organisations. Each role is associated with a set of authorities that determines which functions and data the user is permitted to access.

### Platform Owner

The `Platform Owner` is responsible for operating and administering the StockFlow platform.

Main responsibilities include:

- Creating and managing merchant accounts
- Viewing platform-level merchant information
- Managing merchant access to the platform
- Managing platform-level roles and authorities
- Reviewing platform operations and merchant support requirements
- Accessing platform administration functions

### Merchant

The `Merchant` represents the owner of their business using StockFlow.

Main responsibilities include:

- Managing the merchant business profile
- Managing merchant users and staff access
- Assigning roles to merchant users
- Managing products, categories, and catalogues
- Managing inventory and stock adjustments
- Reviewing and managing orders across supported channels
- Accessing operational information of their business

### Merchant Manager

The `Merchant Manager` is responsible for managing the day-to-day operations of a merchant business.

Main responsibilities include:

- Creating and updating products
- Managing product categories and catalogue assignments
- Reviewing inventory availability
- Updating or adjusting inventory where permitted
- Reviewing incoming orders
- Confirming, modifying, or cancelling eligible orders
- Monitoring operational order and stock information
- Supporting merchant staff during daily operations

### Merchant Staff

The `Merchant Staff` role represents employees responsible for day-to-day operational tasks such as processing orders.

Main responsibilities include:

- Processing `POS` orders
- Viewing product and catalogue information
- Checking inventory availability
- Viewing and updating eligible orders where permitted
- Supporting customer checkout


