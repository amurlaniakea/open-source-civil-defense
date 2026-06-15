# Catalog of Attack Types

This guide catalogs common types of attacks against open source developers and projects. Each entry includes detection methods, mitigation strategies, and references to documented cases.

## 1. Supply Chain Backdoor

**Description:** Malicious code is inserted into a dependency that is widely used. The backdoor activates under specific conditions.

**Notable cases:**
- [xz utils (2024)](../casos/001-xz-utils/) — Backdoor in SSH authentication
- [event-stream (2018)](../casos/002-event-stream/) — Malware targeting crypto wallets

**Detection:**
- Review recent commits for unusual changes
- Run `npm audit` or equivalent
- Check for obfuscated code or unusual network calls
- Use `diff` to compare versions

**Mitigation:**
- Pin dependencies to exact versions
- Review dependency update PRs carefully
- Use lock files (package-lock.json, yarn.lock, etc.)

## 2. Maintainer Account Compromise

**Description:** An attacker gains access to a maintainer's account (GitHub, npm, etc.) and publishes malicious versions.

**Notable cases:**
- [ua-parser-js (2021)](../casos/003-ua-parser-js/) — Account hijacked, crypto miner injected

**Detection:**
- Unexpected package versions
- New maintainer emails or commits
- Unusual login activity on your account

**Mitigation:**
- Enable 2FA on all accounts
- Use strong, unique passwords
- Review account activity regularly
- Use token-based auth instead of passwords

## 3. Phishing / Social Engineering

**Description:** Attackers impersonate trusted entities (GitHub, collaborators, security researchers) to trick maintainers into revealing credentials or running malicious code.

**Detection:**
- Unsolicited emails with urgent requests
- Fake security advisories
- Suspicious DMs from "collaborators"

**Mitigation:**
- Verify all communications through secondary channels
- Never click links in unsolicited emails
- Be skeptical of urgency

## 4. Dependency Confusion

**Description:** Attackers publish packages with the same name as private/internal packages to public registries. Build systems may pull the malicious public version instead of the intended private one.

**Detection:**
- Unexpected package sources in build logs
- Packages from public registry that should be internal

**Mitigation:**
- Use scoped packages (@yourorg/package)
- Configure registry priorities
- Use lockfiles with integrity hashes

## 5. Tool Description Poisoning (MCP)

**Description:** Malicious instructions are embedded in tool descriptions or metadata. When an AI agent reads the description, it executes the hidden instructions.

**Notable cases:**
- [MCP Poisoning (2025-2026)](../casos/004-mcp-poisoning/) — Tool descriptions used to inject malicious instructions

**Detection:**
- Review tool descriptions for unusual instructions
- Check for base64-encoded content in descriptions
- Verify tool sources before installation

**Mitigation:**
- Audit tool descriptions before use
- Use tools from verified sources
- Run tools in sandboxed environments

## 6. Sabotage by Former Maintainer

**Description:** A maintainer (current or former) intentionally introduces breaking changes, backdoors, or deletes code.

**Notable cases:**
- [colors.js / faker.js (2022)](https://github.com/Marak/colors.js/issues/254) — Maintainer sabotaged own packages

**Detection:**
- Sudden breaking changes without explanation
- Maintainer expressing frustration publicly
- Unusual commit patterns

**Mitigation:**
- Have multiple maintainers for critical projects
- Use governance models that prevent single points of failure
- Monitor maintainer health and community sentiment

## 7. Typosquatting

**Description:** Attackers publish packages with names similar to popular packages (e.g., `rquests` instead of `requests`). Developers may accidentally install the wrong package.

**Detection:**
- Review installed packages for name similarities
- Check download counts (typosquats usually have very few)

**Mitigation:**
- Double-check package names before installation
- Use lockfiles
- Verify package metadata and author

## 8. Starjacking

**Description:** Attackers transfer a legitimate project to a new maintainer (with the original maintainer's consent, often obtained through social engineering) and then inject malware.

**Detection:**
- Project transferred to unknown maintainer
- Sudden changes in project direction

**Mitigation:**
- Monitor project transfers
- Verify new maintainer identity
- Review all changes after transfer

---

*This catalog is continuously updated as new attack types emerge. If you encounter a new type of attack, please document it using our [Case Study Template](../.github/ISSUE_TEMPLATE/caso-de-estudio.md).*
