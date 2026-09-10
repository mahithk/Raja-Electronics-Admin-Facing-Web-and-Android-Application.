# 8. Order, Billing & Payment Specification

## Order Data

The admin export model includes:

- Invoice number
- Date/time
- Customer
- Mobile/email
- Owner
- Products
- Units
- Payment method
- Paid state
- Order status
- Subtotal
- Discount
- GST
- Delivery
- Grand total

## Order Status

The console derives order status and supports cancelled-order state on the admin side.

## Cancelled Orders

The source documents an integration limitation: the customer storefront's tracking steps do not contain a cancel step. The admin side stores cancelled state separately, so the storefront must be updated to consume it if cancellation must be visible to customers.

## Payment

Payment confirmation must be authoritative on the backend. Never mark an order paid solely because a browser callback or local storage value says so.

## Invoice

Production invoices should be generated from trusted backend order data and should have server-side access control.
