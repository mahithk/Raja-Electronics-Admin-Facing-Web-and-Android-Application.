# 15. Contributing

## Development Principles

- Keep business logic modular.
- Keep data access behind `Repo`.
- Keep authentication behind `Auth`.
- Log mutating operations through the audit layer.
- Avoid exposing credentials/secrets in source.
- Do not rely on UI checks for authorization.
- Validate destructive actions.
- Preserve responsive behavior.
- Test mobile and desktop layouts.
- Keep exports consistent with visible business data.

## Pull Request Checklist

- [ ] Feature requirement documented
- [ ] UI tested
- [ ] Mobile tested
- [ ] Permission behavior tested
- [ ] Error handling added
- [ ] Audit behavior reviewed
- [ ] Export behavior reviewed
- [ ] Security implications reviewed
- [ ] Documentation updated
