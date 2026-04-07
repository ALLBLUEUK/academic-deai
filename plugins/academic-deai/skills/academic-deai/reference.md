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
- `SD` / `s.d.` → write "standard deviations" or use original units
- `CI` → write "confidence interval"
- `NS` / `n.s.` → state the result directly

**Inline p-values:**
- `(p < 0.01)` inline → use stars in tables; write "significant at the 1% level" in prose

**Correct conventions:**
- Coefficient + standard error: "The effect is 0.12 (0.03)"
- Use original units when possible
- Parentheses reserved for standard errors; other insertions should be woven into the sentence

---

## Abstract Nouns (flag when stacked)
mechanism, framework, vulnerability, resilience, architecture, transmission, channel, outcome, dimension, implication
