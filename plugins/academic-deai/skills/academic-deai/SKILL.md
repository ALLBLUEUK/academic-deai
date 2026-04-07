---
name: academic-deai
description: "Detect AI-like phrasing, templated rhetoric, and economics-specific writing problems in English economics manuscripts, and suggest minimal revisions. Use when user says 'deai', 'AI traces', 'remove AI tone', 'style scrub', 'economics writing check', or 'check AI-like phrasing'."
---

# Academic De-AI for Economics Writing

## Purpose
The goal is not to eliminate all polish. The goal is to remove templated smoothness, inflated abstraction, over-complete explanation, and report-style prose so the manuscript reads like a human-written economics paper.

Prioritize:
- causal discipline
- concrete comparison baselines
- mechanism claims tied to variables or model objects
- journal-style prose over proposal-style prose

When the user provides a file path, read the file first and review the actual text before commenting.

---

## 1. Core Rule

Eliminate writing that is:
- too smooth
- too complete
- too self-explanatory
- too rhetorically balanced
- too abstract relative to the evidence

The target style is:
- precise
- concrete
- restrained
- economical
- field-journal readable

---

## 2. Economics-Specific Exemptions

Do not flag a term only because it sounds formal. Flag it when it is overused, stacked with other abstract terms, or inserted into a templated sentence.

Usually acceptable in economics writing:
- general equilibrium
- input-output linkages
- trade elasticity
- pass-through
- counterfactual
- structural vulnerability
- distributional consequences
- spillover effects
- heterogeneous effects
- asymmetric responses
- welfare analysis
- comparative advantage
- terms of trade

Only flag these when:
- they appear repeatedly in the same paragraph,
- they are stacked in one sentence,
- or they are used without a concrete object, variable, or comparison.

---

## 3. Density Thresholds

Judge by density, not by single occurrence.

| Check | Threshold | Risk |
|---|---:|---|
| Em dashes or dash-style insertions in a paragraph | >= 1 | High |
| `not A but B` / `not only A but also B` in a paragraph | >= 2 | High |
| `This paper` / `This analysis` / `These findings` at sentence start | > 2 per 1,000 words, or repeated paragraph openings | Medium |
| `Moreover` / `Furthermore` / `Additionally` in a paragraph | >= 2 | High |
| `nuanced` / `multifaceted` / `overarching` in a manuscript | > 1 each | High |
| weak hedge words in a paragraph (`broadly`, `relatively`, `somewhat`, `largely`, `in part`) | >= 3 | Medium |
| contribution clichés (`fills a gap`, `offers insights`, `sheds light`) | >= 2 in a section | High |

Use judgment. Thresholds are guides, not substitutes for reading.

---

## 4. High-Risk Lexical Markers

### 4.1 Verbs

Prefer concrete verbs over inflated or corporate ones.

| Risky | Why | Prefer |
|---|---|---|
| register | anthropomorphic | show, exhibit, report |
| underscore | AI emphasis verb | show, indicate |
| illuminate / elucidate | literary | clarify, show |
| navigate | management metaphor | face, address |
| leverage | business register | use |
| foster / bolster / buttress | AI support trio | support, strengthen |
| catalyze / galvanize / spearhead | metaphor-heavy | drive, lead to |
| unpack | conversational | examine, decompose |
| dovetail | templated alignment | is consistent with |
| engender / precipitate | inflated | cause, lead to |
| undergird | highly AI-coded | underlie, support |
| garner | unnecessary formality | receive, attract |

### 4.2 Adjectives and adverbs

#### Very high risk
- nuanced
- multifaceted
- overarching
- burgeoning
- tapestry
- landscape
- nexus
- myriad
- plethora
- realm / arena / sphere

#### Medium risk
- robust outside a statistical context
- salient
- pivotal / paramount / indispensable
- stark
- profound / profoundly
- compelling
- granular
- holistic
- far-reaching

---

## 5. High-Risk Sentence Openers and Transitions

### High risk
- Notably,
- Importantly,
- Crucially,
- Moreover,
- Furthermore,
- Additionally,
- Interestingly,
- Strikingly,
- Encouragingly,
- Reassuringly,
- Tellingly,
- Counterintuitively,
- Paradoxically,
- In light of,
- Against this backdrop,
- Taken together, these findings...

### Medium risk
- Conversely,
- Nevertheless,
- Nonetheless,
- Specifically,
- In particular,
- More broadly,

Flag these when they create a mechanical paragraph rhythm.

---

## 6. High-Risk Template Sentences

