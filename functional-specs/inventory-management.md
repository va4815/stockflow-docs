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

### Merchant Manager

The `Merchant Manager` is responsible for day-to-day inventory operations within the merchant organisation.

Main responsibilities:

- View inventory record and stock availability
- Add stocks if need
- Adjust inventory
- Review reserved and available stock
- View inventory movement history
- Investigate stock difference
- Support order processing when inventory issues occurred

### Merchant Staff

The `Merchant Staff` role supports daily operations and order-processing activities.

Main responsibilities:

- View product stock availability
- Check stock availability
- Reserve and release stock through order-processing workflows
- Report to `Merchant` or `Merchant Manager` to refill stocks

## Functional Capabilities

The Inventory management module provides the following capabilities for managing the quantities of stocks

- Stock Availability
    * View the available stock by product
    * Check if sufficient stock for an order
- Stock Reservation
    * Reserve stock for orders
- Stock Release
    * Release the stock when the order is cancelled
    * Release the stock when the order cannot be completed
- Stock Deduction
    * Deduct the stock when the order is completed
- Stock Adjustment
    * Increase or decrease the on-hand quantity
- Inventory Movement History
    * View the inventory item movement
    * Record reason of movement, date and user to process

## Business Workflows

The following workflows describe the main steps of quantities change at the stock management operations.

### Stock Addition Workflow

- User selects an inventory item
- Enter the quantity to be added to the item
- System checks the user permission and merchant scope
- System validates the quantity if it is greater than zero
- System updates on-hand quantity
- System makes an inventory movement record on the item

### Stock Reservation Workflow

- Customer or merchant staff creates an order
- System verifies the items belong to the merchant
- System checks available stock on the inventory item
- System updates reserved stocks (increase)
- System udpates available stocks (decrease)
- System makes an inventory movement record

### Stock Deduction Workflow

- User selects an inventory item
- Enter the quantity to be deducted to the item
- System checks the user permission and merchant scope
- System validates the quantity if it is greater than zero
- System updates on-hand quantity
- System makes an inventory movement record on the item

