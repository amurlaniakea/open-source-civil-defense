# Forensic Library — Index

This directory contains documented case studies of security incidents affecting open source projects. Each case is anonymized and serves as a learning resource for the community.

## Cases

| # | Name | Type | Year | Status |
|---|------|------|------|--------|
| 001 | [xz utils](./001-xz-utils/) | Supply chain backdoor | 2024 | Documented |
| 002 | [event-stream](./002-event-stream/) | Maintainer compromise | 2018 | Documented |
| 003 | [ua-parser-js](./003-ua-parser-js/) | Account hijack + crypto miner | 2021 | Documented |
| 004 | [MCP Poisoning](./004-mcp-poisoning/) | Tool description poisoning | 2025-2026 | Documented |

## How to Contribute a Case

See our [Case Study Template](../.github/ISSUE_TEMPLATE/caso-de-estudio.md) for the format.

Requirements:
- Must be from a **public source** or have **explicit consent**
- All identifying information must be **removed**
- Must include: timeline, technical details, impact, resolution, lessons learned

## Categories

- **Supply chain backdoor:** Malicious code inserted into widely-used dependencies
- **Maintainer compromise:** Attacker gains control of maintainer account
- **Phishing / social engineering:** Attacker tricks maintainer into compromising actions
- **Dependency confusion:** Attacker publishes packages with names matching private packages
- **Tool description poisoning:** Malicious instructions hidden in tool metadata
- **Sabotage:** Intentional damage by current or former maintainer
- **Typosquatting:** Packages with names similar to popular packages
- **Starjacking:** Project transferred to attacker-controlled account
