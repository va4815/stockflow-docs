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
