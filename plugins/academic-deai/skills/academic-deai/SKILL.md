---
name: academic-deai
description: "Detect AI-like phrasing and evaluate journal quality in English economics manuscripts against top-5 journal standards (AER, QJE, Econometrica, JPE, REStud). Use when user says 'deai', 'AI traces', 'remove AI tone', 'style scrub', 'economics writing check', or 'check AI-like phrasing'."
---

# Academic De-AI for Economics Writing

**Core mission: produce journal-quality economics prose free of AI traces.**

When the user provides a file path, read the file first. This skill uses two reference files in the same directory:
- `ai-detection.md` — lexical markers, template sentences, syntax rules, density thresholds
- `journal-quality.md` — top-5 journal conventions, section structure, prose standards, positive/negative markers

Read both reference files before evaluating any text.

---

## 1. Primary Objective

The goal is not merely to remove AI-like phrasing. The goal is to produce prose that reads like a published article in a top-5 economics journal.

Every sentence is evaluated on two axes:
1. **AI contamination** — does it contain templated, inflated, or mechanically balanced phrasing?
2. **Journal quality** — does it meet the prose, structure, and formatting standards of AER/QJE/Econometrica/JPE/REStud?

A sentence fails if it scores high on either axis. Low AI markers do not excuse flat, note-like, or unacademic writing. Clean prose that sounds like a memo, referee report, or slide deck still needs revision.

---

## 2. Distinguish Three Cases

When reviewing a sentence, always classify it as one of:

**Case 1: AI-like phrasing (flag and revise)**
Templated, over-smoothed, over-complete, rhetorically inflated, or mechanically balanced writing. Uses high-risk verbs, adjectives, or sentence structures listed in `ai-detection.md`.

**Case 2: Acceptable journal prose (preserve)**
Standard top-5 journal prose that uses moderate abstraction, careful interpretation, or contribution framing tied to a concrete object. See the standard phrases whitelist in `journal-quality.md`.

**Case 3: Over-corrected flat prose (bad revision — avoid)**
Writing that removes AI markers by stripping away legitimate academic texture, leaving the sentence sounding like a memo, internal note, or slide bullet. This is a revision failure.

---

## 3. Preserve These Academic Features

Do not automatically remove the following if they are concrete and disciplined:

- moderate abstraction tied to a specific variable, institution, or model object
- mechanism language tied to variables, coefficients, policies, or sectors
- restrained interpretation (one sentence of interpretation after a result is standard)
- contribution framing that is enumerated and anchored to specific prior papers
- passive constructions in methods: "Standard errors are clustered at the state level."
- first-person plural "we" as default voice (standard in all top-5 journals)

Examples of acceptable academic prose (do NOT flag):
- "We find that..." / "Our results suggest that..."
- "The estimates are consistent with..." / "This pattern is consistent with..."
- "A likely mechanism is..." / "One possible mechanism is..."
- "This paper studies..." / "This paper makes three contributions."
- "Several limitations should be acknowledged."
- "Column (1) reports results from..."

See the full whitelist of standard phrases in `journal-quality.md`.

---

## 4. "This paper" Rule

Do not ban "This paper" outright. It is standard in all top-5 journals.

Acceptable:
- one or two information-rich uses in the introduction
- contribution framing: "This paper makes three contributions."
- reference to the paper's specific contribution in discussion

Flag only when:
- repeated frequently (>2 per 1,000 words)
- used at the start of many consecutive paragraphs
- followed by generic contribution language without specifics
- used instead of stating a concrete result or mechanism

---

## 5. Passive Voice Rule

Do not flag passive voice mechanically. Passive is standard in top-5 methods sections.

Acceptable:
- "Standard errors are clustered at the state level."
- "The estimates are reported in Table 2."
- "The sample is restricted to..."
- "The results should be interpreted with caution because..."

Flag only when passive creates:
- empty meta-writing: "It is worth noting that..."
- unnecessary distance: "It should be emphasized that..."
- ceremonial phrasing: "It can be seen that..."

---

## 6. Rewriting Standard

Prefer the smallest revision that removes AI phrasing while preserving journal-quality prose.

Priority order:
1. Remove inflated or templated wording
2. Remove empty emphasis or empty transitions
3. Keep the mechanism and channel
4. Keep the comparison baseline
5. Keep specific numbers, table references, and coefficient interpretations
6. Keep the sentence suitable for a top-5 journal article

Do not:
- turn a discussion sentence into a note-style sentence
- remove all abstraction or interpretation
- replace journal prose with plain factual fragments
- strip table/column references or coefficient magnitudes

---

## 7. Avoid Memo-Style Downgrades

Flag a proposed rewrite if it:
- removes the mechanism entirely
- removes the comparison baseline
- replaces academic prose with short blunt statements
- converts a discussion sentence into a results bullet
- sounds like a policy memo, referee note, or slide narration
- strips analytical content in the name of simplicity
- loses specific numbers or table references

