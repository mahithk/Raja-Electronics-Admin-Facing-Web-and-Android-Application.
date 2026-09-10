# 4. API & Backend Integration Specification

## 4.1 Objective

Replace client-side persistence and authentication with a trusted backend while preserving the existing Admin UI.

## 4.2 Authentication

Recommended endpoints:

```text
POST /api/auth/login
POST /api/auth/logout
GET  /api/auth/session
POST /api/auth/refresh
```

Credentials must never be trusted from browser storage.

## 4.3 Orders

```text
GET   /api/admin/orders
GET   /api/admin/orders/{orderId}
PATCH /api/admin/orders/{orderId}/status
```

## 4.4 Customers

```text
GET /api/admin/customers
GET /api/admin/customers/{customerId}
GET /api/admin/customers/{customerId}/orders
GET /api/admin/customers/{customerId}/warranty
```

## 4.5 Products

```text
GET    /api/admin/products
POST   /api/admin/products
PUT    /api/admin/products/{productId}
DELETE /api/admin/products/{productId}
```

## 4.6 Inventory

```text
GET  /api/admin/inventory
POST /api/admin/inventory/adjustments
GET  /api/admin/inventory/{productId}/ledger
```

## 4.7 Reviews

```text
GET   /api/admin/reviews
POST  /api/admin/reviews/{reviewId}/reply
PATCH /api/admin/reviews/{reviewId}/moderation
```

## 4.8 Coupons

```text
GET    /api/admin/coupons
POST   /api/admin/coupons
PUT    /api/admin/coupons/{couponId}
DELETE /api/admin/coupons/{couponId}
```

## 4.9 Reports

```text
GET /api/admin/reports/sales
GET /api/admin/reports/orders
GET /api/admin/reports/inventory
```

## 4.10 Audit

```text
GET /api/admin/audit
```

Audit records should be append-oriented and protected from ordinary admin modification.

## 4.11 API Security

Every write endpoint must:
- Authenticate the caller.
- Check role/permission.
- Validate request schema.
- Validate resource ownership/scope.
- Write an audit record.
- Return safe error messages.
