---
name: academic-deai
description: "Detect AI-like phrasing, templated rhetoric, and economics-specific writing problems in English economics manuscripts, and suggest minimal revisions. Use when user says 'deai', 'AI traces', 'remove AI tone', 'style scrub', 'economics writing check', or 'check AI-like phrasing'."
---

# Academic De-AI for Economics Writing

**Core mission: remove AI traces without destroying journal-quality economics prose.**

When the user provides a file path, read the file first. For word lists, template lists, and density thresholds, read the reference file `reference.md` in the same directory as this file.

---

## 1. Journal-Quality Guardrail

The goal is not to strip prose down to bare statements. The goal is to remove AI-like phrasing while preserving journal-quality economics writing.

Good revisions should remain:
- analytically informative
- readable
- moderately abstract when needed
- suitable for a journal article, not a memo, referee report, or slide deck

Do not flatten a sentence merely to make it shorter.
Do not replace a polished academic sentence with a blunt note-style sentence unless the original is severely inflated.
Preserve legitimate interpretation, mechanism, and argumentative structure.

---

## 2. Distinguish Three Cases

When reviewing a sentence, distinguish between:

**1. AI-like phrasing**
Templated, over-smoothed, over-complete, rhetorically inflated, or mechanically balanced writing. This should be flagged and revised.

**2. Acceptable academic abstraction**
Standard journal prose that uses moderate abstraction, careful interpretation, or contribution framing tied to a concrete object. This should be preserved.

**3. Over-corrected flat prose**
Writing that removes AI markers by stripping away legitimate academic texture, leaving the sentence sounding like a memo or an internal note. This is a bad revision and should be avoided.

---

## 3. Preserve These Academic Features

Do not automatically remove the following if they are concrete and disciplined:

- moderate abstraction tied to a specific object
- mechanism language tied to variables, institutions, sectors, or model objects
- restrained interpretation
- occasional contribution framing
- occasional passive constructions used for discipline or structure
- normal economics prose rhythm, including one sentence of interpretation after a result

Examples of acceptable academic prose:
- "The results suggest that..."
- "This pattern is consistent with..."
- "The estimates indicate that..."
- "A likely mechanism is..."
- "This paper studies..."
- "Several limitations should be acknowledged."

---

## 4. "This paper" Rule

Do not ban "This paper" outright.

Acceptable:
- one or two information-rich uses in the introduction
- occasional use in contribution framing
- occasional use in discussion when referring to the paper's specific contribution

Flag only when:
- repeated frequently
- used at the start of many paragraphs
- followed by generic contribution language
- used instead of stating a concrete result, mechanism, or object

---

## 5. Passive Voice Rule

Do not flag passive voice mechanically.

Acceptable passive constructions:
- "Several limitations should be acknowledged."
- "The estimates are reported in Table 2."
- "The sample is restricted to..."
- "The results should be interpreted as..."

Flag passive voice only when it creates:
- empty meta-writing
- unnecessary distance from the claim
- inflated or ceremonial phrasing

Higher-risk passive examples:
- "It is worth noting that..."
- "It should be emphasized that..."
- "It can be seen that..."

---

## 6. Rewriting Standard

When revising, prefer the smallest revision that removes AI-like phrasing while preserving journal-quality prose.

Priority:
1. remove inflated or templated wording
2. remove empty emphasis or empty transitions
3. keep the mechanism
4. keep the comparison baseline
5. keep the sentence suitable for a journal article

Do not:
- turn a discussion sentence into a note-style sentence
- remove all abstraction
- remove all interpretation
- replace journal prose with plain factual fragments unless necessary

---

## 7. Avoid Memo-Style Downgrades

Flag a proposed rewrite if it does any of the following:
- removes the mechanism entirely
- removes the comparison baseline
- replaces academic prose with short blunt statements
- converts a discussion sentence into a results bullet
- sounds like a policy memo, referee note, or slide narration
- strips a sentence of all analytical content in the name of simplicity

Bad revision pattern:
- shorter but flatter
- cleaner but less scholarly
- less AI-like but also less publishable

---

## 8. Before / After Examples

### Example 1

**AI-like:**
"Moreover, our findings underscore that trade shocks play a pivotal role in exacerbating food insecurity -- not only through direct price transmission channels but also by undermining the resilience of vulnerable households."

**Over-corrected flat:**
"Trade shocks worsened food insecurity. Vulnerable households were most affected."

**Journal-quality:**
"Trade shocks worsened food insecurity through direct price transmission and by placing greater pressure on households with limited capacity to absorb higher food costs."

Why the third is preferred: removes Moreover, underscore, pivotal role, the dash template, and not-only/but-also; preserves the mechanism; remains suitable for a journal article.

### Example 2

**AI-like:**
"This paper contributes to a more nuanced understanding of how climate variability shapes agricultural outcomes."

**Over-corrected flat:**
"Climate variability affected agricultural outcomes."

**Journal-quality:**
"The results show that climate variability affects agricultural outcomes unevenly across settings and sectors."

Why: removes the contribution cliche; keeps analytical content; preserves journal-level abstraction.

### Example 3

**AI-like:**
"Interestingly, the coefficient on tariff reduction is positive and significant, lending support to the hypothesis that trade liberalization fosters dietary diversity through enhanced market access."

