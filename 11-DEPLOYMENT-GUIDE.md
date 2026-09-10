# 11. Deployment Guide

## Local Development

Place the admin HTML in the project directory and run:

```bash
python -m http.server 8000
```

Open the admin page through HTTP.

## Same-Origin Development

If the admin console is intended to read the customer site's browser storage, serve both files from the same origin.

Example:

```text
http://localhost:8000/index1_v57.html
http://localhost:8000/admin_v62(1).html
```

## Production Recommendation

Do not deploy the static client-side credential model as the final security architecture.

Recommended:

```text
Nginx / CDN
     |
Spring Boot API
     |
Database
```

The frontend should communicate with authenticated HTTPS APIs.

## Deployment Checklist

- [ ] HTTPS enabled
- [ ] Backend authentication enabled
- [ ] Server-side RBAC enabled
- [ ] Database configured
- [ ] Secrets stored outside source
- [ ] CORS restricted
- [ ] Security headers configured
- [ ] Audit logging enabled
- [ ] Backups configured
- [ ] Monitoring configured
- [ ] Error handling verified
- [ ] Export authorization verified
