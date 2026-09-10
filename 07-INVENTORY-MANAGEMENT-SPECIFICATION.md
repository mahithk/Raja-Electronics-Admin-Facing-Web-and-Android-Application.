# 7. Inventory Management Specification

## Product Stock

Product data includes stock-related information and the repository exposes inventory/stock views.

## Stock States

- Healthy
- Low stock
- Out of stock

## Inventory Operations

- View current quantity
- Review stock ledger
- Identify low stock
- Identify out-of-stock products
- Export inventory

## Sold Units

Sold-unit reporting includes:

- Serial/unit identifier
- Product/model
- Sold date
- Warranty term
- Warranty expiry
- Days remaining
- Warranty status
- Invoice
- Customer
- Mobile

## Production Recommendations

Stock adjustments should be transactional on the backend. Every adjustment should record:

```text
product
previous quantity
adjustment quantity
new quantity
reason
admin
timestamp
reference
```
