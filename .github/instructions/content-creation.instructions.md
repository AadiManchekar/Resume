---
description: 'Guidelines for content creation'
applyTo: '**/*.tex'
---

# Resume Content Writing Guidelines

You are editing a LaTeX resume. Your job is to write copy that reads like a real person wrote it, not a language model. Follow these rules precisely.

## Voice and Tone

Write the way a confident professional would speak in an interview: direct, specific, and grounded. Avoid corporate filler. Every word should earn its place. The reader should feel like they are reading about a real person with real work behind them, not a curated AI summary.

## What to Avoid

**AI-specific phrasing — never use:**
- Transitional openers: "Additionally", "Furthermore", "Moreover", "In addition", "Notably", "Importantly", "Ultimately", "Overall", "To that end"
- Self-congratulatory starters: "Passionate about", "Driven by", "Dedicated to", "Committed to", "Leveraged", "Spearheaded", "Championed", "Orchestrated"
- Vague intensifiers: "highly", "robust", "cutting-edge", "innovative", "dynamic", "synergistic", "impactful", "scalable" (unless technically precise)
- Hollow closers: "resulting in success", "driving growth", "enabling transformation"
- Buzzword stacking: avoid cramming three or more industry terms into one bullet

**Typographical habits — never use:**
- Em dashes ( — ) or en dashes ( – ) as stylistic separators
- Semicolons to chain clauses in bullets
- Curly or smart quotes ( " " ' ' ) — LaTeX handles quoting natively; defer to its conventions
- Bullet points that start with the same verb two lines in a row

## What to Do Instead

**Bullet structure:** Start with a strong, varied action verb in past tense. Lead with what you did, then what it produced. Keep bullets to one idea. If you cannot cut it to two lines in LaTeX, split or cut.

**Numbers and specificity:** Prefer concrete over vague. "Reduced build time from 14 minutes to 3" beats "significantly improved build performance". If numbers are unavailable, describe scope: team size, frequency, volume, or geography.

**Sentence rhythm:** Vary sentence length. Short punchy bullets work. Slightly longer ones that carry technical context also work. What does not work is every bullet clocking in at the same 12-word length, which is a dead giveaway.

**Word choice:** Prefer plain, precise words. "Built" over "architected". "Led" over "spearheaded". "Reduced" over "optimized away". "Helped" is fine when accurate. Jargon is acceptable when it is the correct technical term, not when it is decoration.

## LaTeX-Specific Rules

- Do not introduce formatting commands not already present in the file's preamble
- Match the existing `\resumeItem`, `\resumeSubheading`, or equivalent macros already defined
- Preserve all brace structures, environments, and indentation patterns
- Use straight quotes ( " ) in source if quoting is necessary; do not convert to LaTeX quote pairs unless the style already does so
- Do not add comments unless asked

## Section-Specific Guidance

**Experience bullets:** Past tense. Action verb first. One outcome per bullet. Max four bullets per role unless the role warrants more.

**Skills section:** List only; no sentences. Group by category if the template supports it. Do not editorialize ("proficient in", "familiar with" — just list the skill).

**Summary or objective (if present):** Two to three sentences maximum. Written in third person or headless first person (no "I"). States what the person does and what they bring, without adjectives that the reader cannot verify.

**Education:** Factual only. Dates, institution, degree, relevant honors. No narrative.

## Final Check Before Outputting

Read the content aloud in your head. If it sounds like a press release, rewrite it. If it sounds like a person explaining their job to someone at a dinner party, it is ready.