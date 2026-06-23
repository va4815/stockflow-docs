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

### Customer

The `Customer` is an external user who purchases products from a merchant through customer-facing ordering workflows.

Main responsibilities include:

- Registering and managing a customer account
- Browsing products available through supported catalogues
- Adding, updating, and removing items from a shopping cart
- Placing orders through online, retail, or restaurant ordering workflows
- Viewing the status and details of their own orders
- Managing their own account and delivery or collection information
- Cancelling eligible orders where permitted by the merchant’s cancellation rules


## Functional Capabilities

The Authentication and Access Control module provides the following capabilities for managing user accounts, authentication, roles, authorities, and user groups within StockFlow.

- User account management
    * create user account
    * view and update user account information
- User authentication
    * login and logout
    * change password
    * reset password
- Role management
    * create roles
    * assign roles to users
    * view roles assigned to users
    * Disable roles
- Authority management
    * create authorities
    * view authorities
    * assign authorities to roles
    * remove authorities to roles
- User group management
    * create user groups
    * add user to user groups
    * remove user from user groups
    * associate user groups with merchant organisation

## Business Workflows

The following workflows describe the main steps involved in user account management, authentication, role and authority management, user group management, and access control within StockFlow.

### User Account Workflows

#### User Account Creation Workflow

- A new user account is created through one of the following methods:
  - A `Customer` creates their own account without requiring an authorised user
  - An authorised user creates an account for a platform-level or merchant-level user
- StockFlow validates the submitted account information
- StockFlow creates the account:
  - A customer account is created without a merchant association
  - A merchant-level account is associated with the relevant merchant organisation
  - A platform-level account is created without a merchant association
- Predefined roles or user groups may be assigned where applicable

#### User Account Viewing and Update Workflow

- A user requests to view their own account information
- StockFlow returns the account information when the request is permitted
- The user may submit changes to editable account information
- StockFlow validates the submitted changes and the user’s permission to make them
- StockFlow saves the changes when validation succeeds


#### User Login Workflow

- A user submits their account credentials
- StockFlow verifies the credentials and account status
- StockFlow identifies the user’s assigned roles, authorities, user groups, and merchant association
- Access is granted when authentication succeeds and the account is permitted to access StockFlow
- Access is denied when authentication fails or the account is not permitted to log in

#### User Logout Workflow

- A user requests to end their current authenticated session
- StockFlow invalidates or removes the corresponding session
- The user must authenticate again before accessing protected functions

#### Password Change Workflow

- An authenticated user submits their current password and a new password
- StockFlow verifies the current password and validates the new password
- StockFlow updates the user’s credentials when validation succeeds

#### Password Reset Workflow

- A user requests a password reset
- StockFlow verifies the account and initiates the password-reset process
- The user completes the required verification
- The user submits a new password
- StockFlow validates and saves the new password
- Any expired or previously used reset request is rejected


### Role Workflows

#### Role Creation Workflow

- An authorised user creates a role to represent a business responsibility.
- The user provides a role name and description
- StockFlow validates the role information and the user’s permission
- StockFlow saves the role within the permitted platform or merchant scope

#### Role Assignment to User Workflow

- An authorised user selects a user and a role
- StockFlow verifies that the requesting user is permitted to assign the selected role
- StockFlow verifies that the selected role and user belong to a compatible access scope
- StockFlow assigns the role to the user

#### Role Removal from User Workflow

- An authorised user selects a role assigned to a user
- StockFlow verifies the requesting user’s permission
- StockFlow removes the role from the user

#### View User Roles Workflow

- An authorised user requests to view the roles assigned to a selected user
- StockFlow verifies the requesting user’s permission and data scope
- StockFlow returns the assigned roles when access is permitted

#### Role Disablement Workflow

- An authorised user requests to disable a role
- StockFlow verifies the requesting user’s permission
- StockFlow marks the role as disabled
- The disabled role cannot be assigned to additional users
- Existing role assignments are handled according to the applicable business rules


### Authority Workflows

#### Authority Creation Workflow

- An authorised platform-level user creates an authority.
- The user provides the authority name, description, and relevant capability category
- StockFlow validates the authority information
- StockFlow saves the authority

#### View Authorities Workflow

- An authorised user requests to view available authorities
- StockFlow verifies the requesting user’s permission and access scope
- StockFlow returns the authorities that the user is permitted to view

#### Authority Assignment to Role Workflow

- An authorised user selects a role and one or more authorities
- StockFlow verifies that the user is permitted to manage the selected role and authorities
- StockFlow assigns the authorities to the role

#### Authority Removal from Role Workflow

- An authorised user selects one or more authorities assigned to a role
- StockFlow verifies the requesting user’s permission
- StockFlow removes the selected authorities from the role


