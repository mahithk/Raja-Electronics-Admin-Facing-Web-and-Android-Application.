# 3. System Architecture

## 3.1 Current Architecture

```text
+---------------------------+
| Raja Electronics Admin UI |
+-------------+-------------+
              |
       +------+------+
       | Application |
       |   Logic     |
       +------+------+
              |
      +-------+--------+
      | Auth / Repo /  |
      | Audit / Notify |
      +-------+--------+
              |
       +------+------+
       | Browser DB  |
       | localStorage|
       +-------------+
              |
       Same-origin shop data
              |
       +------+------+
       | Customer    |
       | Storefront  |
       +-------------+
```

## 3.2 Recommended Production Architecture

```text
Admin Browser
     |
 HTTPS
     |
 API Gateway / Spring Boot
     |
 +---+-----------------------------+
 | Auth & RBAC | Business Services |
 +---+-----------------------------+
             |
     +-------+--------+
     | Relational DB  |
     +----------------+
             |
      Audit / Reporting
```

## 3.3 Repository Seam

The source intentionally isolates data access behind `Repo`. This allows the local implementation to be replaced with REST-backed implementations.

Example conceptual mapping:

```text
Repo.orders.list()       -> GET /api/admin/orders
Repo.products.list()     -> GET /api/admin/products
Repo.products.save()     -> POST/PUT /api/admin/products
Repo.customers.list()    -> GET /api/admin/customers
Repo.reviews.list()      -> GET /api/admin/reviews
```

## 3.4 Important Integration Boundary

The customer storefront currently keeps some information in source code rather than shared storage. Products, cancelled-order state and review moderation state therefore require additional storefront integration before admin changes can automatically round-trip to the customer UI.
