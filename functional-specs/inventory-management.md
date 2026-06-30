# Inventory Management

## Purpose

Inventory Management is to maintain accurate and consistent stock information across StockFlow’s supported channels.

Inventory Management tracks stock quantities for merchant products, including on-hand, reserved, and available stock. It supports stock additions, reservations, releases, deductions, adjustments, and movement history while ensuring that inventory changes remain associated with the correct merchant and stock location.

The module also prevents overselling by validating stock availability and handling concurrent inventory updates during order processing.

## Scope

Inventory Management provides the following capabilities for StockFlow.

### Initial Scope

- Create and maintain inventory records for merchant products
- Check on-hand, reserved, and available stock quantities
- Add stock to inventory record
- Check stock availability
- Reserve stock during order processing
- Release reserved stock when an order is cancelled or cannot be completed
- Reduce stock when the order is completed
- Restore stock when the order is canncelled
- Manual stock adjustments
- Record inventory movements for stock changes
- View inventory movement history
- Prevent stock quantities from becoming negative
- Handle concurrent stock updates to reduce the risk of overselling
- Restrict inventory access to the relevant merchant organisation

### Future Scope

- Transfer stock to another locations
- Damaged, lost, returned stock handling

## Inventory Concepts

Inventory Management uses the following concepts to track stock ownership, location, quantity, and changes within StockFlow.

### Inventory Items

Inventory item represents the stock record for a merchant product.

Examples:

Restaurants - 

* Coffee (Regular size)
* Spaghetti Bolognese
* Cheese Cake (1 Slice)

Retail -

* Logo T Shirt Mens
* Superstar Slip On Trainers
* Light Wash Slim Fit Jeans

### Stock Locations

Stock location represents the physical location where the inventory is stored.

Examples:

* The Noodle Fridge (Restaurant)
* The Captain Sport Store (Retail)
* The Captain Sport Store Warehouse (Warehouse)

