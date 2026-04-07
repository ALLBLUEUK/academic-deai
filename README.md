<p align="center">
  <img src="https://em-content.zobj.net/source/apple/391/magnifying-glass-tilted-left_1f50d.png" width="100" />
</p>

<h1 align="center">academic-deai</h1>

<p align="center">
  <strong>Your paper should sound like you wrote it, not like a model completed a writing task.</strong>
</p>

<p align="center">
  <a href="https://github.com/ALLBLUEUK/academic-deai/stargazers"><img src="https://img.shields.io/github/stars/ALLBLUEUK/academic-deai?style=flat&color=yellow" alt="Stars"></a>
  <a href="https://github.com/ALLBLUEUK/academic-deai/commits/main"><img src="https://img.shields.io/github/last-commit/ALLBLUEUK/academic-deai?style=flat" alt="Last Commit"></a>
  <a href="LICENSE"><img src="https://img.shields.io/github/license/ALLBLUEUK/academic-deai?style=flat" alt="License"></a>
</p>

<p align="center">
  <a href="#before--after">Before / After</a> &middot;
  <a href="#what-it-catches">What It Catches</a> &middot;
  <a href="#install">Install</a> &middot;
  <a href="#usage">Usage</a>
</p>

---

A [Claude Code](https://docs.anthropic.com/en/docs/claude-code) and [Codex](https://openai.com/index/codex/) skill that evaluates economics manuscripts on two axes: **AI contamination** and **journal quality** (benchmarked against AER, QJE, Econometrica, JPE, REStud conventions). It scores every sentence, flags the worst offenders, and tells you exactly what to delete, swap, or split.

Built for economics papers. Useful for any social-science manuscript.

## Before / After

<table>
<tr>
<td width="50%">

### Before (AI: 3, JQ: 2)

> "Moreover, our findings underscore that trade shocks play a pivotal role in exacerbating food insecurity -- not only through direct price transmission channels but also by undermining the resilience of vulnerable households. These results have important implications for policy design."

</td>
<td width="50%">

### After (AI: 0, JQ: 0)

> "Trade shocks worsened food insecurity through higher prices for imported staples and by reducing the purchasing power of low-income households."

</td>
</tr>
<tr>
<td>

### Before (AI: 3, JQ: 2)

> "This paper contributes to a more nuanced understanding of how climate variability shapes agricultural outcomes. Notably, the heterogeneous effects across food groups illuminate the multifaceted nature of dietary vulnerability in developing economies."

</td>
<td>

### After (AI: 0, JQ: 0)

> "Climate variability affects agricultural outcomes unevenly across food groups: cereals and perishable crops show larger declines than legumes or dairy in our sample of developing economies."

</td>
</tr>
<tr>
<td>

### Before (AI: 3, JQ: 2)

> "Interestingly, the coefficient on tariff reduction is positive and significant, lending support to the hypothesis that trade liberalization fosters dietary diversity through enhanced market access."

</td>
<td>

### After (AI: 0, JQ: 0)

> "Tariff reductions are associated with higher dietary diversity, consistent with greater access to imported food varieties in the treated regions."

</td>
</tr>
</table>

**AI traces removed. Journal quality achieved.**

---

## What It Catches

### Two-axis evaluation

Every sentence is scored on two independent axes:

| Axis | What it measures | Scale |
|---|---|---|
| **AI score** | Templated rhetoric, inflated phrasing, mechanical balance | 0-3 |
| **JQ score** | Adherence to top-5 economics journal conventions | 0-3 |

A sentence needs revision if **either** score >= 2. A sentence can be low on AI markers and still fail journal quality (too flat, too memo-like, missing table references).

### AI lexical markers
Flags verbs like `underscore`, `foster`, `leverage`, `illuminate`, `dovetail`, `undergird` and adjectives like `nuanced`, `multifaceted`, `overarching`, `pivotal` that are high-frequency AI fingerprints.

### Template sentences
Detects canned patterns: `plays a crucial role`, `has important implications for`, `fills a gap in the literature`, `warrants further investigation`, `a growing body of literature suggests`.

### Density, not just occurrence
A single `Moreover` is fine. Three in one section is a pattern. The skill uses per-paragraph and per-1000-word thresholds to avoid false positives.

### Journal-quality checks (top-5 standard)
Evaluates against published conventions of AER, QJE, Econometrica, JPE, REStud:
- **Prose register**: first-person plural "we", active voice, 15-25 word sentences, calibrated hedging
- **Results reporting**: must include table/column references, coefficient + standard error, magnitude interpretation
- **Section structure**: canonical introduction formula (hook, question, results preview, mechanism, contribution, roadmap)
- **Contribution framing**: enumerated, anchored to specific prior papers, specific about nature
- **Formatting**: standard errors in parentheses, leading zeros, "percent" vs "percentage points"
- **Sentence variety**: flags uniform sentence/paragraph length as both AI marker and quality failure

### Economics-specific problems
- **Causal overreach**: `cause`, `drive`, `shape` without identification strategy
- **Significance without magnitude**: "positive and significant" with no coefficient or unit
- **Missing comparison baseline**: "higher" / "increased" without saying relative to what
- **Unanchored mechanism claims**: "through several channels" with no variable or model object
- **Proposal-style language**: "fills an important gap", "offers novel insights"
- **Non-standard notation**: inline p-values, `SD` abbreviation, parenthesis overload

### Structure and figures
- Results sections that read off figures without explaining why the pattern matters
- Discussion sections that re-summarize instead of adding interpretation
- Figure captions that restate conclusions instead of describing what is plotted

---

## Full Skill Output

The block below is **unedited output** from running `/academic-deai` on the three Before sentences using the current version of the skill (dual-axis scoring with top-5 journal standards).

<details>
<summary>Click to expand</summary>

**Sentence 1** (AI: 3, JQ: 2)
> "Moreover, our findings underscore that trade shocks play a pivotal role in exacerbating food insecurity -- not only through direct price transmission channels but also by undermining the resilience of vulnerable households. These results have important implications for policy design."

- Rules triggered: `Moreover` opener (ai-detection §3), `underscore` (ai-detection §1), `play a pivotal role` template (ai-detection §4 + §2), em dash (ai-detection §5.1), `not only/but also` contrast template (ai-detection §5.2), abstract-noun stacking: `resilience` + `transmission` + `channels` (ai-detection §5.4), implication template verbatim match (ai-detection §4), `exacerbating` causal overreach (ai-detection §6.1)
- JQ issues: mechanism claimed but no variable/coefficient/group named (journal-quality §2.2), no table reference (journal-quality §2.1), "vulnerable households" is vague (journal-quality §8)
- Journal-quality revision: "Trade shocks worsened food insecurity through higher prices for imported staples and by reducing the purchasing power of low-income households."

---

**Sentence 2** (AI: 3, JQ: 2)
> "This paper contributes to a more nuanced understanding of how climate variability shapes agricultural outcomes. Notably, the heterogeneous effects across food groups illuminate the multifaceted nature of dietary vulnerability in developing economies."

- Rules triggered: "contributes to a more nuanced understanding" literature template (ai-detection §4), `nuanced` + `multifaceted` very-high-risk adjectives (ai-detection §2), `Notably` opener (ai-detection §3), `illuminate` (ai-detection §1), `shapes` causal overreach (ai-detection §6.1), abstract-noun stacking: `vulnerability` + `nature` + `outcomes` (ai-detection §5.4), proposal-style language (ai-detection §6.5)
- JQ issues: no food group named, no magnitude, no direction (journal-quality §2.2), contribution not specific — names no method, data, or prior paper (journal-quality §5.2)
- Journal-quality revision: "Climate variability affects agricultural outcomes unevenly across food groups: cereals and perishable crops show larger declines than legumes or dairy in our sample of developing economies."

---

**Sentence 3** (AI: 3, JQ: 2)
> "Interestingly, the coefficient on tariff reduction is positive and significant, lending support to the hypothesis that trade liberalization fosters dietary diversity through enhanced market access."

- Rules triggered: `Interestingly` opener (ai-detection §3), "positive and significant" without coefficient (ai-detection §6.2), `lending support to the hypothesis` over-hedged template (ai-detection §4), `fosters` high-risk verb (ai-detection §1), unanchored mechanism: "enhanced market access" names no variable (ai-detection §6.4)
- JQ issues: no coefficient or standard error (journal-quality §2.1), no table/column reference (journal-quality §2.2), "positive and significant" is top red flag in economics results reporting (journal-quality §9)
- Journal-quality revision: "Tariff reductions are associated with higher dietary diversity, consistent with greater access to imported food varieties in the treated regions."

---

**Density summary:**
- Em dashes: 1
- AI transitions: 3/3 sentences open with Moreover, Notably, Interestingly
- Very-high-risk adjectives: nuanced, multifaceted
- Abstract-noun stacking: 2 instances
- Non-standard notation: no coefficient reported in sentence 3

</details>

---

## Install

```bash
npx skills add ALLBLUEUK/academic-deai
```

This installs to Claude Code, Codex, Cursor, and other supported agents automatically.

Or with Claude Code plugin system:

```bash
claude plugin marketplace add ALLBLUEUK/academic-deai
claude plugin install academic-deai@academic-deai
```

### Update

```bash
# reinstall to get the latest version
npx skills remove academic-deai -g
npx skills add ALLBLUEUK/academic-deai -g -y
```

## Usage

In Claude Code or Codex:

```
/academic-deai
```

Then paste your text, or point to a file:

```
/academic-deai
Review the Results section in draft-v3.tex
```

## License

MIT
