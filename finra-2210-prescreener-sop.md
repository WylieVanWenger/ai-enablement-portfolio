# FINRA Rule 2210 Pre-Screener SOP & Prompt Harness

This SOP walks through how to pre-screen client emails, investor updates, and marketing drafts for FINRA Rule 2210 compliance issues and AI clichés before sending them to a licensed principal or Compliance officer.

**Scope Boundary:** This pre-screener is a first-pass quality gate. It catches obvious red flags and cleans up sloppy prose so Compliance spends less time bouncing drafts back. It never replaces human judgment, primary-source verification, or registered principal approval.

---

## Step 1: Classify the Communication

Under FINRA Rule 2210, how a draft is supervised depends on who receives it. Identify the category before you screen or route it:

| Category | Audience | Pre-Use Principal Approval |
| :--- | :--- | :--- |
| **Correspondence** | 25 or fewer retail investors within any rolling 30-calendar-day period (e.g., 1:1 client emails). | Not required pre-use; subject to firm supervisory review under Rule 3110. |
| **Retail Communication** | More than 25 retail investors within any rolling 30-calendar-day period (e.g., newsletters, websites, social media, mass emails). | Required before first use (unless a specific Rule 2210 exception applies). Certain products also require FINRA filing. |
| **Institutional Communication** | Institutional investors only (e.g., banks, insurance companies, qualified plans with 100+ participants, entities with $50M+ in assets). | Not required pre-use; subject to written supervisory procedures. |

**The Forwarding Rule:** Never treat a draft as an Institutional Communication if you have reason to believe it (or an excerpt of it) will be forwarded to a retail investor. If it can reach retail eyes, screen and approve it as retail.

---

## Step 2: Redact Before You Paste

Before running any draft through an AI tool, follow the **Red / Yellow / Green** rules in our [Plain-Language AI Policy](./plain-language-ai-policy.md):

- Strip out all client PII (names paired with account numbers, SSNs, addresses, or tax IDs).
- Remove Material Non-Public Information (MNPI) and confidential deal terms.
- Replace specific client names and exact dollar figures with generic placeholders (e.g., `[CLIENT_NAME]`, `[DOLLAR_AMOUNT]`).
- Use company-approved enterprise AI tools only. Never paste work drafts into personal or free accounts.

---

## Step 3: Run the Pre-Screener

Use **Option A** for repeatable team intake, or **Option B** for a quick manual check inside an approved enterprise LLM.

### Option A: Automated Workflow (Recommended)
Submit the redacted draft through the **[Anti-Slop & Compliance Auditor (n8n + Gemini)](https://github.com/WylieVanWenger/anti-slop-compliance-auditor)**. The workflow evaluates the text against FINRA Rule 2210 and anti-slop rules, then routes the output into a `FLAGGED FOR COMPLIANCE REVIEW` or `CLEARED FOR USE` report.

### Option B: Manual Prompt Harness
Paste the prompt below into an approved enterprise AI tool, then insert your communication category and redacted draft at the bottom.

```text
You are a strict broker-dealer compliance pre-screener reviewing a draft communication under FINRA Rule 2210 standards and plain-English writing rules. You do not give final legal approval; your job is to flag risks, identify missing balance, and remove AI filler so a human reviewer can work faster.

Audit the draft below for these five issues:
1. Promissory, exaggerated, or unwarranted language (e.g., "guaranteed," "risk-free," "proven to outperform," "will maximize").
2. One-sided claims that highlight benefits without stating material risks, costs, or limitations.
3. Unverified statistics, tax/legal claims, or investment comparisons that lack a cited primary source or omit material differences.
4. Performance projections or targeted returns (flag any forward-looking return language unless the draft explicitly notes it is authorized under firm Rule 2210 projection procedures and includes required disclosures).
5. AI slop and clichés (e.g., "delve," "tapestry," "fast-paced landscape," "game-changing," "in today's dynamic market," or generic filler).

Output your audit in this exact structure:
- **Status:** FLAGGED FOR COMPLIANCE REVIEW or CLEARED FOR HUMAN REVIEW
- **FINRA Rule 2210 Red Flags:** Bullet list quoting the exact risky phrase, naming the rule issue, and explaining why it fails. Write "None detected" if clean.
- **Verification Checklist:** List every statistic, fee, date, or product claim the human author must verify against a primary source before sending.
- **Slop Removed:** List any clichés or filler phrases cut from the draft.
- **Suggested Clean Rewrite:** Provide a fair, balanced, plain-English rewrite that preserves the author's intent without adding new facts or unsupported claims.

Communication Category: [Correspondence / Retail Communication / Institutional Communication]
Draft Text:
"""
[PASTE REDACTED DRAFT HERE]
"""