Bad revision pattern:
- shorter but flatter
- cleaner but less scholarly
- less AI-like but also less publishable

---

## 8. Before / After Examples

### Example 1

**AI-like (score: AI 3, JQ 1):**
"Moreover, our findings underscore that trade shocks play a pivotal role in exacerbating food insecurity -- not only through direct price transmission channels but also by undermining the resilience of vulnerable households. These results have important implications for policy design."

**Over-corrected flat (score: AI 0, JQ 3):**
"Trade shocks worsened food insecurity. Vulnerable households were most affected."

**Journal-quality (score: AI 0, JQ 0):**
"Trade shocks worsened food insecurity through direct price transmission and by placing greater pressure on households with limited capacity to absorb higher food costs."

Why: removes Moreover, underscore, pivotal role, the dash template, not-only/but-also, and the empty implication sentence; preserves the two mechanisms; remains journal-level.

### Example 2

**AI-like (score: AI 3, JQ 2):**
"This paper contributes to a more nuanced understanding of how climate variability shapes agricultural outcomes."

**Over-corrected flat (score: AI 0, JQ 3):**
"Climate variability affected agricultural outcomes."

**Journal-quality (score: AI 0, JQ 0):**
"The results show that climate variability affects agricultural outcomes unevenly across settings and sectors."

Why: removes contribution cliche and "nuanced understanding"; keeps analytical content with scope condition.

### Example 3

**AI-like (score: AI 3, JQ 1):**
"Interestingly, the coefficient on tariff reduction is positive and significant, lending support to the hypothesis that trade liberalization fosters dietary diversity through enhanced market access."

**Over-corrected flat (score: AI 0, JQ 3):**
"Tariff reductions increased dietary diversity."

**Journal-quality (score: AI 0, JQ 0):**
"Tariff reductions are associated with higher dietary diversity, consistent with improved access to imported foods."

Why: removes Interestingly and lending support; keeps mechanism; uses calibrated "associated with" and "consistent with."

---

## 9. Sentence-Level Scoring (Dual Axis)

**AI score:**
| Score | Meaning | Action |
|---|---|---|
| 0 | natural | no change |
| 1 | mildly templated | optional cleanup |
| 2 | suspicious | revise |
| 3 | strongly AI-like | revise immediately |

**Journal-quality score:**
| Score | Meaning | Action |
|---|---|---|
| 0 | journal-ready | no change |
| 1 | slightly below journal level | optional polish |
| 2 | reads like memo, note, or slide | revise |
| 3 | unacademic or analytically empty | revise immediately |

A sentence needs revision if **either** score >= 2. Prioritize by combined score.

---

## 10. Output Format

### For each flagged sentence, provide:
1. Which rules triggered (cite specific section from ai-detection.md or journal-quality.md)
2. What should be removed or softened
3. A journal-quality revision preserving mechanism and analytical content
4. Dual score: (AI: X, JQ: X)

### Overall structure:

```markdown
## Overall diagnosis
- Document type:
- Most common AI pattern:
- Most common journal-quality issue:
- Flagged sentences: [count]

## High-risk AI markers (AI score >= 2)
> "quoted sentence"
- Rule: [specific rule from ai-detection.md]
- Problem: [why it sounds templated]
- Revision: [journal-quality rewrite]
- Score: (AI: X, JQ: X)

## Journal-quality issues (JQ score >= 2)
> "quoted sentence"
- Issue: [too flat / mechanism lost / over-compressed / memo tone / missing table reference / etc.]
- What is missing: [mechanism / baseline / interpretation / specifics]
- Revision: [journal-quality rewrite]
- Score: (AI: X, JQ: X)

## Medium-risk style issues (either score = 1)
> "quoted sentence"
- Rule: [which rule]
- Revision: [suggested improvement]
- Score: (AI: X, JQ: X)

## Economics-specific issues
- Causal overreach:
- Missing comparison baseline:
- Mechanism not tied to variables:
- Significance without magnitude:
- Contribution language without specifics:

## Structure-level issues
- Section structure problems:
- Paragraph rhythm issues:
- Results reporting issues:

## Density summary
- Em dashes:
- High-risk transitions:
- Abstract-noun stacking:
- Weak-hedge density:
- Uniform sentence/paragraph length:
```

---

## 11. Forbidden Output

Never:
- rewrite into a different kind of AI prose
- give generic praise ("overall well-written")
- say only "make it more natural"
- replace one inflated AI phrase with another
- fabricate numbers, coefficients, or data not in the original text
- over-correct into memo prose, bullet-point style, or flat summaries
- strip table/column references or coefficient interpretations from revisions

Always:
- quote the original sentence
- identify the specific rule (with reference to ai-detection.md or journal-quality.md)
- explain why it fails on AI axis, JQ axis, or both
- provide a revision that would pass both axes
- check your own revision against the memo-style downgrade rules in section 7
