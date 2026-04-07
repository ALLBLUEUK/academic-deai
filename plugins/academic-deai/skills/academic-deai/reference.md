# Academic De-AI: Reference Tables

This file contains the lexical markers, sentence templates, and density thresholds referenced by the main academic-deai skill. Read this file when you need to check specific words, phrases, or patterns.

---

## High-Risk Verbs

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

---

## High-Risk Adjectives and Adverbs

### Very high risk (flag on sight)
- nuanced / a more nuanced understanding
- multifaceted
- overarching
- burgeoning
- tapestry
- landscape (non-geographic)
- nexus
- myriad / plethora
- realm / arena / sphere

### Medium risk (flag when dense)
- robust (outside statistical context)
- salient
- pivotal / paramount / indispensable
- stark
- profound / profoundly
- compelling
- granular
- holistic
- far-reaching

---

## High-Risk Sentence Openers

### High risk
Notably, Importantly, Crucially, Moreover, Furthermore, Additionally, Interestingly, Strikingly, Encouragingly, Reassuringly, Tellingly, Counterintuitively, Paradoxically, In light of, Against this backdrop, Taken together these findings...

### Medium risk
Conversely, Nevertheless, Nonetheless, Specifically, In particular, More broadly,

---

## High-Risk Template Sentences

### Role sentences
- X plays a crucial role in Y
- X serves as a ...
- X provides a lens through which ...
- X offers a window into ...
- X speaks to the broader issue of ...

### Literature-positioning templates
- a growing body of literature suggests ...
- the literature remains largely silent on ...
- to the best of our knowledge ...
- fills a gap in the literature
- sheds new light on ...
- contributes to a more nuanced understanding of ...

### Implication templates
- has important implications for policy
- carries significant policy implications
- offers actionable insights
- can inform policy design
- warrants further investigation
- merits attention
- remains an open question

### Over-hedged templates
- may well be ...
- could potentially ...
- appears to suggest ...
- seems to indicate ...
- tends to be associated with ...

---

## Density Thresholds

| Check | Threshold | Risk |
|---|---:|---|
| Em dashes or dash-style insertions in a paragraph | >= 1 | High |
| `not A but B` / `not only A but also B` in a paragraph | >= 2 | High |
| `This paper` / `This analysis` / `These findings` at sentence start | > 2 per 1,000 words, or repeated paragraph openings | Medium |
| `Moreover` / `Furthermore` / `Additionally` in a paragraph | >= 2 | High |
| `nuanced` / `multifaceted` / `overarching` in a manuscript | > 1 each | High |
| weak hedge words in a paragraph (`broadly`, `relatively`, `somewhat`, `largely`, `in part`) | >= 3 | Medium |
| contribution cliches (`fills a gap`, `offers insights`, `sheds light`) | >= 2 in a section | High |

---

## Economics-Specific Exemptions

Usually acceptable (flag only when stacked or repeated):
- general equilibrium, input-output linkages, trade elasticity
- pass-through, counterfactual, structural vulnerability
- distributional consequences, spillover effects, heterogeneous effects
- asymmetric responses, welfare analysis, comparative advantage, terms of trade

---

## Non-Standard Statistical Notation

**Abbreviations to avoid:**
- `SD` / `s.d.` â†?write "standard deviations" or use original units
- `CI` â†?write "confidence interval"
- `NS` / `n.s.` â†?state the result directly

**Inline p-values:**
- `(p < 0.01)` inline â†?use stars in tables; write "significant at the 1% level" in prose

**Correct conventions:**
- Coefficient + standard error: "The effect is 0.12 (0.03)"
- Use original units when possible
- Parentheses reserved for standard errors; other insertions should be woven into the sentence

---

## Abstract Nouns (flag when stacked)
mechanism, framework, vulnerability, resilience, architecture, transmission, channel, outcome, dimension, implication


---

## Journal-Quality Positive Markers (Top-5 Standard)

Presence of these markers indicates journal-quality prose. Their absence may indicate under-written or non-academic prose.

