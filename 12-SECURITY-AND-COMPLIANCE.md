# 12. Security & Compliance

## Current Limitation

The source explicitly states that static HTML cannot provide trustworthy client-side authentication: credentials and role checks can be inspected or modified by a user.

## Required Production Controls

### Authentication
Use server-side authentication with secure password hashing.

### Authorization
Check every API request against the authenticated user's role and permission.

### Session
Use secure, short-lived sessions/tokens with appropriate expiration and revocation.

### Data Protection
- HTTPS
- Secure cookies where applicable
- Encryption at rest for sensitive systems
- Avoid unnecessary browser storage of sensitive information

### Input Security
Validate and sanitize all user-controlled data. Avoid unsafe HTML injection.

### Audit
Log sensitive actions:
- Login/logout
- Permission changes
- Order changes
- Product changes
- Inventory changes
- Review moderation
- Coupon changes
- Data deletion
- Exports

### Destructive Actions
Require explicit confirmation and preferably server-side approval/authorization for bulk deletion.

### Privacy
Customer exports should be restricted to authorized personnel and logged.

## Integration Caveats

The source identifies three admin-side-only areas until the storefront is changed:
1. Product catalogue stored as a JavaScript literal.
2. Cancelled order state stored separately from storefront tracking.
3. Review moderation state stored separately from storefront review display.
