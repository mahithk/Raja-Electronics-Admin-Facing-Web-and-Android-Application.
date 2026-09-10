🛡️ RAJA ELECTRONICS — Admin Website & Application

<p align="center">
  <strong>Enterprise Administration Console for Raja Electronics</strong>
</p>

<p align="center">
  Centralized management for orders, customers, products, inventory, warranty, reviews, coupons, reports, audit activity and administrative settings.
</p>

📌 Overview

RAJA ELECTRONICS Admin is a responsive web-based administration console designed to provide authorized staff with a centralized interface for managing and monitoring the Raja Electronics business platform.

The application provides an administrative workspace covering the complete operational lifecycle — from orders and customers to products, inventory, warranty, reviews, coupons, reporting, exports and audit activity.

The current implementation is a client-side HTML/JavaScript prototype with a deliberately separated authentication (Auth) and repository (Repo) architecture. The source is structured so the local storage implementation can later be replaced with a Spring Boot / REST backend without redesigning the application screens.

Important: The current browser-based authentication and role enforcement are not a production security boundary. Production deployment must use server-side authentication, authorization and persistent backend storage.

✨ Key Features

📊 Dashboard

Operational KPI overview

Order activity monitoring

Inventory alerts

Low-stock and out-of-stock indicators

Quick access to operational sections

Dynamic navigation badges

🧾 Orders & Invoices

View customer orders

Invoice-level information

Customer and contact details

Product and quantity information

Payment status

Order status

Subtotal

Discounts

GST

Delivery charges

Grand total

Cancelled-order state

Excel/CSV reporting

👥 Customer Management

Customer listing

Customer search

Customer profile information

Order history

Purchased items

Sold units

Warranty information

Reviews written by the customer

Customer-specific data export

Filtered customer export

🏷️ Product Catalogue

Product catalogue management

Product ID

Product name

Brand

Model number

Category

HSN code

Selling price

MRP

Discount

GST

Warranty

Stock

Active/inactive state

Product create/update/delete operations

Catalogue export

📦 Inventory Management

Current stock monitoring

Stock ledger

Sold quantity tracking

Stock adjustments

Low-stock threshold

Out-of-stock detection

Inventory activity history

🔎 Sold Units & Warranty

Sold-unit tracking

Serial/unit information

Product/model

Sold date

Warranty term

Warranty expiry

Days remaining

Warranty status

Invoice reference

Customer information

⭐ Reviews

Customer reviews

Product/target information

Author

Rating

Review content

Shop reply

Answered state

Administrative review state

🎟️ Coupons

Coupon code management

Percentage/fixed coupon concepts

Minimum order amount

Maximum discount

Expiry date

Usage count

Usage limit

Coupon status

📈 Reports & Analytics

Sales reporting

Period-based reports

Orders

Units

Discounts

GST

Revenue

Sales charts

Excel export

CSV export

Cancelled orders excluded from sales figures

📤 Business Data Export

The application supports structured business exports for operational analysis and backup.

Export areas include:

Orders

Products

Customers

Inventory

Sold units

Warranty

Reviews

Coupons

Activity/Audit

Customer-level exports can contain:

Profile

Orders

Purchased items

Serial & warranty information

Reviews

🕵️ Audit & Activity Log

Administrative actions can be recorded with:

Timestamp

Administrator

Role

Action

Record

Previous value

New value

This provides an operational history of important changes.

🛡️ Authentication & RBAC

The application contains an Auth abstraction for:

Login

Logout

Session management

Idle timeout

Role checks

Permission checks

User management

Configured role concepts include:

Super Admin

Manager

Sales Staff

Inventory Staff

Support Staff

Permissions are represented at the feature/action level, such as:

orders.write
products.write
stock.write
customers.write
reviews.write
coupons.write
reports.read
audit.read
backup.write

💾 Data & Backup

The console includes browser-storage administration with:

Backup creation

Backup validation

Restore support

Safety backup before restore

Scoped data deletion

Full shop-data reset

Storage inspection

⚙️ Settings

Configurable administrative settings include:

Shop name

Currency

Low-stock threshold

Session idle timeout

♿ Accessibility

The interface provides accessibility and presentation controls including:

Interface scaling

Density settings

Contrast

Reduced motion

Speech/read-out preference

Link underline preference

🌗 Appearance

Dark mode

Light mode

Responsive layout

Mobile navigation drawer

Print-friendly views

🔍 Global Search

A global search mechanism is provided for finding relevant business records without relying on a permanently cached search index.

🏗️ Architecture

The application follows a layered client-side architecture:

┌─────────────────────────────────────┐
│       RAJA ELECTRONICS ADMIN        │
│          HTML / CSS / JS            │
└──────────────────┬──────────────────┘
                   │
          ┌────────▼────────┐
          │  Screen / UI    │
          │     Logic       │
          └────────┬────────┘
                   │
        ┌──────────▼──────────┐
        │      Auth / RBAC    │
        │      Repo / Audit   │
        │      Settings       │
        └──────────┬──────────┘
                   │
          ┌────────▼────────┐
          │ Browser Storage  │
          │   localStorage   │
          └────────┬────────┘
                   │
          Shared shop data
                   │
          ┌────────▼────────┐
          │ Customer Website │
          └──────────────────┘