1. Specific table/column references when discussing results: "(Table 3, column 4)"
2. Quantitative coefficient interpretation: "implies a X% increase"
3. Calibrated hedging that varies by claim type (not uniform)
4. Present tense for results, past tense for procedures
5. Varied sentence length (8-35 words range)
6. Topic sentences that make claims, not meta-statements
7. Section structure matching the canonical economics template
8. Standard errors in parentheses with clear labeling
9. Leading zeros on all decimals (0.357, not .357)
10. Disciplinary shorthand used naturally (IV, DiD, FE, RDD)
11. First-person plural "we" as default voice
12. One idea per paragraph, 4-8 sentences typical
13. Contributions enumerated and anchored to specific prior papers
14. Mechanism discussion structured as: evidence ¡ú interpretation ¡ú alternatives

---

## Journal-Quality Negative Markers (Top-5 Standard)

Presence of these markers indicates non-journal-quality prose, independent of AI detection.

### Vocabulary red flags
- "delve into" ¡ª never appears in top-5 papers
- "it is important to note that" ¡ª filler, delete
- "crucial", "pivotal", "groundbreaking" ¡ª hyperbolic
- "in today's world", "in the modern economy" ¡ª vague framing
- "various", "numerous", "a plethora of" ¡ª imprecise quantifiers
- "utilize" instead of "use" ¡ª pretentious
- "Firstly", "Secondly", "Thirdly" ¡ª use "First," "Second," "Third,"
- "in order to" ¡ª just "to"
- "whether or not" ¡ª just "whether"
- "basically", "essentially", "fundamentally" ¡ª filler adverbs
- "this study aims to" ¡ª off-register; use "this paper estimates/shows/provides evidence"

### Structural red flags
- Literature review as standalone section that surveys without connecting to contribution
- Introduction that buries the research question past page 2
- Results discussed without reference to specific tables and columns
- Conclusion that introduces new arguments or evidence
- Excessive bullet points in running text
- Sections too short (1-2 paragraphs) or too long (15+ pages without subsections)
- Footnotes that are mini-essays

### Tone red flags
- Excessive hedging: "tentatively suggest that preliminary results might possibly indicate"
- Insufficient hedging: "We prove that X causes Y" in observational study
- Evaluative adjectives: "interesting finding", "remarkable result"
- Emotional language: "Sadly, unemployment rose"
- Grandiose claims: "revolutionizes our understanding"
- Rhetorical questions (almost never appear in top-5 papers)
- Exclamation marks (never)

### Uniformity red flags (AI + quality failure)
- Uniform sentence length throughout
- Uniform paragraph length throughout
- Perfectly parallel structures repeated mechanically
- Synonym cycling: "effect/impact/influence" used in rotation
- Generic hedging applied uniformly regardless of claim type

---

## Standard Phrases in Top-5 Papers (Acceptable)

These phrases are common in published top-5 papers and should NOT be flagged:

### Results reporting
- "We find that..."
- "Our results suggest that..."
- "The estimates are consistent with..."
- "The coefficient is statistically significant at the X percent level."
- "The magnitude implies that..."
- "Column (1) reports results from..."
- "The dependent variable in all columns is..."
- "Results are robust to..."

### Methods
- "We exploit variation in..."
- "We instrument for X using Z..."
- "Conditional on [controls]..."
- "In our preferred specification..."
- "Standard errors, clustered at the [level], are reported in parentheses."
- "We include [entity] and [time] fixed effects."

### Contribution and framing
- "This paper makes [N] contributions."
- "To the best of our knowledge..."
- "We contribute to the literature on X by..."
- "Unlike [Author], who studies X, we focus on Y."
- "The remainder of the paper is organized as follows."

### Mechanism and interpretation
- "One possible mechanism is..."
- "This is consistent with a model in which..."
- "A natural interpretation is that..."
- "An alternative explanation is that... However, this seems unlikely because..."
- "We cannot rule out that..."

### Limitations
- "Our analysis is subject to several limitations."
- "The results should be interpreted with caution because..."