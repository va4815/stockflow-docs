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

