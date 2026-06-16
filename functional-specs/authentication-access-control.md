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