🔌 Repository Layer

Business screens communicate through the Repo layer instead of directly accessing browser storage.

Conceptually:

Repo.orders.list()
Repo.products.list()
Repo.products.save(product)
Repo.stock.rows()
Repo.customers.list()
Repo.reviews.list()

This creates a clean migration path:

Current:
Admin UI → Repo → localStorage

Production:
Admin UI → Repo → REST API → Spring Boot → Database

The source explicitly describes this as a seam for a future Spring Boot backend.

🔐 Security Architecture

Current Prototype

The current authentication implementation is intentionally isolated inside Auth.

However, because this is a static HTML application:

Client-side credentials and role checks can be inspected or modified by a user.

Therefore, the current implementation should be treated as a prototype authentication model, not production authentication.

Recommended Production Architecture

Admin Browser
      │
      │ HTTPS
      ▼
┌─────────────────────┐
│ Spring Boot Backend │
├─────────────────────┤
│ Authentication      │
│ Authorization / RBAC│
│ Business APIs       │
│ Audit Logging       │
└──────────┬──────────┘
           │
           ▼
    ┌──────────────┐
    │   Database   │
    └──────────────┘

Production should enforce authorization on the server for every protected operation.

Recommended controls:

HTTPS

Secure authentication

Password hashing

Server-side RBAC

Session/token expiration

Rate limiting

Input validation

CSRF protection where applicable

Secure cookies/token handling

Audit logging

Database authorization

Backup and recovery

Restricted exports

🔄 Customer Website Integration

The Admin console is designed to work with data used by the Raja Electronics customer website.

The current implementation uses namespaced browser storage for shop data.

Examples include:

re_invoices
re_accounts
re_stock
re_reviews
re_used_coupons

Admin-owned data uses an admin_ namespace.

Examples:

admin_products
admin_review_state
admin_coupons
admin_stock_log
admin_audit
admin_users
admin_session
admin_settings

⚠️ Same-Origin Requirement

When the current browser-storage integration is used, the Admin application and customer website must be served from the same origin.

Do not rely on opening the HTML directly with:

file://

Use an HTTP server instead.

🔁 Current Integration Limitations

Some Admin data is intentionally stored separately because the customer website currently keeps corresponding information in source code or does not consume the administrative state.

Products

The Admin console maintains its own editable product store.

The catalogue can be exported as a shop block for integration with the customer website.

Cancelled Orders

The Admin console supports:

adminStatus: "cancelled"

The customer website must be updated to consume this state if cancelled orders are expected to appear there.

Review Moderation

Administrative review state is stored separately.

The customer website must filter against the administrative moderation state if rejected reviews should be hidden from customers.

🧰 Technology Stack

Layer

Technology

Markup

HTML5

Styling

CSS3

Application Logic

Vanilla JavaScript

Storage

Browser localStorage

Charts

CSS / SVG

Export

Client-side CSV / Excel-style workbook generation

Responsive UI

CSS Media Queries

Authentication Seam

JavaScript Auth abstraction

Data Access

JavaScript Repo abstraction

Future Backend

Spring Boot / REST API

📱 Responsive Design

The Admin console is designed for:

🖥️ Desktop

💻 Laptop

📱 Mobile

📟 Tablet

On smaller screens, the desktop sidebar transforms into a navigation drawer.

Tables support horizontal scrolling to preserve administrative data density.

The application also provides print-specific styling for cleaner printed reports.

🚀 Running Locally

Because the application relies on browser storage and same-origin behavior, serve it using a local HTTP server.

Option 1 — Python

python -m http.server 8000

Open:

http://localhost:8000/admin_v62(2).html

Option 2 — VS Code

Install the Live Server extension and open the HTML using Live Server.

Example:

http://127.0.0.1:5500/admin_v62(2).html

Keep the customer website and Admin website under the same origin when testing shared browser-storage integration.

📂 Recommended Repository Structure

raja-electronics-admin-app/
│
├── admin_v62(2).html
│
├── README.md
├── .gitignore
├── LICENSE
│
├── assets/
│   ├── images/
│   ├── icons/
│   └── logos/
│
└── docs/
    ├── 01-SOFTWARE-REQUIREMENTS-SPECIFICATION.md
    ├── 02-TECHNICAL-SPECIFICATION.md
    ├── 03-SYSTEM-ARCHITECTURE.md
    ├── 04-API-BACKEND-INTEGRATION-SPEC.md
    ├── 05-ADMIN-MODULE-SPECIFICATION.md
    ├── 06-ROLE-AND-ACCESS-CONTROL.md
    ├── 07-INVENTORY-MANAGEMENT-SPECIFICATION.md
    ├── 08-ORDER-BILLING-PAYMENT-SPECIFICATION.md
    ├── 09-REPORTING-AND-DASHBOARD-SPECIFICATION.md
    ├── 10-TEST-PLAN.md
    ├── 11-DEPLOYMENT-GUIDE.md
    ├── 12-SECURITY-AND-COMPLIANCE.md
    ├── 13-ADMIN-USER-GUIDE.md
    ├── 14-CHANGELOG.md
    └── 15-CONTRIBUTING.md

