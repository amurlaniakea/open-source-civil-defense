# How to Report an Incident

If you are a developer or open source maintainer who has been attacked, this guide explains how to report it safely and get help from the OSCD community.

## Before You Report

### Assess the Situation

1. **Is the attack still active?** If yes, prioritize containment first.
2. **Is your account compromised?** Secure it immediately (change passwords, revoke tokens, enable 2FA).
3. **Is malicious code already published?** If possible, do NOT remove it yet — it serves as evidence.

### Gather Information

Before reporting, try to collect:

- When you first noticed the attack
- How you detected it
- What was affected (code, account, packages, users)
- Any evidence (screenshots, commit hashes, log entries)

## How to Report

**Use our private report form:** [OSCD Incident Report Form](https://forms.gle/REPLACE_WITH_FORM_LINK)

> **IMPORTANT:** Do NOT open a GitHub Issue to report an attack. GitHub Issues are public and would alert the attacker to the fact that you are aware of the attack.

The form will ask for:

1. **Your contact information** (name/alias + email)
2. **Repository details** (optional — only if you are comfortable sharing)
3. **Attack description** (what happened, when, how you detected it)
4. **Current status** (active, contained, under investigation)
5. **Impact assessment** (users affected, projects depending on yours)
6. **Evidence** (links to commits, PRs, suspicious messages)
7. **Help requested** (what kind of assistance you need)
8. **Consent** (acknowledgment of OSCD's terms)

## What Happens Next

1. **Acknowledgment** — You will receive an email acknowledgment within 72 hours (sooner for critical cases)
2. **Initial Assessment** — The case is classified by severity and type
3. **Private Communication** — You will be contacted privately to discuss the incident
4. **Resolution** — The community works with you to resolve the issue
5. **Documentation** — With your consent, the case is documented anonymously for the community

## If the Attack is Critical

If the attack is:
- Active and ongoing
- Affecting thousands of users
- A supply chain compromise with potential for mass infection

Mark your report as **URGENT** in the form. This triggers priority handling.

## Tips for Effective Reporting

- **Be specific** about dates, versions, and affected components
- **Preserve evidence** — don't delete logs, commits, or messages
- **Don't blame yourself** — attacks happen to everyone, even security experts
- **Be patient** — the community is volunteer-based and will respond as quickly as possible

## What NOT to Do

- **Don't** open a public GitHub Issue about an active attack
- **Don't** share credentials, tokens, or passwords in the report form
- **Don't** attempt to retaliate against the attacker
- **Don't** delete evidence before documenting it
- **Don't** publicly disclose the attack until it is resolved

## After Resolution

Once the incident is resolved, you will be asked for permission to document the case. This is entirely optional. If you consent:

- All identifying information will be removed
- The case will be published in the forensic library
- Your contribution helps other developers avoid the same fate
