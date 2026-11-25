# ai-enablement-portfolio

Practical AI harnesses, no-code compliance workflows, and plain-language enablement tools built for regulated financial teams.

---

## Included Frameworks & Policies

- **[AI Fluency Rubric](./ai-fluency-rubric.md)** - A four-level skill framework (Beginner to Steward) for measuring how teams actually use AI day-to-day, paired with a 90-day rollout and coaching guide.
- **[Plain-Language AI Policy (Broker-Dealer Edition)](./plain-language-ai-policy.md)** - A readable, enforceable usage policy covering approved tools, red/yellow/green data redaction tiers, FINRA Rule 2210 safeguards, output ownership, and incident reporting.

---

## Tools & Automations

- **[Anti-Slop & Compliance Auditor (n8n + Gemini)](https://github.com/WylieVanWenger/anti-slop-compliance-auditor)** - An automated pre-screening workflow built in n8n and Google Gemini that checks broker-dealer drafts against FINRA Rule 2210, strips AI clichés, and routes outputs into `FLAGGED FOR COMPLIANCE REVIEW` or `CLEARED FOR USE` reports using strict Boolean gating and fence-safe JSON parsing.

---

## Design Principles

- **Plain English over legalese:** Policies and rubrics only work if people actually read and apply them.
- **Human-in-the-loop by default:** AI assists with drafting, auditing, and organization; licensed humans own final compliance and business decisions.
- **Built for regulated environments:** Every framework accounts for data privacy, hallucination risk, and FINRA Rule 2210 standards from the start.
- **Repeatable systems over one-off prompts:** Focused on templates, checklists, and lightweight automations that save measurable time without adding bloat.
