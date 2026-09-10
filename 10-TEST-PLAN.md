# 10. Test Plan

## Authentication Tests
- Valid login
- Invalid login
- Logout
- Session expiry
- Idle timeout
- Unauthorized route access
- Role permission checks

## Dashboard Tests
- KPI calculation
- New order notification
- Pending delivery notification
- Low-stock notification
- Out-of-stock notification

## Order Tests
- Search
- Detail view
- Status changes
- Payment state
- Totals
- Cancelled state
- Export

## Customer Tests
- Search/filter
- Profile
- Order history
- Warranty
- Customer export

## Catalogue Tests
- Create
- Edit
- Delete/deactivate
- Price validation
- GST/HSN fields
- Export
- Shop catalogue synchronization

## Inventory Tests
- Quantity changes
- Low-stock threshold
- Out-of-stock state
- Ledger
- Serial/warranty data

## Review Tests
- Review display
- Reply
- Moderation state
- Storefront filtering integration

## Coupon Tests
- Percentage coupon
- Fixed coupon
- Minimum order
- Maximum discount
- Expiry
- Usage limit

## Security Tests
- Client-side role tampering
- API authorization bypass
- IDOR/resource ownership
- XSS
- CSRF where applicable
- Injection
- Session fixation
- Rate limiting
- Sensitive export access

## Responsive Tests
- Desktop
- Tablet
- Mobile
- Navigation drawer
- Tables
- Modals
- Print

## Regression
Every release should retest authentication, order changes, product changes, inventory, exports and destructive operations.