### User Group Workflows

#### User Group Creation Workflow

- An authorised merchant user creates a user group for a team, department, location, or operational responsibility
- StockFlow verifies the requesting user’s permission
- StockFlow associates the user group with the relevant merchant organisation
- StockFlow saves the user group

#### Add User to User Group Workflow

- An authorised user selects a user and a user group
- StockFlow verifies the requesting user’s permission
- StockFlow verifies that the user and user group belong to the same merchant organisation
- StockFlow adds the user to the group

#### Remove User from User Group Workflow

- An authorised user selects a member of a user group
- StockFlow verifies the requesting user’s permission
- StockFlow removes the user from the group

#### Associate User Group with Merchant Workflow

- An authorised user associates a user group with a merchant organisation
- StockFlow verifies the requesting user’s permission
- StockFlow ensures that the group and its members remain within the permitted merchant scope
- StockFlow prevents the group from containing users associated with another merchant


### Shared Access Control Workflows

#### Protected Function Access Workflow

- An authenticated user requests access to a protected function
- StockFlow verifies the user’s authentication status
- StockFlow checks the user’s assigned roles and associated authorities
- StockFlow verifies the user’s merchant association and permitted data scope where applicable
- StockFlow allows the request only when all required access conditions are satisfied
- StockFlow denies the request when any required condition is not satisfied

#### Merchant Data Isolation Workflow

- A merchant-level user requests access to merchant-owned data.
- StockFlow identifies the merchant organisation associated with the authenticated user
- StockFlow verifies that the requested data belongs to the same merchant organisation
- StockFlow restricts the request to data belonging to the user’s merchant
- StockFlow denies access to data belonging to another merchant

#### Restricted Role Assignment Workflow

- A user attempts to assign a role to another user.
- StockFlow checks the requesting user’s roles, authorities, and access scope
- StockFlow checks whether the requesting user is permitted to assign the selected role
- StockFlow rejects the assignment when the selected role exceeds the requesting user’s permitted level
- StockFlow also rejects the assignment when the users or role belong to incompatible merchant scopes

#### Unauthorised Access Handling Workflow

- A user attempts to access a function or data without the required authority or permitted data scope
- StockFlow denies the request
- StockFlow returns an appropriate access-denied response without exposing restricted information
- StockFlow records the unauthorised access attempt when required for security and audit purposes


## Role and Authority Matrix

The following matrix defines the default authorities assigned to each predefined StockFlow role.

An assigned authority permits a user to perform the corresponding action or operation. Merchant-level roles can only manage their authorities within their own merchant organisation.

### Platform User Management Authorities

| Authority | Platform Owner | Merchant | Merchant Manager | Merchant Staff | Customer |
|---|---:|---:|---:|---:|---:|
| `PLATFORM_USER_CREATE` | ✓ | - | - | - | - |
| `PLATFORM_USER_READ` | ✓ | - | - | - | - |
| `PLATFORM_USER_UPDATE` | ✓ | - | - | - | - |
| `PLATFORM_USER_DISABLE` | ✓ | - | - | - | - |
| `PLATFORM_USER_DELETE` | ✓ | - | - | - | - |

### Merchant User Management Authorities

| Authority | Platform Owner | Merchant | Merchant Manager | Merchant Staff | Customer |
|---|---:|---:|---:|---:|---:|
| `MERCHANT_USER_CREATE` | ✓ | - | - | - | - |
| `MERCHANT_USER_READ` | ✓ | ✓ | ✓ | ✓ | - |
| `MERCHANT_USER_UPDATE` | ✓ | ✓ | ✓ | - | - |
| `MERCHANT_USER_DISABLE` | ✓ | ✓ | - | - | - |
| `MERCHANT_USER_DELETE` | ✓ | - | - | - | - |

- Merchant managers may view or update merchant staff account information only when the required authority has been assigned

### Customer Account Management Authorities

| Authority | Platform Owner | Merchant | Merchant Manager | Merchant Staff | Customer |
|---|---:|---:|---:|---:|---:|
| `CUSTOMER_ACCOUNT_READ` | ✓ | - | - | - | - |
| `CUSTOMER_ACCOUNT_UPDATE` | ✓ | - | - | - | - |
| `CUSTOMER_ACCOUNT_READ_SELF` | ✓ | - | - | - | ✓ |
| `CUSTOMER_ACCOUNT_UPDATE_SELF` | ✓ | - | - | - | ✓ |
| `CUSTOMER_ACCOUNT_DISABLE` | ✓ | - | - | - | - |
| `CUSTOMER_ACCOUNT_DELETE` | ✓ | - | - | - | - |

- `Customer` can create and manage only their own accounts
- `Customer` account belongs to the platform, they could use different merchant's service in a single account