🧑‍💼 Admin User Journey

        ┌───────────────┐
        │  Admin Login  │
        └───────┬───────┘
                │
                ▼
        ┌───────────────┐
        │   Dashboard   │
        └───────┬───────┘
                │
       ┌────────┼────────┐
       ▼        ▼        ▼
    Orders   Customers Products
       │        │        │
       │        │        ▼
       │        │    Inventory
       │        │        │
       │        │        ▼
       │        │   Sold/Warranty
       │        │
       │        ▼
       │      Reviews
       │
       ├──────► Reports
       ├──────► Coupons
       ├──────► Activity Log
       ├──────► Data & Backup
       └──────► Settings

📊 Business Data Coverage

Area

Admin Capability

Orders

✅

Invoices

✅

Customers

✅

Products

✅

Catalogue

✅

Inventory

✅

Sold Units

✅

Warranty

✅

Reviews

✅

Coupons

✅

Sales Reports

✅

Excel Export

✅

CSV Export

✅

Audit Log

✅

Admin Users

✅

Backup & Restore

✅

Global Search

✅

Dark/Light Mode

✅

Accessibility

✅

Responsive UI

✅

Backend API

🔄 Migration seam

Production Authentication

🔄 Requires backend

📈 Reporting & Export

The application provides operational exports for business analysis.

Orders Export

Includes information such as:

Invoice No.
Date
Time
Customer
Mobile
Owner
Products
Units
Payment
Paid
Status
Subtotal
Discount
GST
Delivery
Grand Total

Product Export

Includes:

Product ID
Product Name
Brand
Model
Category
HSN
Selling Price
MRP
Discount %
GST %
Warranty
Stock
Status

Customer Export

Can combine:

Profile
Orders
Purchased Items
Warranty
Reviews

💾 Backup & Recovery

The Admin console includes backup validation and restoration mechanisms.

A restore operation creates a safety copy before replacing live data.

Recommended production improvements:

Server-side backups

Scheduled backups

Database point-in-time recovery

Off-site backup storage

Encryption

Restore drills

Backup retention policy

🧪 Testing

Before production deployment, test:

Functional

Login/logout

Session timeout

Dashboard

Orders

Customers

Products

Inventory

Warranty

Reviews

Coupons

Reports

Exports

Backup/restore

Security

Authentication bypass

Role manipulation

Unauthorized API access

IDOR/resource access

XSS

CSRF

Injection

Session attacks

Export authorization

Responsive

Desktop

Tablet

Mobile

Navigation drawer

Tables

Forms

Modals

Print output

🔮 Recommended Production Roadmap

Phase 1 — Backend

Spring Boot
REST APIs
Database
Authentication
RBAC

Phase 2 — Security

HTTPS
Password hashing
Secure sessions
API authorization
Audit logging
Rate limiting

Phase 3 — Data Migration

Move:

localStorage
    ↓
REST API
    ↓
Database

Phase 4 — Integration

Connect:

Customer Website
       ↕
   Backend API
       ↕
 Admin Console

This eliminates the need for fragile same-origin browser-storage synchronization.

Phase 5 — Production Operations

Add:

Monitoring

Error tracking

Automated backups

CI/CD

Automated testing

Database migrations

API documentation

Disaster recovery

🏆 Project Highlights

🎯 Purpose-built administration interface

🧩 Clear Auth abstraction

🗄️ Clear Repo data-access abstraction

🕵️ Audit logging

📊 Operational reporting

📤 Business data exports

📦 Inventory and warranty tracking

⭐ Review management

🎟️ Coupon management

🔎 Global search

💾 Backup and restore

🌗 Dark/light themes

♿ Accessibility controls

📱 Responsive mobile navigation

🖨️ Print support

🔄 Designed for Spring Boot migration

⚠️ Production Readiness Notice

This repository contains a client-side administration prototype.

The UI, business workflows and backend migration seams are suitable as a foundation, but the following must be moved to a trusted backend before production use:

Credentials

Authentication

Authorization

Role enforcement

Business-critical mutations

Payment/order authority

Customer-sensitive data

Audit persistence

Backup storage

Never consider a browser-side password, role or permission check sufficient for protecting an administrative system.

📄 Documentation

Detailed technical documentation is available under:

/docs

Recommended starting points:

01-SOFTWARE-REQUIREMENTS-SPECIFICATION.md

02-TECHNICAL-SPECIFICATION.md

03-SYSTEM-ARCHITECTURE.md

04-API-BACKEND-INTEGRATION-SPEC.md

06-ROLE-AND-ACCESS-CONTROL.md

12-SECURITY-AND-COMPLIANCE.md

🤝 Contributing

When modifying the Admin console:

Keep data access inside Repo.

Keep authentication inside Auth.

Preserve role/permission checks.

Record important mutations through audit logging.

Test responsive layouts.

Test exports after data-model changes.

Avoid exposing credentials or secrets.

Update documentation for major functionality changes.