### 6.1 Role sentences
- `X plays a crucial role in Y`
- `X serves as a ...`
- `X provides a lens through which ...`
- `X offers a window into ...`
- `X speaks to the broader issue of ...`

### 6.2 Literature-positioning templates
- `a growing body of literature suggests ...`
- `the literature remains largely silent on ...`
- `to the best of our knowledge ...`
- `fills a gap in the literature`
- `sheds new light on ...`
- `contributes to a more nuanced understanding of ...`

### 6.3 Implication templates
- `has important implications for policy`
- `carries significant policy implications`
- `offers actionable insights`
- `can inform policy design`
- `warrants further investigation`
- `merits attention`
- `remains an open question`

### 6.4 Over-hedged templates
- `may well be ...`
- `could potentially ...`
- `appears to suggest ...`
- `seems to indicate ...`
- `tends to be associated with ...`

---

## 7. Syntax-Level AI Markers

### 7.1 Ban em dashes and dash-driven explanation
Treat em dashes and dash-style insertions as high-risk by default.

Replace with:
- commas
- parentheses
- semicolons
- or sentence breaks

### 7.2 Repeated contrast templates
Too many:
- `not A but B`
- `not only A but also B`
- `rather than`

These often create a templated AI cadence. Keep at most one per paragraph.

### 7.3 Meta-writing overload
Flag repeated or low-information uses of:
- `This paper`
- `This analysis`
- `These findings`
- `The implication is`
- `The results show that`

Single, information-rich uses of `This paper` are acceptable, especially in an introduction or contribution paragraph. Flag them only when:
- they appear too frequently,
- they open many paragraphs,
- or they are followed by generic contribution language rather than a concrete object, finding, or mechanism.

Prefer direct statements when possible.

### 7.4 Abstract-noun stacking
Flag sentences that pile up terms such as:
- mechanism
- framework
- vulnerability
- resilience
- architecture
- transmission
- channel
- outcome
- dimension
- implication

If a sentence contains more than one abstract core noun without a concrete variable or comparison, mark it.

### 7.5 Over-complete sentences
Flag sentences that try to contain:
- method
- result
- explanation
- implication

in one line.

Split into:
1. result
2. anchor number or comparison
3. interpretation

### 7.6 Number-dump prose
If the paragraph lists many category-level numbers in sequence, flag it.

Economics journal style should usually be:
- pattern first
- 1-2 anchor numbers
- interpretation

### 7.7 Gold-plated closing sentences
Flag paragraph endings that sound like policy-report slogans:
- `therefore requires...`
- `this demonstrates that...`
- `the implication is that...`

Not every paragraph needs a maximally polished closing line.

---

## 8. Economics-Specific Writing Risks

These are not always AI markers, but they are common in weak economics drafts and often overlap with AI-generated prose.

### 8.1 Causal overreach
Flag verbs such as:
- cause
- drive
- lead to
- explain
- determine
- shape
- account for

when the design does not support that level of causal language.

Ask:
- Is there an identification strategy?
- Is there a formal decomposition?
- Is the model structure sufficient for this claim?

If not, suggest weaker language.

### 8.2 Significance without magnitude
Flag:
- positive and significant
- statistically significant
- economically meaningful
- robustly significant

when there is no:
- coefficient magnitude
- unit
- benchmark
- economic interpretation

### 8.3 Missing comparison baseline
Flag comparative language when no baseline is stated:
- increases
- declines
- larger
- smaller
- more
- less
- higher
- lower

Every comparative claim should identify what it is relative to.

### 8.4 Mechanism without variable anchoring
Flag mechanism claims that do not mention a concrete object:
- through several channels
- reflecting structural factors
- via multiple mechanisms
- through market frictions

Mechanism claims should be tied to:
- a variable
- a coefficient
- a policy
- a model object
- a group comparison

### 8.5 Proposal-style contribution language
Flag:
- fills an important gap
- offers novel insights
- provides a useful lens
- contributes to a richer understanding
- has broad relevance for

These often sound like grant applications rather than journal prose.

### 8.6 Literature positioning without specifics
If the text says it is:
- consistent with the literature
- in line with prior work
- related to previous studies

without specifying how, flag it.

### 8.7 Weak-hedge density
Flag high-density use of:
- broadly
- relatively
- somewhat
- largely
- in part
- to some extent

These are often used by AI to sound cautious without being precise.

### 8.8 Non-standard statistical notation

AI-generated economics prose often uses notation conventions from other fields or from informal writing. Flag and correct the following:

