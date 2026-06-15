# Frequently Asked Questions

## General

### What is OSCD?

Open Source Civil Defense (OSCD) is a community hub for independent developers and open source maintainers who have been attacked. We provide a private reporting system, coordinate community help, and document resolved cases as learning resources.

### Is OSCD a professional service?

**No.** OSCD is a voluntary community effort. We are not a company, not a professional incident response team, and not a substitute for GitHub Security or corporate security teams. All support is provided "as is" without warranties.

### Who runs OSCD?

OSCD is maintained by a community of volunteers. The project was founded by [Sil](https://github.com/amurlaniakea) and is governed by the rules in [GOVERNANCE.md](./GOVERNANCE.md).

## Reporting

### How do I report an attack?

Use our **private report form** (link coming soon). Do NOT open a GitHub Issue — Issues are public and would alert the attacker.

### What information do I need to provide?

At minimum: your contact information and a description of what happened. Optional: repository URL, impact assessment, evidence links.

### Is my report confidential?

Yes. Reports are only seen by trusted community members. Your case will NOT be made public without your explicit consent.

### What if the attack is still active?

Mark your report as "URGENT" in the form. We prioritize active attacks. In the meantime:
1. Revoke compromised tokens
2. Enable 2FA if not already active
3. Do NOT delete evidence

### Can I report anonymously?

Yes. You can provide only an alias and a secure email (e.g., ProtonMail). However, anonymous reports may be harder to verify and assist.

## Helping

### How can I help?

- Review active cases on our Kanban board
- Contribute code audits, malware analysis, or documentation
- Share your expertise in discussions
- Help translate content

### How do I become a Guardian?

Guardians are invited by the Coordinator after demonstrating expertise and commitment. There is no formal application process — it's based on contribution quality and trust.

### Can I help without technical skills?

Yes! We need:
- Technical writers (documentation, guides)
- Translators (making content accessible in other languages)
- Community moderators
- Social media / outreach helpers

## Cases

### Where can I find documented cases?

In the [casos/](./casos/) directory. Each case includes a detailed analysis, timeline, and lessons learned.

### Can I submit a case study?

Yes! Use the [Case Study Template](./.github/ISSUE_TEMPLATE/caso-de-estudio.md). Cases must be from public sources or have explicit consent from the affected party.

### Are real cases anonymized?

Yes. All identifying information is removed before publication. We document the attack type, techniques, and lessons — not the victim's identity.

## Legal

### Is OSCD legal advice?

**No.** OSCD does not provide legal advice. If you need legal counsel, please consult a qualified attorney in your jurisdiction.

### Can I be held liable for advice I give through OSCD?

We recommend all contributors include a disclaimer that their advice is personal opinion, not professional guidance. OSCD's [SECURITY.md](./SECURITY.md) provides more details.

### What if someone uses OSCD to harm others?

This violates our [Code of Conduct](./CODE_OF_CONDUCT.md) and will result in immediate removal from the project.

## Technical

### What technologies does OSCD use?

- **GitHub** for the repository, Kanban board, and discussions
- **Google Forms or Formspree** for private incident reports
- **Markdown** for all documentation
- **GitHub Actions** for basic automation

### Does OSCD use AI agents?

OSCD coordinates with the Hermes security ecosystem, which includes AI-powered security tools. However, OSCD itself is primarily a documentation and coordination platform.

### How can I verify OSCD's legitimacy?

- Check the GitHub repository history
- Review the open governance process
- All case studies cite public sources
- The project is transparent about its limitations

---

*If your question is not answered here, please open an Issue with the `question` label.*
