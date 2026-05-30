---
name: sde-resume-content
description: >
  Write, rewrite, and quantify resume bullet content for Software Development Engineers (SDEs).
  Trigger this skill whenever a user wants to improve, add, or quantify resume bullets for a
  tech/SDE role — including requests like "make this bullet better", "add metrics", "quantify my
  experience", "write a bullet for X", "I don't have numbers", or "update my resume". Also trigger
  when the user pastes raw LaTeX resume content and asks for improvements. Always use this skill
  for any SDE resume writing task, even if the request sounds simple.
---

# SDE Resume Content Skill

Write, quantify, and return resume bullet content for Software Engineers in their existing LaTeX
template. Focus is purely on **content quality** — wording, metrics, impact. Never restructure,
reformat, or change the user's template.

---

## Bullet Anatomy (SDE)

Every strong SDE bullet follows this structure:

```
[Strong Verb] + [What you built/did] + [Scale/Scope] + [Outcome/Impact]
```

**Examples:**
```
Architected a real-time data pipeline processing 2M events/day, reducing P99 latency by 60%
Refactored monolithic auth service into 4 microservices, cutting deploy time from 45 min → 8 min
Led migration of 3 legacy MySQL databases to DynamoDB, eliminating $40K/yr in licensing costs
```

---

## SDE Metric Cheatsheet

Pick the metrics that apply. You don't need all — 2–3 per bullet is ideal.

| Category | What to Measure |
|---|---|
| **Scale** | users, requests/sec, events/day, records, API calls |
| **Performance** | latency (P50/P95/P99), throughput, uptime (SLA %), response time |
| **Efficiency** | build/deploy time, CI runtime, query time, manual hours saved |
| **Cost** | infra savings ($), cost per request, compute reduction (%) |
| **Quality** | test coverage (%), bug reduction (%), incident rate, MTTR |
| **Velocity** | release frequency, sprint throughput, PR cycle time |
| **Ownership** | team size, services owned, engineers mentored, codebase size (LOC, modules) |

---

## Finding Your Numbers (When You Have None)

Use these questions to surface hidden metrics:

**Scale:** How many users/customers touched this? Daily traffic? Records in the DB?

**Before/After:** What was slow, expensive, or broken before? What is it now?

**Frequency:** How often did something happen? (deploys/week × time → annual hours)

**Your slice:** What % of the codebase/system did you own?

**Team context:** How many engineers total? How many did you mentor/lead?

### Estimation Rules
- Estimate **conservatively** — use `~`, `+`, or ranges: `75+`, `40–60%`, `~$20K`
- You must be able to defend every number in an interview
- Never fabricate; always round down, not up

---

## Strong SDE Verbs

| Category | Verbs |
|---|---|
| Build | Architected, Engineered, Developed, Implemented, Designed, Built |
| Improve | Optimized, Refactored, Reduced, Accelerated, Streamlined, Migrated |
| Lead | Led, Owned, Spearheaded, Drove, Mentored, Coordinated |
| Operate | Deployed, Monitored, Automated, Maintained, Triaged, Resolved |
| Collaborate | Partnered, Collaborated, Contributed, Reviewed, Defined |

Avoid weak openers: *Helped, Assisted, Worked on, Participated in, Was responsible for*

---

## Template Policy — Read This First

**Never change the user's LaTeX template, structure, or formatting commands.** The user owns their template. Your job is content only.

### Rules
- Mirror whatever commands the user is already using (`\resumeItem`, `\item`, `\cventry`, etc.)
- Do not introduce new environments, packages, or macros
- Do not reorder sections, rename headings, or alter spacing commands
- Do not add or remove `\resumeItemListStart` / `\resumeItemListEnd` or equivalent wrappers — only touch what's inside them

### Template Validation (one-time, silent)

If the user pastes their full template or preamble, do a quick scan for these common issues. Fix silently only if they're clearly broken — otherwise leave as-is:

| Issue | Fix |
|---|---|
| Unescaped `%`, `$`, `&` inside bullet text | Escape: `\%`, `\$`, `\&` |
| Missing period at end of `\resumeItem{}` | Add `.` |
| Unclosed braces in a bullet | Close the brace |

Do **not** flag stylistic preferences (font choices, spacing, color) as issues. If unsure whether something is intentional, leave it alone.

### Output format

Always return bullets using the exact command the user uses. If they use `\resumeItem{}`, use that. If they use `\item`, use that. When in doubt, match what's in the pasted code.

```latex
\resumeItem{Strong verb + what + scale + outcome.}
```

---

## Workflow

### Case 1: User pastes existing bullets to improve

1. Identify bullets that lack numbers, use weak verbs, or are vague
2. For each weak bullet, ask **one targeted question** to surface a metric (don't ask 5 at once)
3. Rewrite and return the full LaTeX block

### Case 2: User describes experience without a bullet

1. Ask: *"What did you build, and what was the measurable result?"*
2. Draft a bullet using the anatomy above
3. Return in LaTeX

### Case 3: User says "I have no metrics"

Acknowledge, then walk through the metric cheatsheet categories one at a time. Most SDEs have:
- Traffic/scale numbers (even rough ones)
- Latency or uptime improvements
- Time saved (manual process automated)
- Cost reduction (infra rightsizing, query optimization)

---

## Output Template

Return a clear before/after block, then the LaTeX:

```
### Original:
"Worked on improving database performance"

### Questions asked:
- What DB? → PostgreSQL
- What was slow? → A report query, ~12s
- After optimization? → ~800ms
- Used by how many? → ~200 internal users

### Quantified Bullet:
Optimized 3 critical PostgreSQL queries for an internal analytics dashboard used by 200+ users,
reducing average query time from 12s → 800ms (93% improvement).

### LaTeX:
\resumeItem{Optimized 3 critical PostgreSQL queries for an internal analytics dashboard used by 200+ users, reducing average query time from 12s to 800ms (93\% improvement).}
```

---

## Quality Checklist

Before returning any bullet:
- ✅ Starts with a strong verb (not "Helped", "Worked on")
- ✅ Contains at least 1 concrete number or metric
- ✅ Metric is defensible and conservative
- ✅ Outcome is stated (not just activity)
- ✅ 1–2 lines max, no fluff
- ✅ Uses the **same LaTeX command** the user already uses
- ✅ Special chars escaped: `%` → `\%`, `$` → `\$`, `&` → `\&`
- ✅ Ends with a period inside the bullet command
- ✅ Template structure left completely unchanged

---

## LaTeX Escaping Reference

| Character | Escape |
|---|---|
| `%` | `\%` |
| `$` | `\$` |
| `&` | `\&` |
| `_` | `\_` (only outside math mode) |
| `#` | `\#` |
| `~` | `\textasciitilde{}` or just write "approximately" |
| `→` | `$\rightarrow$` or use `-->` in plain text |