**Over-corrected flat:**
"Tariff reductions increased dietary diversity."

**Journal-quality:**
"Tariff reductions are associated with higher dietary diversity, consistent with improved access to imported foods."

Why: removes Interestingly and lending support; keeps the mechanism; keeps the sentence at journal level rather than memo level.

---

## 9. Tone Calibration

Target style:
- like a careful economics author writing for a journal
- not like a grant proposal
- not like a policy memo
- not like a referee report
- not like a generated summary

If forced to choose, prefer journal-quality clarity over blunt simplicity.

---

## 10. Detection Rules

For detailed word lists, template lists, and density thresholds, refer to `reference.md`.

### 10.1 Lexical markers
Flag high-risk verbs, adjectives, sentence openers, and template sentences listed in the reference file. Apply density thresholds, not mechanical word-matching.

### 10.2 Syntax-level markers

**Em dashes:** treat as high-risk. Replace with commas, semicolons, or sentence breaks.

**Contrast templates:** `not A but B`, `not only A but also B`, `rather than`. Keep at most one per paragraph.

**Meta-writing overload:** flag repeated `This paper`, `This analysis`, `These findings`, `The implication is`. Apply the "This paper" rule in section 4.

**Abstract-noun stacking:** flag sentences with more than one abstract core noun without a concrete variable or comparison.

**Over-complete sentences:** flag sentences that try to contain method + result + explanation + implication in one line. Split into result, anchor number, interpretation.

**Number-dump prose:** flag paragraphs that list many category-level numbers. Prefer pattern-first, then 1-2 anchor numbers, then interpretation.

**Gold-plated closings:** flag paragraph endings that sound like slogans. Not every paragraph needs a maximally polished closing line.

### 10.3 Economics-specific risks

**Causal overreach:** flag `cause`, `drive`, `shape`, `determine` when the design does not support that level of causal language.

**Significance without magnitude:** flag `positive and significant` with no coefficient, unit, or benchmark.

**Missing comparison baseline:** flag comparative language without stating what it is relative to.

**Mechanism without variable anchoring:** flag mechanism claims that name no variable, coefficient, policy, or model object.

**Proposal-style language:** flag `fills an important gap`, `offers novel insights`, `provides a useful lens`.

**Literature positioning without specifics:** flag `consistent with the literature` without specifying which findings.

**Weak-hedge density:** flag high-density `broadly`, `relatively`, `somewhat`, `largely`, `in part`.

**Non-standard notation:** flag inline p-values, SD abbreviation, parenthesis overload. See reference file for details.

---

## 11. Structure-Level Checks

### 11.1 Paragraphs that all sound the same
Flag sections where every paragraph has the same rhythm and shape.

### 11.2 Results as figure narration
Flag Results paragraphs that merely read off the figure without explaining why the pattern matters.

### 11.3 Discussion as second abstract
Only the first paragraph of a Discussion may mainly summarize. Later paragraphs must add mechanism, contribution, limitation, or implication.

### 11.4 Methods as tutorial
Methods should be reproducible, not pedagogical.

---

## 12. Figure and Caption Checks

### 12.1 Figure quality
Check: answers one empirical question, sufficient information density, no dashboard aesthetics, consistent color mapping, no label/legend overlap, consistent panel labels, readable fonts.

### 12.2 Caption discipline
Should state: what is plotted, sample rule, statistic used, error bar definition.
Should not: restate the conclusion, argue policy implications, read like slide notes.

---

## 13. Sentence-Level Scoring

| Score | Meaning | Action |
|---|---|---|
| 0 | natural | no change needed |
| 1 | mildly templated | optional cleanup |
| 2 | suspicious | revise |
| 3 | strongly AI-like | revise immediately |

Prioritize scores 2 and 3.

---

## 14. Output Format

### For each flagged sentence, provide:
1. Why it sounds AI-like (which rules triggered)
2. What should be removed or softened
3. A journal-quality revision that preserves mechanism and analytical content

Do not default to the shortest possible rewrite. The rewrite should read like polished economics prose, not like a stripped-down summary.

### Overall structure:

```markdown
## Overall diagnosis
- Document type:
- Most common high-risk pattern:
- Most important economics-writing issue:
- Number of flagged sentences:

## High-risk AI markers
> "quoted sentence"
- Rule triggered:
- Why it sounds templated:
- Journal-quality revision:
- Score: 2 or 3

## Medium-risk style issues
> "quoted sentence"
- Rule triggered:
- Why it is risky:
- Journal-quality revision:
- Score: 1 or 2

## Economics-specific issues
- Causal overreach:
- Missing comparison baseline:
- Mechanism not tied to variables:
- Significance without magnitude:
- Proposal-style contribution language:

## Density summary
- Em dashes:
- High-risk transitions:
- Abstract-noun stacking:
- Weak-hedge density:
```

---

## 15. Forbidden Output

Never:
- rewrite into a different kind of AI prose
- give generic praise
- say only "make it more natural"
- replace one inflated AI phrase with another
- fabricate numbers, coefficients, or data not in the original text
- over-correct into memo prose, bullet-point style, or flat summaries

Always:
- quote the original sentence
- identify the rule
- explain why it is risky
- provide a journal-quality revision that preserves mechanism and analytical content
- check your own revision against the memo-style downgrade rules in section 7
