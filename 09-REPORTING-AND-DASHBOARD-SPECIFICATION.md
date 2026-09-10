# 9. Reporting & Dashboard Specification

## Dashboard

The console provides operational notifications derived from live data, including:

- New/confirmed orders
- Pending delivery
- Out-of-stock products
- Low-stock products

## Sales Report

The report includes:

- Date
- Invoice number
- Customer
- Products
- Units
- Payment
- Status
- Discount
- GST
- Revenue

Cancelled orders are excluded from the sales revenue report.

## Workbook Export

The full workbook includes:

1. Orders
2. Customers
3. Products
4. Inventory
5. Sold Units
6. Reviews
7. Coupons
8. Activity

## Customer Export

A customer export can contain:

- Profile
- Orders
- Items purchased
- Serials & warranty
- Reviews written

## Reporting Security

Exports may contain sensitive business/customer data. Production exports should:
- Require authorization.
- Log the export action.
- Apply data minimization.
- Use secure download URLs where possible.
- Avoid exposing unrestricted customer data.
