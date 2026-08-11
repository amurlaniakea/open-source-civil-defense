# Open Source Civil Defense (OSCD)

> "The software of the world is built on the shoulders of independent developers. It is time to protect them."

---

> **DISCLAIMER — READ BEFORE USING THIS PROJECT**
>
> **This is a voluntary community effort of mutual aid. We are not legal advisors, we are not a professional incident response (IR) company, and we are not a substitute for GitHub Security or any corporate security team. All support and advice is provided "AS IS", without warranties of any kind. The use of suggested tools is at the sole responsibility of the user. By submitting a report through our private form, you acknowledge these conditions and consent to your case being documented anonymously for the benefit of the community.**

---

## What is OSCD

Open Source Civil Defense is a community space for independent developers and open source maintainers who are suffering (or have suffered) an attack on their code, account, or infrastructure.

We are not a company. We are not a professional service. We are a community of developers who take care of each other.

## The Problem

Most of the world's software depends on small libraries maintained by one or two people. When an attacker compromises an independent maintainer's repository, they can infect millions of installations within hours.

Recent attacks prove this:

- **xz utils (2024):** Backdoor inserted over 2+ years. Nearly compromised all Linux.
- **event-stream (2018):** Maintainer compromised, malware to steal bitcoins. 2M+ downloads/week.
- **ua-parser-js (2021):** Account hijacked, crypto-mining malware. 7M+ downloads/week.
- **MCP tool poisoning (2025-2026):** Poisoning of MCP tool descriptions to inject malicious instructions.

When an independent developer is attacked, they are usually alone. They don't have a security team. They don't have a lawyer. They don't have anyone to call.

**Until now.**

## What We Do

### 1. Receive and Classify Alerts

When a developer reports an attack, we use a structured form to understand:

- Type of attack (code injection, account takeover, phishing, etc.)
- Current status (active, contained, under investigation)
- Estimated impact (affected users, dependent projects)

### 2. Coordinate Community Response

Cases are published on a public Kanban board with priority levels:

- **CRITICAL:** Active attack on high-impact project. Requires immediate action.
- **HIGH:** Attack contained but needs cleanup or audit.
- **LOW:** Case resolved, lessons learned.

Any developer can join a case to help with:

- Code audit
- Emergency forks
- Malware analysis
- Incident documentation

### 3. Facilitate Reporting to Platforms

When a case is serious, we help prepare structured reports for:

- GitHub Security (via CVD)
- OpenSSF Malicious Packages DB
- Package manager security teams (npm, PyPI, crates.io, etc.)

### 4. Share Knowledge

Every resolved case becomes public documentation:

- How the attack was detected
- How it was contained
- How to prevent it in the future

## What OSCD is NOT

- **NOT** a professional incident response service
- **NOT** legal advice
- **NOT** a substitute for GitHub Security or any corporate security team
- **NOT** guaranteed 24/7 real-time response
- **NOT** responsible for actions taken based on community advice

All support is voluntary and offered "as is" without warranties.

## How to Get Help

**Use our private report form:** [OSCD Incident Report Form](https://amurlaniakea.github.io/open-source-civil-defense/form.html)
2. A community member will respond when they can
3. We work with you privately until the issue is resolved
4. With your consent, we document the case (anonymized) for the community

**If the attack is active and urgent**, mark your report as "URGENT" in the form.

> **IMPORTANT:** Do NOT open a GitHub Issue to report an active attack. Issues are public and would alert the attacker. Use the private form above.

## How to Help

- Review open cases on our [Kanban Board](https://github.com/amurlaniakea/open-source-civil-defense/projects)
- If you have experience in security, code audit, or incident response, consider becoming a Guardian
- Share reports (respecting victim privacy) for visibility
- Contribute documentation, guides, and tools

## Forensic Library

Our growing database of documented incidents:

| Case | Type | Status |
|------|------|--------|
| [001-xz-utils](./casos/001-xz-utils/) | Supply chain backdoor | Documented |
| [002-event-stream](./casos/002-event-stream/) | Maintainer compromise | Documented |
| [003-ua-parser-js](./casos/003-ua-parser-js/) | Account hijack + crypto miner | Documented |
| [004-mcp-poisoning](./casos/004-mcp-poisoning/) | Tool description poisoning | Documented |

## Technological Ecosystem

OSCD is coordinated with the Hermes security ecosystem:

- **MCP Core Defense:** Security scanning for MCP repositories
- **Agent Fixer Stage:** Detection and correction of malicious outputs
- [Hermes-Crew Hybrid](https://github.com/amurlaniakea/hermes-crew-hybrid): Security agent orchestration

These tools are open source and can be used locally by any developer to audit their own code.

## Governance

See [GOVERNANCE.md](./GOVERNANCE.md) for project governance, roles, and decision-making processes.

## Contributing

See [CONTRIBUTING.md](./CONTRIBUTING.md) for how to contribute to the project.

## Code of Conduct

See [CODE_OF_CONDUCT.md](./CODE_OF_CONDUCT.md) for community standards.

## Security

See [SECURITY.md](./SECURITY.md) for how to report vulnerabilities in OSCD itself.

## License

This project is licensed under the **GNU Affero General Public License v3.0 or later (AGPL-3.0-or-later)**. The knowledge to defend software creators must remain free.

## Contact

- **Repository:** [github.com/amurlaniakea/open-source-civil-defense](https://github.com/amurlaniakea/open-source-civil-defense)
- **Report an incident:** [Private Form](https://amurlaniakea.github.io/open-source-civil-defense/form.html)
- **Contact:** Sil-MagoPredator-Fenix (Pedro Sordo Martínez) — amurlaniakea@gmail.com
- **License:** AGPL-3.0-or-later
---

*OSCD is a community project. It is not perfect. But it is necessary.*
