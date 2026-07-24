# Organisation Management

## Purpose

The purpose of Organisation Management is to create, maintain, and manage organisations within StockFlow.

Organisation Management stores organisation information, including the business profile, status, and configuration. It establishes the organisation as the top-level ownership and data-isolation boundary for business data. Organisation-level resources, such as products and users, belong directly to an organisation, while operational resources, such as inventory and orders, belong to shops within that organisation.

The module also ensures that organisation users can only access and manage resources belonging to their own organisation, providing data isolation between organisations operating on the platform.

## Scope

Organisation Management provides the following capabilities for managing organisations.

### Initial Scope

- Register organisations
- View organisation information
- Update organisation profile information
- Manage organisation status
- Manage organisation configuration
- Manage shops belonging to an organisation
- Associate organisation users with an organisation
- Restrict organisation users to accessing resources belonging to their own organisation
- Isolate organisation data from other organisations

### Future Scope

- Organisation subscription management
- Free trial support
- Subscription grace period
- Subscription renewal
- Payment gateway integration
- Organisation branding and customisation
- Organisation onboarding workflow
- Organisation audit history

## Organisation Concepts

Organisation Management uses the following concepts to describe how organisations are created, managed, and isolated within StockFlow.

### Organisation

An organisation represents a business that uses StockFlow to manage its products, inventory, and orders. Each organisation operates independently within the platform. Business data belonging to one organisation must not be visible or accessible to another organisation.

Examples:

Restaurants -

- The Noodle House
- Coffee Corner

Retail -

- Captain Sport
- Fashion Outlet

### Organisation Profile

An organisation profile stores the basic information of an organisation.

Examples:

- Business name
- Business registration number
- Contact person
- Contact number
- Email address
- Business address

### Organisation Status

Organisation status represents the operational state of an organisation.

- `Active` - the organisation can access and use StockFlow normally
- `Suspended` - the organisation is temporarily prevented from using StockFlow
- `Disabled` - the organisation is inactive and cannot use StockFlow until it is re-abled by an authorised platform user

### Organisation Ownership

Organisation ownership defines the organisation-level ownership and data-isolation boundary for business resources within StockFlow.

Examples of organisation-owned resources:

- Products
- Product categories
- Inventory
- Orders
- organisation users
- User groups

### Organisation Configuration

Organisation configuration represents the operational settings that control how an organisation uses StockFlow.

Examples:

- Supported order workflows
- Operational preferences

### Shop

A shop represents a physical or operational location belonging to an organisation. Each shop belongs to exactly one organisation, and an organisation may operate one or more shops. Products are shared across shops within the same organisation, while inventory and orders belong to individual shops. A shop cannot access or use products belonging to another organisation.

## User Roles and Responsibilities

The following roles define how users can create, view, update, and manage organisations.

### Platform Owner

The `Platform Owner` is responsible for operating the StockFlow platform and managing organisations.

Main responsibilities:

- Register organisations
- View organisation information
- Update organisation profile information
- Suspend or disable organisations where required
- Manage organisation configuration
- Support organisations with platform-related issues

### Organisation Owner

The `Organisation Owner` is the owner of an organisation and has the highest level of administrative access within that organisation.

Main responsibilities:

- View organisation profile information
- Update organisation profile information
- Review organisation operational status
- Manage organisation users through Authentication and Access Control

### Shop Manager

The `Shop Manager` manages the day-to-day operation of an assigned shop. Their permissions are limited to the shop they are assigned to.

Main responsibilities:

- Support the day-to-day administration of the shop
- Report organisation profile or configuration issues to the `Organisation Owner`

## Functional Capabilities

The Organisation Management module provides the following capabilities for managing organisations, organisation information, and organisation configuration.

- Organisation Registration
    * Register a new organisation
    * Submitted organisation information may include:
        * Business name
        * Business registration number
        * Contact person
        * Contact number
        * Email address
        * Business address
    * The system initialises:
        * Default organisation status
        * Default organisation configuration
- Organisation Viewing
    * View organisation information
    * Organisation information may include:
        * Business profile
        * Contact information
        * Organisation status
        * Organisation configuration
- Organisation Update
    * Allow authorised users to update organisation information
    * Organisation updates may include:
        * Business name
        * Contact information
        * Business address
        * Organisation configuration
- Organisation Suspension
    * Allow authorised platform users to suspend an organisation
    * Suspended organisations cannot access StockFlow until the suspension is removed
    * Organisation data remains available for future reactivation
- Organisation Configuration Management
    * Configure organisation-specific settings
    * Organisation configuration may include:
        * Supported order workflows
        * Default order confirmation behaviour
        * Default currency
        * Time zone
    * Allow authorised users to update organisation configuration
- Shop Management
    * Create a shop under an organisation
    * View shop information
    * Update shop information
    * Activate, suspend, or disable a shop
    * Associate shop managers and staff with a shop

## Business Workflows

The following workflows describe the main business processes for organisation management

### Organisation Registration Workflow

- Platform Owner enters the organisation information
- Platform Owner submits the organisation registration request
- System validates the submitted organisation information
- System checks that the organisation does not already exist
- System creates the organisation
- System initialises the default organisation status and organisation configuration
- System returns the created organisation information

### Organisation Viewing Workflow

- User requests to view organisation information
- System checks the user's permission and access scope
- System verifies that the user is authorised to access the requested organisation
- System retrieves the organisation information
- System returns the permitted organisation information

### Organisation Update Workflow

- An authorised user requests to update organisation information
    - A `Platform Owner` selects an organisation they are authorised to manage
    - An `Organisation Owner` updates their own organisation
- System checks the user's permission and access scope
- Authorised user submits the updated organisation information
- System validates the submitted information
- System saves the updated organisation information
- System returns the updated organisation information

### Organisation Suspension Workflow

- `Platform Owner` requests to suspend an organisation
- System verifies the user's permission
- System verifies that the organisation exists
- System changes the organisation status to `Suspended`
- Suspended organisation users can no longer access StockFlow
- Organisation data remains available for future reactivation
- System returns the updated organisation information

### Organisation Configuration Update Workflow

- Authorised user requests to view or update organisation configuration
- System checks the user's permission and access scope
- System retrieves the permitted organisation configuration
- Authorised user submits the updated configuration settings
- System validates the submitted configuration
- System saves and applies the updated organisation configuration
- System returns the updated organisation configuration
