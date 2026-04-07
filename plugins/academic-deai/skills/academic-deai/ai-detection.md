# AI Detection Rules for Economics Writing

This file contains all AI-specific detection rules: lexical markers, template sentences, syntax patterns, density thresholds, and economics-specific AI risks. Referenced by the main SKILL.md.

---

## 1. High-Risk Verbs

| Risky verb | Why | Prefer |
|---|---|---|
| register | anthropomorphic ("food groups register positive") | show, exhibit, report |
| underscore | AI emphasis verb | show, indicate |
| illuminate / elucidate | literary register | clarify, show |
| navigate | management metaphor | face, address |
| leverage | business register | use |
| foster / bolster / buttress | AI support trio | support, strengthen |
| catalyze / galvanize / spearhead | metaphor-heavy | drive, lead to |
| unpack | conversational | examine, decompose |
| dovetail | templated alignment | is consistent with |
| engender / precipitate | inflated | cause, lead to |
| undergird | highly AI-coded | underlie, support |
| garner | unnecessary formality | receive, attract |
| delve into | never appears in top-5 papers | examine, investigate |
| utilize | pretentious | use |

---

## 2. High-Risk Adjectives and Adverbs

### Very high risk (flag on sight)
- nuanced / "a more nuanced understanding"
- multifaceted
- overarching
- burgeoning
- tapestry
- landscape (non-geographic)
- nexus
- myriad / plethora
- realm / arena / sphere
- groundbreaking
- holistic

### Medium risk (flag when dense or stacked)
- robust (outside statistical context)
- salient
- pivotal / paramount / indispensable
- stark
- profound / profoundly
- compelling
- granular
- far-reaching
- crucial (hyperbolic in most contexts)

### Filler adverbs (flag on sight)
- basically / essentially / fundamentally
- broadly / relatively / somewhat / largely / in part (flag when >=3 per paragraph)

---

## 3. High-Risk Sentence Openers

### High risk (flag on sight)
- Notably, Importantly, Crucially
- Moreover, Furthermore, Additionally (flag when >=2 in a paragraph)
- Interestingly, Strikingly, Encouragingly, Reassuringly, Tellingly
- Counterintuitively, Paradoxically
- In light of, Against this backdrop
- Taken together, these findings...
- It is important to note that...
- It is worth noting that...
- It should be emphasized that...
- It can be seen that...

