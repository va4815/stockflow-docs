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

### Stock Quantities

Stock quantities represent the number of units recorded for an inventory item.

### Available, Reserved, and On-Hand Stock

* **On-hand** - The total physical quantity currently recorded at stock location
* **Reserved** - Allocated stock to orders but not yet deducted from the physical stock quantity
* **Available stock** - The quantity remains available for new orders


Available stock is calculated:

```
Available stock = On-hand stock - Reserved stock
```

### Inventory Movements

Inventory movement is a inventory item’s movement history, it provides a reason of quantity change

Examples:

- Stock addition
- Stock reservation
- Stock release
- Stock deduction
- Manual adjustment
- Stock restoration

### Inventory Adjustments

Inventory adjustment is to correct or update the stock quantity record

The stock needs to be changed due to the following reason:
- Physical stock counts
- Damaged item
- Lost stock
- Data-entry errors
- Unrecorded stock changes
- Other operational corrections

## User Roles and Responsibilities

The following roles define how users can access and manage the inventory.


### Platform Owner

The `Platform Owner` is responsible for supporting merchants to solve platform issues when merchants have troubles.

Main responsibilities:
- Support `Merchants` to solve inventory-related platform issues
- View inventory information if required
- Manage platform-level inventory configuration
- Investigate technical or operational issues affecting inventory processing

### Merchant

The `Merchant` has the highest level of inventory access within their own merchant organisation.

Main responsibilities:

- Create and maintain inventory records
- Manage stock locations
- View on-hand, reserved, and available stock quantities
- Add stock to inventory
- Adjust stock
- View inventory movement history
- Manage merchant users's inventory access
- Review and resolve inventory difference

