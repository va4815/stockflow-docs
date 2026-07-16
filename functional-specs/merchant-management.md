# Merchant Management

## Purpose

The purpose of Merchant Management is to create, maintain, and manage merchant organisations within StockFlow.

Merchant Management stores merchant information such as business profile, status, and configuration. It establishes the merchant organisation as the ownership boundary for business data, ensuring that products, inventory, orders, users, and other merchant resources are associated with the correct merchant.

The module also ensures that merchant users can only access and manage resources belonging to their own merchant organisation, providing data isolation between merchants operating on the platform.

## Scope

Merchant Management provides the following capabilities for managing merchant organisations.

### Initial Scope

- Register merchant organisations
- View merchant information
- Update merchant profile information
- Manage merchant status
- Manage merchant configuration
- Associate merchant users with a merchant organisation
- Restrict merchant access to their own organisation
- Isolate merchant data from other merchant organisations

### Future Scope

- Merchant subscription management
- Free trial support
- Subscription grace period
- Subscription renewal
- Payment gateway integration
- Merchant branding and customisation
- Multi-store support under a merchant organisation
- Merchant onboarding workflow
- Merchant audit history

## Merchant Concepts

Merchant Management uses the following concepts to describe how merchant organisations are created, managed, and isolated within StockFlow.

### Merchant Organisation

A merchant organisation represents a business that uses StockFlow to manage its products, inventory, and orders. Each merchant organisation operates independently within the platform. Business data belonging to one merchant must not be visible or accessible to another merchant.

Examples:

Restaurants -

- The Noodle House
- Coffee Corner

Retail -

- Captain Sport
- Fashion Outlet

### Merchant Profile

A merchant profile stores the basic information of a merchant organisation.

Examples:

- Business name
- Business registration number
- Contact person
- Contact number
- Email address
- Business address

### Merchant Status

Merchant status represents the operational state of a merchant organisation.

- `Active` - the merchant can access and use StockFlow normally
- `Suspended` - the merchant is temporarily prevented from using StockFlow
- `Disabled` - the merchant is permanently disabled and can no longer use StockFlow

### Merchant Ownership

Merchant ownership represents which merchant organisation owns and manages the business resources.

Examples of Merchant owned resources:

- Products
- Product categories
- Inventory
- Orders
- Merchant users
- User groups

### Merchant Configuration

Merchant configuration represents the business settings that control how a merchant organisation operates.

Examples:

- Supported order workflows
- Business information
- Operational preferences

## User Roles and Responsibilities

The following roles define how users can create, view, update, and manage merchant organisations.

### Platform Owner

The `Platform Owner` is responsible for operating the StockFlow platform and managing merchant organisations.

Main responsibilities:

- Register merchant organisations
- View merchant information
- Update merchant profile information
- Suspend or disable merchant organisations where required
- Manage merchant configuration
- Support merchants with platform-related issues

### Merchant

The `Merchant` is the owner of a merchant organisation and has the highest level of administrative access within that organisation.

Main responsibilities:

- View merchant profile information
- Update merchant profile information
- Review merchant operational status
- Manage merchant users

### Merchant Manager

The `Merchant Manager` is responsible for supporting the day-to-day administration within the merchant organisation.

Main responsibilities:

- Support operational administration within the merchant organisation
- Report merchant profile or configuration issues to the `Merchant`

## Functional Capabilities

The Merchant Management module provides the following capabilities for managing merchant organisations, merchant information, and merchant configuration.

- Merchant Registration
    * Register a new merchant organisation
    * Merchant information may include:
        * Business name
        * Business registration number
        * Contact person
        * Contact number
        * Email address
        * Business address
        * Merchant status
        * Merchant configuration
- Merchant Viewing
    * View merchant information
    * Merchant information may include:
        * Business profile
        * Contact information
        * Merchant status
        * Merchant configuration
- Merchant Update
    * Allow authorised users to update merchant information
    * Merchant updates may include:
        * Business name
        * Contact information
        * Business address
        * Merchant configuration
- Merchant Suspension
    * Allow authorised platform users to suspend a merchant organisation
    * Suspended merchants cannot access StockFlow until the suspension is removed
    * Merchant data remains available for future re-activation
- Merchant Configuration Management
    * Configure merchant-specific settings
    * Merchant configuration may include:
        * Supported order workflows
        * Default currency
        * Time zone
        * Default order confirmation behaviour
    * Allow authorised users to update merchant configuration

## Business Workflows

The following workflows describe the main business processes for merchant management

### Merchant Registration Workflow

- Platform Owner enters the merchant information
- Platform Owner submits the merchant registration request
- System validates the submitted merchant information
- System checks that the merchant does not already exist
- System creates the merchant organisation
- System initialises the default merchant status and configuration
- System returns the created merchant information

### Merchant Viewing Workflow

- User requests to view merchant information
- System checks the user's permission and scope
- System verifies that the user is authorised to access the requested merchant organisation
- System retrieves the merchant information
- System returns the permitted merchant information

### Merchant Update Workflow

- Select an exising merchant organisation if this is `Platform Owner`
- Authorised user submits the updated merchant information
- System checks the user's permission and scope
- System validates the submitted information
- System saves the updated merchant information
- System returns the updated merchant information

### Merchant Suspension Workflow

- `Platform Owner` requests to suspend a merchant organisation
- System verifies the Platform Owner's permission
- System verifies that the merchant organisation exists
- System changes the merchant status to `Suspended`
- Suspended merchant users can no longer access StockFlow
- Merchant data remains available for future re-activation
- System returns the updated merchant information
