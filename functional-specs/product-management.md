# Product Management

## Purpose

The purpose of Product Management is to create, maintain, organise, and control the products to support merchants to process StockFlow’s's workflows. It stores the product information such as product name, description, category, price, status and channel visibility. Product Management also ensures that merchant users can only manage products belonging to their own merchant organisation. Products created by one merchant must not be visible or manageable by another merchant.

## Scope

Product Management provides the following capabilities for StockFlow.

### Initial Scope

- Create products for a merchant
- View product details
- Update product information
- Disable products that should no longer be sold
- Create and manage product categories
- Assign products to categories
- Manage product pricing
- Search and filter products
- Manage `POS`, `Online Ordering`, and `Self Checkout` workflows to retrieve available products
- Restrict product access by other merchants

### Future Scope

- Product images
- Support barcode or QR code
- Import and export product
- Product bundles
- Channel-specific pricing

## Product Concepts

Product Management uses the following concepts to describe how products are created, organised, priced, displayed, and controlled within StockFlow.

### Products

A product represents an item that a merchant can sell through StockFlow.

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

The product price is used by Order Management when creating orders. When an order is created, the product price should be copied into the order item so that the order history keeps the price accurates even if the product price changes later.

### Product Channel Visibility

Product channel visibility represents which workflows can display or sell a product.

Supported workflows include:

- `POS`
- `Online Ordering`
- `Self Checkout`
- `Manual`

### Product Status

Product status represents different situations to be used in the system.

Product statuses include:

- `Active` - the product can be viewed and sold
- `Inactive` - the product is unavailable but remains in the system
- `Disabled` - the product is no longer used for normal selling workflows

### Product Ownership

Product ownership represents which merchant organisation owns and manages a product.

Each product belongs to one merchant organisation. Merchant users can use to create, view, update, or disable products belonging to their own merchant.

## User Roles and Responsibilities

The following roles define how users can manage the product.

### Platform Owner

The `Platform Owner` is responsible for supporting merchants to solve platform issues when merchants have troubles.

Main responsibilities:
- Support `Merchant` to solve product-related platform issues
- View product information if required
- Manage platform-level product configuration
- Investigate technical or operational issues affecting product processing

### Merchant

The `Merchant` has the highest level of product access within their own merchant organisation.

Main responsibilities:

- Create products
- View product details
- Update product information
- Disable products if no longer be sold
- Create and manage product categories
- Assign products to categories
- Manage product pricing
- Manage product channel visibility
- Review product status
- Manage product-related access for merchant users

### Merchant Manager

The `Merchant Manager` is responsible for day-to-day product management within the merchant organisation.

Main responsibilities:

- Create products if authorised
- View product details
- Update product information
- Disable products if authorised
- Manage product categories
- Update product pricing if authorised
- Configure product visibility for different workflows
- Review product availability
- Support merchant staff with product-related issues

### Merchant Staff

The `Merchant Staff` is responsible for daily restaurant or retail operations.

Main responsibilities:

- View product information
- Search and filter products
- Create POS orders using the products
- Report incorrect product information to a `Merchant` or `Merchant Manager`

### Customer

The `Customer` is an external user who views and selects products through customer-facing workflows.

Main responsibilities:

- Purchase products through `Online Ordering` or `Self Checkout`
- View product information

## Functional Capabilities

The Product Management module provides the following capabilities for managing products, categories, pricing and visibility

- Product Creation
    * Create a product record within the merchant organisation
    * Product information may include
        * Product name
        * Description
        * Category
        * Unit price
        * Product status
        * Channel visibility
- Product Viewing
    * View the product information
    * When `Merchant` views the product, it includes:
        * Product name
        * Description
        * Category
        * Unit price
        * Product status
        * Channel visibility
    * When `Customer` views the product, it includes:
        * Product name
        * Description
        * Category
        * Unit price
- Product Update
    * Update the product information from authorised users
    * Product updates may include:
        * Product name
        * Description
        * Category
        * Unit price
        * Product status
        * Channel visibility
- Product Disablement
    * Disable the product from authorised users when the product is no longer be sold
    * Disabled product should not be available for new orders
- Product Category
    * Use product category to group products
    * Product category may include
        * Category name
        * Description
        * List of products
        * Category visibility
    * Product category includes the following features
        * Create product category
        * View product category
        * Update product category, including
            * Category name
            * Description
            * Assign products to category
        * Disable category
- Search and Filter Product
    * When `Merchant` searchs the product, the keyword includes:
        * Product name
        * Description
        * Category
        * Price range
        * Product status
        * Channel visibility
    * When `Customer` searchs the product, the keyword includes:
        * Product name
        * Description
        * Category
        * Price range

## Business Workflows

The following workflows describe the main business processes for creating, maintaining, displaying, and managing products within StockFlow.

### Product Creation Workflow

- Merchant user enters the product information, including product name, category, price, status, and channel visibility
- Merchant user submits product information to the system
- System checks the user's permission and merchant scope
- System validates the submitted product information
- System verifies that the selected category belongs to the merchant organisation
- System creates the product record
- System returns the created product information

### Product Update Workflow

- Merchant user selects an existing product
- System checks the user's permission and merchant scope
- Merchant user submits the updated product information
- System validates the updated information
- System verifies that the product belongs to the merchant organisation
- System saves the updated product information
- System returns the updated product information