### Medium risk (flag when dense)
- Conversely, Nevertheless, Nonetheless
- Specifically, In particular, More broadly
- As mentioned earlier (if it was mentioned, don't repeat it)

### Off-register openers (not standard in top-5)
- "This study aims to..." → use "This paper estimates/shows/provides evidence"
- "In today's world..." / "In the modern economy..." → vague framing, delete
- "Firstly, Secondly, Thirdly" → use "First, Second, Third,"

---

## 4. High-Risk Template Sentences

### Role sentences
- X plays a crucial/pivotal/key role in Y
- X serves as a ...
- X provides a lens through which ...
- X offers a window into ...
- X speaks to the broader issue of ...

### Literature-positioning templates
- a growing body of literature suggests ...
- the literature remains largely silent on ...
- fills a gap in the literature
- sheds new light on ...
- contributes to a more nuanced understanding of ...
- offers novel insights into ...
- provides a useful lens for ...

### Implication templates
- has important implications for policy
- carries significant policy implications
- offers actionable insights
- can inform policy design
- warrants further investigation
- merits attention
- remains an open question
- These results have important implications for policy design.

### Over-hedged templates
- may well be ...
- could potentially ...
- appears to suggest ...
- seems to indicate ...
- tends to be associated with ...
- We tentatively suggest that our preliminary results might possibly indicate...

### Evaluative templates (never appear in top-5)
- This is a very interesting finding
- This remarkable result...
- This compelling evidence...

---

## 5. Syntax-Level Markers

### 5.1 Em dashes
Treat as high-risk AI marker. AI writing uses em dashes to insert parenthetical expansions, creating the "not only A -- but also B" or "X -- a pattern that..." template.

**Rule:** Replace every em dash with a comma, semicolon, or sentence break. Zero em dashes is the target.

### 5.2 Contrast templates
- `not A but B`
- `not only A but also B`
- `rather than A, B`

**Rule:** Keep at most one per paragraph. When stacked, these create an unmistakable AI rhythm.

### 5.3 Meta-writing overload
Flag repeated self-referential constructions:
- `This paper` / `This analysis` / `This study`
- `These findings` / `Our findings` / `The findings`
- `The implication is` / `The key takeaway is`

**Rule:** Apply the "This paper" rule from SKILL.md §4. Flag when >2 per 1,000 words or used as repeated paragraph openers.

### 5.4 Abstract-noun stacking
Flag sentences with more than one abstract core noun without a concrete variable or comparison anchoring them:
- mechanism, framework, vulnerability, resilience, architecture
- transmission, channel, outcome, dimension, implication

**Example (bad):** "The mechanism through which this channel of transmission affects outcomes has important implications."
**Example (good):** "Trade shocks reduce food security through higher import prices."

### 5.5 Over-complete sentences
Flag sentences that try to pack method + result + explanation + implication into one line.

**Rule:** Split into: result sentence (with table reference), then interpretation sentence.

### 5.6 Number-dump prose
Flag paragraphs that list many category-level numbers sequentially without interpretation.

**Rule:** Pattern-first, then 1-2 anchor numbers, then interpretation.

### 5.7 Gold-plated closings
Flag paragraph endings that sound like slogans or TED talk conclusions. Not every paragraph needs a maximally polished closing line.

### 5.8 Uniform length (AI structural marker)
- Uniform sentence length (real papers vary 8-35 words)
- Uniform paragraph length (real papers vary 3-10 sentences)
- Perfectly parallel structures repeated mechanically across paragraphs
- Synonym cycling: "effect/impact/influence" used in artificial rotation
- Lists of exactly three where two or four would be more natural

---

## 6. Economics-Specific AI Risks

### 6.1 Causal overreach
Flag `cause`, `drive`, `shape`, `determine` when the empirical design does not support that level of causal language.

**Rule:** Match verb strength to identification strategy. IV/RDD/RCT can support "causes"; DiD supports "leads to" or "is associated with"; OLS cross-section supports only "is correlated with" or "predicts."

### 6.2 Significance without magnitude
Flag "positive and significant" or "statistically significant effect" with no coefficient, unit, or benchmark.

**Rule:** Every significance claim must be accompanied by a magnitude and unit. "The effect is 0.12 (0.03), significant at the 1% level" — not just "significant."

### 6.3 Missing comparison baseline
Flag comparative language ("larger", "stronger", "more pronounced") without stating what it is relative to.

**Rule:** Every comparison must name the baseline: "larger than the OLS estimate", "stronger for women than for men", "more pronounced in urban areas relative to rural."

### 6.4 Mechanism without variable anchoring
Flag mechanism claims that name no variable, coefficient, policy, or model object.

**Bad:** "The underlying mechanism operates through multiple channels."
**Good:** "Trade shocks reduce food security through higher import prices (price channel) and lower household income (income channel)."

### 6.5 Proposal-style language
Flag: `fills an important gap`, `offers novel insights`, `provides a useful lens`, `contributes to a more nuanced understanding`.

**Rule:** Contribution claims must be specific about what is new: "better data", "cleaner identification", "first estimates of X", "new mechanism" — not vague importance claims.

### 6.6 Literature positioning without specifics
Flag "consistent with the literature" or "as previous studies have shown" without citing specific papers or findings.

**Rule:** Always specify which findings: "consistent with Autor (2003), who finds that..."

### 6.7 Weak-hedge density
Flag high-density use of: broadly, relatively, somewhat, largely, in part.

**Threshold:** >= 3 weak hedges in a single paragraph.

---

## 7. Density Thresholds

| Check | Threshold | Risk |
|---|---:|---|
| Em dashes in a paragraph | >= 1 | High |
| `not A but B` / `not only A but also B` in a paragraph | >= 2 | High |
| `This paper` / `This analysis` / `These findings` at sentence start | > 2 per 1,000 words | Medium |
| `Moreover` / `Furthermore` / `Additionally` in a paragraph | >= 2 | High |
| `nuanced` / `multifaceted` / `overarching` in a manuscript | > 1 each | High |
| Weak hedge words in a paragraph | >= 3 | Medium |
| Contribution cliches in a section | >= 2 | High |
| Evaluative adjectives ("interesting", "remarkable", "compelling") | >= 1 | High |
| Synonym cycling (effect/impact/influence rotation) in a page | >= 3 alternations | Medium |
| Uniform sentence length (all within ±5 words of mean) | sustained over 5+ sentences | Medium |

---

## 8. Economics-Specific Exemptions

These terms are standard economics vocabulary. Flag only when stacked (3+ in one sentence) or repeated mechanically:

- general equilibrium, input-output linkages, trade elasticity
- pass-through, counterfactual, structural vulnerability
- distributional consequences, spillover effects, heterogeneous effects
- asymmetric responses, welfare analysis, comparative advantage, terms of trade
- IV, DiD, FE, RDD (disciplinary shorthand, do not require full definition in economics papers)

---

## 9. Non-Standard Statistical Notation

### Abbreviations to avoid in prose
- `SD` / `s.d.` → write "standard deviations" or use original units
- `CI` → write "confidence interval"
- `NS` / `n.s.` → state the result directly ("the coefficient is small and not statistically significant")

### Inline p-values
- `(p < 0.01)` inline → use stars in tables; write "significant at the 1% level" in prose
- `(p = 0.023)` inline → almost never appears in top-5 papers; report in tables only

### Correct conventions
- Coefficient + standard error: "The effect is 0.12 (0.03)"
- Use original units when possible: "3.2 percentage points" not "0.4 standard deviations"
- Parentheses in prose reserved for standard errors and table/column references
- Leading zeros required: 0.357, never .357
- "Percent" vs "percentage points" must be used precisely — these are different quantities

### Parenthesis overload
Flag sentences with more than one set of parentheses. Restructure so that only standard errors or table references use parentheses; other insertions should be woven into the sentence.