**Abbreviations that do not belong in economics papers:**
- `SD` or `s.d.` for standard deviation → write "standard deviations" in full, or report in original units
- `CI` for confidence interval → write "confidence interval" or use bracket notation as per journal style
- `NS` or `n.s.` for not significant → do not use; state the result directly

**Inline p-values and parenthetical test statistics:**
- `(p < 0.01)` or `(p = 0.03)` inserted inline → economics papers report significance via stars on coefficients in tables, not inline p-values in prose
- `(Table 3, col. 2)` as parenthetical mid-sentence → acceptable but check whether it reads like a figure caption rather than prose; often better at sentence end or as a separate reference

**Correct economics conventions:**
- Report coefficient + standard error in parentheses: "The effect is 0.12 (0.03)"
- Use stars in tables for significance levels, not inline text
- Write "significant at the 1% level" if significance must be mentioned in prose, not "p < 0.01"
- Use original units when possible: "a 10 percentage point tariff reduction increased the diet diversity index by 0.8 points" rather than "by 0.4 SD"
- When standard-deviation units are necessary, write "standard deviations" in full on first use

**Parenthesis overload:**
- Flag sentences with two or more parenthetical insertions — this is a common AI pattern that makes prose read like annotated code rather than journal text
- Economics papers use parentheses sparingly in running text; heavy parenthetical style is a marker of AI or report-style writing

---

## 9. Structure-Level Checks

### 9.1 Paragraphs that all sound the same
Flag sections where every paragraph has the same rhythm and shape.

### 9.2 Results as figure narration
Flag Results paragraphs that merely read off the figure without explaining why the pattern matters.

### 9.3 Discussion as second abstract
Only the first paragraph of a Discussion may mainly summarize. Later paragraphs must add:
- mechanism
- contribution
- limitation
- implication

### 9.4 Methods as tutorial
Methods should be reproducible, not pedagogical. Remove lecture-style explanation unless needed for a non-specialist audience.

---

## 10. Figure and Caption Checks

### 10.1 Figure quality
Check whether the figure:
- answers one empirical question
- has enough information density for a main-text figure
- avoids dashboard or slide-deck aesthetics
- uses consistent color mapping across figures
- has no label or legend overlap
- has consistent panel-label placement
- has readable font sizes

### 10.2 Caption discipline
A good economics-journal caption should tell the reader:
- what is plotted
- sample or exclusion rule
- statistic used
- confidence interval / error bar definition

A caption should not:
- restate the full substantive conclusion
- argue policy implications
- read like slide notes

---

## 11. Sentence-Level Scoring

Score each flagged sentence:

| Score | Meaning | Action |
|---|---|---|
| 0 | natural | no change needed |
| 1 | mildly templated | optional cleanup |
| 2 | suspicious | revise |
| 3 | strongly AI-like | revise immediately |

Prioritize scores 2 and 3.

---

## 12. Revision Priority Order

When suggesting edits, follow this order:
1. remove em dashes
2. remove repeated or low-information `This paper` / `These findings` sentence starts
3. reduce contrast templates
4. reduce abstract-noun density
5. split over-complete sentences
6. replace slogan-like closing lines with concrete result statements
7. add comparison baselines where missing
8. tone down causal language where identification is weak

---

## 13. Output Format

Always return the review in this structure:

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
- Minimal revision move:
- Score: 2 or 3

## Medium-risk style issues
> "quoted sentence"
- Rule triggered:
- Why it is risky:
- Minimal revision move:
- Score: 1 or 2

## Economics-specific issues
- Causal overreach:
- Missing comparison baseline:
- Mechanism not tied to variables:
- Significance without magnitude:
- Proposal-style contribution language:

## Figure and caption issues
- Figure:
- Problem:
- Why it looks unpolished:
- Minimal fix:

## Suggested rewrites
- Sentence:
- Keep:
- Cut:
- Replace with:

## Density summary
- Em dashes:
- High-risk transitions:
- `This paper` sentence starts:
- Abstract-noun stacking:
- Weak-hedge density:
```

Do not praise vaguely. Do not rewrite entire sections unless asked.

---

## 14. Forbidden Output

Never:
- rewrite the whole paragraph into a different kind of AI prose
- give generic praise
- say only “make it more natural”
- replace one inflated AI phrase with another inflated AI phrase
- produce longer replacement sentences than the originals unless necessary

Always:
- quote the original sentence
- identify the rule
- explain why it is risky
- propose the smallest effective fix
