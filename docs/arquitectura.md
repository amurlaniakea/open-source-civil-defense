# OSCD — Architecture

## System Overview

```
                    ATTACKED DEVELOPER
                           |
                           | (private form / email)
                           v
              +---------------------------+
              |   PRIVATE INBOX          |
              |   (coordinators only)    |
              +---------------------------+
                           |
                           | (initial analysis)
                           v
              +---------------------------+
              |   CLASSIFICATION         |
              |   - Attack type          |
              |   - Severity             |
              |   - Impact estimate      |
              +---------------------------+
                     |           |
                  HIGH         LOW
                     |           |
                     v           v
              +-----------+  +-----------+
              | PRIVATE   |  | PUBLIC    |
              | 1:1 Help  |  | Anonymized|
              | until     |  | Case      |
              | resolved  |  | Study     |
              +-----------+  +-----------+
                     |           |
                     v           v
              +---------------------------+
              |   FORENSIC LIBRARY       |
              |   (public knowledge base)|
              +---------------------------+
```

## Components

### 1. Private Report Form

**Purpose:** Receive incident reports without exposing victims.

**Implementation:** Google Forms or Formspree (free, no backend needed).

**Fields:** See the form template in `docs/formulario-reporte.md`.

**Notifications:** Email alert to coordinator when a new report arrives.

### 2. Classification System

Each report is classified by:

- **Type:** Code injection, account takeover, phishing, supply chain, MCP poisoning, sabotage, other
- **Severity:** Critical (active, high-impact), High (contained, needs work), Low (resolved)
- **Impact:** >1000 stars, >1000 downloads/week, dependency of others, personal project

### 3. Kanban Board (Public)

**Location:** GitHub Projects v2

**Columns:**
- **Reported** — New case, pending analysis
- **Investigating** — Being analyzed by community
- **Mitigation in Progress** — Active help underway
- **Resolved** — Case closed with public documentation
- **Lessons Documented** — Full case study in forensic library

**Privacy:** The board shows only case numbers, attack types, and status. No sensitive data.

### 4. Forensic Library

**Location:** `casos/` directory in the repository.

**Structure per case:**
```
casos/NNN-short-name/
  README.md          # Summary
  detalle.md         # Technical analysis
  lecciones.md       # Lessons learned
  herramientas.md    # Tools used
  cronologia.md      # Timeline
```

### 5. Response Process

1. Report arrives via private form
2. Coordinator acknowledges receipt (within 72h for critical cases)
3. Initial assessment and classification
4. Private communication with reporter
5. Resolution (with community help if needed)
6. Request consent for anonymized documentation
7. Case study published in forensic library
8. Kanban card moved to "Lessons Documentated"

## Privacy Safeguards

- No sensitive data in the GitHub repository
- All case studies are anonymized before publication
- Consent required for any documentation
- Private reports are deleted after resolution
- No access to victim repositories without explicit permission

## Technology Stack

| Component | Tool | Cost |
|---|---|---|
| Repository | GitHub | Free |
| Kanban Board | GitHub Projects v2 | Free |
| Private Forms | Google Forms or Formspree | Free |
| Communication | Email + GitHub Issues | Free |
| Case Studies | Markdown files in repo | Free |
| Search | GitHub Search + Google indexing | Free |

## Scaling

OSCD is designed to scale without additional infrastructure:

- **More cases:** Just add more files to `casos/`
- **More contributors:** Anyone can submit PRs
- **More visibility:** Content is indexed by Google automatically
- **More languages:** Translations are welcome as additional files
