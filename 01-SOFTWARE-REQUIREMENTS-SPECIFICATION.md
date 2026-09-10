# 1. Software Requirements Specification

## 1.1 Purpose

Define the requirements for the Raja Electronics Admin Website/Application used by authorized staff to monitor and manage the customer storefront's operational data.

## 1.2 Scope

The console covers:

- Authentication/session handling
- Role-based access
- Dashboard/KPIs
- Orders and invoices
- Customers
- Products/catalogue
- Inventory
- Sold units and warranty
- Reviews
- Coupons
- Reports
- Data administration
- Audit/activity
- Notifications
- Settings/accessibility
- Search and exports

## 1.3 Functional Requirements

### Authentication
- Admin must sign in before accessing the console.
- Session state must be maintained.
- Idle timeout and logout must be supported.
- Production credentials must be validated server-side.

### Dashboard
- Display operational KPIs.
- Surface order and stock notifications.
- Provide quick navigation to affected records.

### Orders
- List orders/invoices.
- Search/filter orders.
- View order details.
- Display customer, products, payment, discounts, GST, delivery and grand total.
- Track order status.
- Export order data.

### Customers
- List customers.
- Search/filter customers.
- View customer-level order and ownership information.
- Export filtered customer data.
- Export a customer's profile, orders, items, warranty and reviews.

### Catalogue
- Maintain product records.
- Manage product attributes such as name, brand, model, category, HSN, price, MRP, GST, warranty and active status.
- Export catalogue data.
- Generate a shop catalogue block for the current architecture.

### Inventory
- Monitor stock on hand.
- Identify healthy, low-stock and out-of-stock states.
- Maintain stock ledger/adjustments where supported.

### Sold Units & Warranty
- Track serial numbers and sold units.
- Show warranty term, expiry, remaining days and warranty state.
- Link units to invoices/customers.

### Reviews
- Display reviews, ratings and replies.
- Track whether a review has been answered.
- Maintain admin review state.
- Note: storefront filtering must be added separately if moderation state is to hide rejected reviews from customers.

### Coupons
- Manage custom coupon codes.
- Support percentage/fixed amount concepts.
- Track minimum order, maximum discount, expiry, usage and limits.
- Display Active, Inactive, Expired and Used up states.

### Reporting
- Generate sales reports.
- Exclude cancelled orders from revenue reporting.
- Export operational workbooks.

### Audit
- Record mutating actions with administrator, role, record and before/after values.
- Bound the stored audit history.

### Data Administration
- Support scoped deletion where implemented.
- Require confirmation for destructive actions.
- Provide full reset only with explicit confirmation.

## 1.4 Non-Functional Requirements

- Responsive from desktop to mobile.
- Keyboard-accessible controls.
- Clear status indicators.
- Fast scanning of tables.
- Print-friendly output.
- Avoid unbounded client-side logs/data.
- Production APIs must enforce authorization independently of UI.

## 1.5 Constraints

The current website is a static HTML implementation and therefore cannot provide a trustworthy security boundary. The source itself identifies client-side credentials/roles as bypassable and labels the local authentication implementation as a prototype.
