# Basic Security for Maintainers

Essential security practices for open source maintainers. This is not a comprehensive security guide — it's a starting point.

## Account Security

### Enable Two-Factor Authentication (2FA)

**GitHub:**
1. Go to Settings > Password and authentication
2. Enable 2FA with an authenticator app (not SMS)
3. Save recovery codes in a secure location

**npm / PyPI / crates.io:**
- Enable 2FA on all package registries you use

### Use Strong, Unique Passwords

- Use a password manager (Bitwarden, 1Password, KeePass)
- Never reuse passwords across services
- Minimum 16 characters

### Review Account Activity

- Check GitHub Security Log regularly
- Review authorized applications and tokens
- Revoke unused tokens and sessions

## Repository Security

### Protect Your Main Branch

1. Go to Settings > Branches
2. Enable branch protection rules:
   - Require pull request reviews
   - Require status checks
   - Include administrators
   - No force pushes

### Review Dependencies

- Run `npm audit` / `pip audit` / `cargo audit` regularly
- Enable Dependabot or Renovate for automatic updates
- Review dependency update PRs carefully

### Use Signed Commits

```bash
# Configure GPG signing
git config --global commit.gpgsign true
git config --global user.signingkey YOUR_KEY_ID
```

### Limit Token Scope

- Use fine-grained tokens instead of classic tokens
- Grant minimum necessary permissions
- Rotate tokens regularly

## Release Security

### Verify Before Publishing

- Review all changes in the release
- Run tests and security scans
- Check for unexpected files in the package

### Use Provenance

- npm: `npm publish --provenance`
- PyPI: Use trusted publishing (OIDC)
- This proves where the package was built

## Incident Response Basics

If you suspect a compromise:

1. **Don't panic** — assess the situation calmly
2. **Contain** — revoke compromised tokens, disable affected packages
3. **Document** — save logs, commit hashes, timestamps
4. **Report** — use the [OSCD private form](https://forms.gle/REPLACE_WITH_FORM_LINK) or contact GitHub Security
5. **Communicate** — inform your users transparently after containment

## Resources

- [GitHub Security Best Practices](https://docs.github.com/en/code-security)
- [OpenSSF Best Practices](https://openssf.org/projects/best-practices/)
- [npm Security](https://docs.npmjs.com/getting-started/)
- [OSCD Attack Types Catalog](./tipos-de-ataque.md)
