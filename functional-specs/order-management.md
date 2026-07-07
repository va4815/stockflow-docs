# Order Management

## Purpose

The purpose of Order Management is to create, process, track, and manage orders across StockFlow’s supported sales channels. It stores order details, order items, customer or merchant information, pricing, channel, and order status. Order Management also ensures that merchant users can only manage orders belonging to their own merchant organisation, while customers can only access and manage their own orders.

## Scope

Order Management provides the following capabilities for StockFlow.

### Initial Scope

- Create order through `POS`, `Self Checkout` or `Online Ordering` workflows
- Orders could be created by authorised merchant users or authenticated customers
- View order details and order history
- Cancel order

### Future Scope

- Anonymous purchase
- Refund or partial refund workflows
- Split orders
- Split payment
- Amend order after confirmation

## Order Concepts

Order Management uses the following concepts to describe how orders are created, processed, tracked, and owned within StockFlow.

### Orders

Order represents customer purchases the product(s) from the merchant via the supported channel. The order contains the purchase information, including merchant, customer or staff user, order status, order itmes and price.

### Order Items

Order item represents a product included in an order, it includes quantity, unit price when the order created.

Examples:

Restaurants - 

* Coffee (Regular size) x 2
* Spaghetti Bolognese x 1
* Cheese Cake (1 Slice) x 1

Retail -

* Logo T Shirt Mens x 3
* Superstar Slip On Trainers x 1
* Light Wash Slim Fit Jeans x 2

### Order Statuses

Order Statuses represents the stage of the order lifecycle

- `Pending` - Order submitted and is waiting for confirmation or processing
- `Confirmed` - Order has been accepted and inventory reserved
- `Processing` - Order is being prepared, picked or packed or fulfilled
- `Completed` - Order has been fulfilled and the stock has been deducted
- `Cancelled` - Order has been cancelled and the stock has been released

### Order price

Order price represents the purchase values marked for the order and its order items. The price should be included in the order record so that it keeps the record accurate even if the product price changes later.

### Order channels

Order channel represents the source or workflow where the order is created. It would be marked in the order record so that merchant could trace the order by channel.

Order channel includes:
- POS
- Retail
- Online

### Order Ownership

Order ownership defines which merchant, customer, or user is allowed to access and manage the order. Each order belongs to one merchant organisation, and merchant users can only access orders associated with their own merchant.


## User Roles and Responsibilities

The following roles define how users can access and manage the order.


### Platform Owner

The `Platform Owner` is responsible for operating and supporting the StockFlow platform.

Main responsibilities:
- Support `Merchants` to solve order-related platform issues
- View order information if required
- Investigate technical or operational issues when the order process is affected
- Manage order configuration if needed

### Merchant

The `Merchant` has the highest level of order access within their own merchant organisation.

Main responsibilities:

- View orders
- Create `Manual` order if needed
- Review orders
- Confirm orders
- Update orders
- Cancel orders
- Complete orders
- Review order history
- Manage merchant users access
- Resolve order issues

### Merchant Manager

The `Merchant Manager` is responsible for day-to-day order operations within the merchant organisation.

Main responsibilities:
- View orders
- Review incoming orders from `Online Ordering` and `Self Checkout` channels
- Create order from `POS` channel
- Create `Manual` order if needed
- Confirm orders
- Update orders
- Cancel orders
- Complete orders
- Review order history
- Handle order operational issues
- Support `Merchant Staff` during order processing

