# Product Management

## Purpose

The purpose of Product Management is to create, maintain, organise, and control the products sold by organisations through StockFlow. It stores product information such as product name, description, category, price, status and channel visibility. Product Management also ensures that organisation users can only manage products belonging to their own organisation. Products created by one organisation must not be visible or manageable by another organisations.

## Scope

Product Management provides the following capabilities for StockFlow.

### Initial Scope

- Create products for an organisation
- View product details
- Update product information
- Disable products that should no longer be sold
- Create and manage product categories
- Assign products to categories
- Manage product pricing
- Search and filter products
- Provide products to `POS`, `Online Ordering`, `Self Checkout`, and `Manual` workflows
- Restrict product access by other organisations

### Future Scope

- Product images
- Support barcode or QR code
- Import and export product
- Product bundles
- Channel-specific pricing

## Product Concepts

Product Management uses the following concepts to describe how products are created, organised, priced, displayed, and controlled within StockFlow.

### Products

A product represents an item that an organisation can sell through one or more of its shops using StockFlow.

Examples:

Restaurants - 

- Coffee
- Spaghetti Bolognese
- Cheese Cake
- Chicken Burger

Retail -

- Logo T Shirt Mens
- Superstar Slip On Trainers
- Light Wash Slim Fit Jeans


### Product Categories

A product category is used to organise products into different groups.

Examples:

Restaurants -

- Drinks
- Main Course
- Desserts
- Snacks

Retail -

- T Shirts
- Shoes
- Jeans
- Accessories

### Product Pricing

Product pricing represents the unit price of the product. 

The product price is used by Order Management when creating orders. When an order is created, the product price should be copied into the order item so that the order history keeps the price accurate even if the product price changes later.

### Product Channel Visibility

Product channel visibility represents which workflows can display or sell a product.

Supported workflows include:

- `POS`
- `Online Ordering`
- `Self Checkout`
- `Manual`

### Product Status

Product status represents whether a product is available for use within the system.

Product statuses include:
- `Active` - the product can be viewed and sold
- `Inactive` - the product is temporarily unavailable but remains in the system
- `Disabled` - the product is no longer available through normal selling workflows

### Product Ownership

Product ownership defines which organisation owns and manages a product.

Every product belongs to exactly one organisation. Organisation users may only create, view, update, or disable products belonging to their own organisation. Products are isolated between organisations and cannot be accessed or modified by other organisations.

## User Roles and Responsibilities

The following roles define how users can manage the product.

### Platform Owner

The `Platform Owner` is responsible for operating the StockFlow platform and supporting organisations with product-related platform issues.

Main responsibilities:
- Support `Organisation Owner` with product-related platform issues
- View product information where required
- Manage platform-level product configuration
- Investigate technical or operational issues affecting product processing

### Organisation Owner

The `Organisation Owner` has the highest level of product access within their own organisation.

Main responsibilities:

- Create products
- View product details
- Update product information
- Disable products that are no longer sold
- Create and manage product categories
- Assign products to categories
- Manage product pricing
- Manage product channel visibility
- Review product status
- Manage product-related access for organisation users

### Shop Manager

The `Shop Manager` is responsible for day-to-day product management within the organisation.

Main responsibilities:

- Create products if authorised
- View product details
- Update product information
- Disable products if authorised
- Manage product categories
- Update product pricing if authorised
- Configure product visibility for different workflows
- Review product availability
- Support shop staff with product-related issues

### Shop Staff

The `Shop Staff` is responsible for daily restaurant or retail operations.

Main responsibilities:

- View product information, including product name, category and price
- Search and filter products
- Create POS orders using the products
- Report incorrect product information to `Organisation Owner` or `Shop Manager`

### Customer

The `Customer` is an external user who views and selects products through customer-facing workflows.

Main responsibilities:

- View products through `Online Ordering` or `Self Checkout`
- Select products for purchase

## Functional Capabilities

The Product Management module provides the following capabilities for managing products, categories, pricing and visibility.

- Product Creation
    * Create a product record within the organisation
    * Product information may include
        * Product name
        * Description
        * Category
        * Unit price
        * Product status
        * Channel visibility
- Product Viewing
    * View the product information
    * Organisation users can view:
        * Product name
        * Description
        * Category
        * Unit price
        * Product status
        * Channel visibility
    * Customers can view:
        * Product name
        * Description
        * Category
        * Unit price
- Product Update
    * Allow authorised users to update product information
    * Product updates may include:
        * Product name
        * Description
        * Category
        * Unit price
        * Product status
        * Channel visibility
- Product Availability
    * Determine whether a product can be sold
    * Product availability is determined by:
        * Product status
        * Channel visibility
        * Inventory availability
- Product Disablement
    * Allow authorised users to disable products that should no longer be sold
    * Disabled product should not be available for new orders
- Product Category Management
    * Use product category to group products
    * Product category may include
        * Category name
        * Description
        * List of products
        * Category visibility
    * Product Category Management includes the following features
        * Create product category
        * View product category
        * Update product category, including
            * Category name
            * Description
            * Assign products to category
        * Disable category
- Product Search and Filtering
    * Organisation users can search and filter products by:
        * Product name
        * Description
        * Category
        * Price range
        * Product status
        * Channel visibility
    * Customers can search and filter products by:
        * Product name
        * Description
        * Category
        * Price range

## Business Workflows

The following workflows describe the main business processes for creating, maintaining, displaying, and managing products within StockFlow.

### Product Creation Workflow

- Organisation user enters the product information, including product name, category, price, status, and channel visibility
- Organisation user submits product information to the system
- System checks the user's permission and organisation scope
- System validates the submitted product information
- System verifies that the selected category belongs to the organisation
- System assigns the product to the organisation
- System creates the product record
- System returns the created product information

### Product Update Workflow

- Organisation user selects an existing product
- System checks the user's permission and organisation scope
- Organisation user submits the updated product information
- System validates the updated information
- System verifies that the product belongs to the organisation
- System saves the updated product information
- System returns the updated product information

### Product Viewing Workflow

- User requests to view the product(s)
- System checks the user's permission and access scope
- System retrieves the product information by organisation ownership, product status, and channel visibility
- System returns the permitted product information

### Product Disablement Workflow

- Organisation user requests to disable a product
- System checks the user's permission and organisation scope
- System verifies that the product belongs to the organisation
- System changes the product status to `Disabled`
- System returns the updated product information

### Category Creation Workflow

- Organisation user enters the category information
- Organisation user submits the category
- System checks the user's permission and organisation scope
- System validates the submitted category information
- System creates the category
- System returns the created category information

### Category Update Workflow

- Organisation user selects an existing category
- System checks the user's permission and organisation scope
- Organisation user submits the updated category information
- System verifies that the category belongs to the organisation
- System saves the updated category
- System returns the updated category information

### Product Assignment to Category Workflow

- Organisation user selects a category
- Organisation user selects a product
- System checks the user's permission and organisation scope
- System verifies that both the product and category belong to the same organisation
- System associates the product with the selected category
- System returns the updated product information

### Channel Visibility Update Workflow

- Organisation user selects an existing product
- Organisation user selects the workflows where the product should be available
- System checks the user's permission and organisation scope
- System validates the selected channel visibility
- System updates the product channel visibility
- System returns the updated product information

### Product Search Workflow

- User enters search criteria
- System checks the user's permission and access scope
- System searches products using the specified criteria
- System applies organisation ownership, product status, and channel visibility rules
- System returns the matching products
