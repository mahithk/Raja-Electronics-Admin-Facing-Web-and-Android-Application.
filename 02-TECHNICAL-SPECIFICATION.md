# 2. Technical Specification

## 2.1 Current Technology

- HTML5
- CSS3
- Vanilla JavaScript
- Browser storage
- CSS/SVG-based charts
- Client-side workbook/export generation
- Responsive CSS
- No requirement for a frontend framework in the current implementation

## 2.2 Design System

The console uses a dense administrative visual language:

- Near-black dark theme
- Light theme
- Blue interaction accent
- Green success state
- Amber warning state
- Red destructive state
- Tabular numerals
- Rounded panels and controls
- Responsive drawer navigation

## 2.3 Application Layers

### Presentation
HTML screens, tables, forms, modals, navigation, notifications and responsive layout.

### Application Logic
Navigation, dashboards, search, reports, export functions, settings and workflow handlers.

### Repository Layer
`Repo` provides business collection methods such as orders, products and related data access. The architecture is designed so storage implementation can be replaced by REST calls without rewriting screen code.

### Authentication/Authorization
`Auth` is the single seam for session and role checks. Production implementation should replace its local credential logic with backend authentication.

### Audit
Mutating repository operations produce audit entries containing timestamp, administrator, role, action, record and truncated before/after values.

## 2.4 Storage

Current implementation uses browser storage. Customer/shop records may be namespaced by customer email. The admin repository discovers storage slices rather than assuming a single bare key.

## 2.5 Export

The application supports workbook-style exports containing sheets for:

- Orders
- Customers
- Products
- Inventory
- Sold Units
- Reviews
- Coupons
- Activity

Customer-specific exports can additionally include profile, orders, purchased items, warranty and reviews.

## 2.6 Accessibility

Current controls include configurable scale, density, contrast, motion, speech and underline preferences. Settings persist per browser.

## 2.7 Responsive Behavior

- Desktop: fixed sidebar
- Smaller screens: navigation drawer
- Mobile: compact tables with horizontal scrolling
- Modals adapt to viewport dimensions
- Print stylesheet hides application chrome
