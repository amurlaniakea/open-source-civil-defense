# How to Help in Cases

OSCD relies on community members to help respond to incident reports. This guide explains how you can contribute your skills.

## Who Can Help

Anyone with relevant skills can help:

- **Security researchers** — malware analysis, vulnerability assessment
- **Experienced developers** — code review, audit, emergency patches
- **DevOps/SRE** — infrastructure hardening, access control
- **Technical writers** — documentation, case study writing
- **Translators** — making content accessible in other languages

## How to Get Involved

### 1. Monitor Active Cases

Check the [Kanban Board](https://github.com/amurlaniakea/open-source-civil-defense/projects) for cases marked as "Investigating" or "Mitigation in Progress".

Cases with the `help-wanted` label are actively seeking assistance.

### 2. What You Can Do

**Code Audit:**
- Review the affected repository's code for malicious changes
- Check commit history for suspicious modifications
- Verify dependency integrity

**Malware Analysis:**
- Analyze suspicious files or packages in a sandbox
- Identify the attack vector and payload
- Document findings for the forensic library

**Emergency Response:**
- Help create clean forks of compromised repositories
- Assist with access control and token rotation
- Guide the victim through containment steps

**Documentation:**
- Write up case studies from resolved incidents
- Create guides for specific types of attacks
- Improve existing documentation

### 3. Rules for Helpers

- **Respect privacy** — never share details of active cases publicly
- **Don't access repositories** without explicit permission from the owner
- **Be constructive** — the victim is likely stressed and overwhelmed
- **Cite sources** — back up your analysis with evidence
- **Stay within your expertise** — if you're not sure, say so

## Becoming a Guardian

Guardians are trusted community members with elevated responsibilities. To become a Guardian:

1. Contribute meaningfully to at least 3 cases
2. Demonstrate expertise in security, audit, or incident response
3. Be invited by the Coordinator

Guardians can:
- Access private case details (under NDA-like informal agreement)
- Help classify and prioritize new cases
- Mentor new contributors
- Represent OSCD in external communications

## Code of Conduct

All helpers must follow the [Code of Conduct](../CODE_OF_CONDUCT.md). Violations, especially privacy violations, result in immediate removal.

## Recognition

Contributors are recognized in:
- The commit history of case studies
- The `CONTRIBUTORS.md` file (coming soon)
- Case study acknowledgments (with permission)
