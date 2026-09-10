# 6. Role & Access Control

## Current Model

The source implements a role/permission map and a wildcard permission for Super Admin. Permission checks are centralized through `Auth.can()`.

## Recommended Roles

| Role | Intended Access |
|---|---|
| Super Admin | Full administrative access |
| Admin | Operational management |
| Manager | Orders, customers, catalogue, inventory, reports |
| Support | Customers, orders, reviews |
| Inventory Manager | Catalogue and inventory |
| Finance | Orders, invoices, payments and reports |

These role names are a recommended production model; only roles actually configured in the source should be treated as existing runtime roles.

## Permission Examples

```text
dashboard.read
orders.read
orders.write
customers.read
products.read
products.write
inventory.read
inventory.write
reviews.read
reviews.write
coupons.read
coupons.write
reports.read
audit.read
data.write
settings.write
```

## Critical Rule

UI permission checks are convenience controls, not security controls. The backend must enforce the same permissions on every API request.
