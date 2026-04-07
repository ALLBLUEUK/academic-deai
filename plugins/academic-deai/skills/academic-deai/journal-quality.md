# Top-5 Economics Journal Quality Standards

Prose, structure, and formatting conventions for AER, QJE, Econometrica, JPE, and REStud. Referenced by the main SKILL.md for journal-quality scoring.

---

## 1. Prose Style

### 1.1 Voice and person
- First-person plural "we" dominates, even for single-authored papers: "We estimate...", "We find that...", "Our results suggest..."
- Third-person reference to the paper is standard: "This paper shows...", "This paper contributes to..."
- Active voice strongly preferred: "We estimate a regression of X on Y" not "A regression was estimated."
- Passive acceptable in methods only: "Standard errors are clustered at the state level."

### 1.2 Sentence structure
- Short declarative sentences. Subject-Verb-Object with minimal subordinate clauses.
- Typical sentence length: 15-25 words. Rarely exceeds 35 words.
- Complex ideas broken across multiple sentences, not packed into one.
- Each sentence advances the argument by exactly one step — one new piece of information.
- Sentence length varies naturally (8-35 words). Uniform length is a quality failure.

### 1.3 Hedging calibration
Hedging is calibrated to claim type, not applied uniformly:

| Claim type | Appropriate hedge | Example |
|---|---|---|
| Main result | Low hedge | "We find that X increases Y by 3.2 pp." |
| Interpretive claim | Moderate hedge | "Our results suggest that..." / "The estimates are consistent with..." |
| Mechanism argument | Moderate-high hedge | "One possible mechanism is..." / "This is consistent with a model in which..." |
| Acknowledging alternatives | High hedge | "We cannot rule out that..." |
| Mechanical description | No hedge | "We regress Y on X." (not "We attempt to regress...") |

**Flag:** Generic hedging applied uniformly regardless of claim type. This is a strong AI marker AND a journal-quality failure.

### 1.4 Tense usage
- Present tense for general claims and literature: "Smith (2020) finds that..."
- Past tense for procedures: "We collected data from...", "The experiment was conducted in..."
- Present tense for own results: "We find that...", "Table 3 shows that..."

---

## 2. Results Reporting

### 2.1 Specificity requirements
Every results sentence must include:
- A specific table and column reference: "(Table 3, column 4)" or "Column (1) reports..."
- A quantitative coefficient interpretation: "The coefficient of 0.043 implies that a 10% increase in minimum wages reduces teen employment by 0.43 percentage points."
- Clear indication of what is in parentheses (standard errors, confidence intervals, t-stats)

### 2.2 Results prose pattern
The standard pattern for discussing a regression result:
1. Describe the specification: "Column (1) presents the baseline specification with state and year fixed effects."
2. Report key coefficient: "The coefficient on trade exposure is -0.12 (0.03)."
3. Interpret magnitude: "This implies that a one-standard-deviation increase in trade exposure reduces employment by 2.4 percentage points."
4. Note statistical significance: "The estimate is significant at the 1% level."
5. Compare across columns: "Adding controls in column (2) reduces the estimate slightly, from 0.043 to 0.039."

### 2.3 Economic vs statistical significance
- Always discuss economic significance, not just statistical significance.
- Translate coefficients into meaningful units: "roughly X% of the mean", "equivalent to Y dollars per household."
- Flag: "positive and significant" with no magnitude or context.

### 2.4 What NOT to do in results
- Never discuss results without table/column references
- Never use "interesting finding" or "remarkable result" (evaluative language has no place)
- Never use "large effect" or "substantial impact" without a number
- Never report significance without magnitude

---

## 3. Section Structure

### 3.1 Abstract
- AER: max 100 words (~4-5 sentences)
- QJE: max 250 words
- Econometrica: max 150 words
- REStud/JPE: ~150 words typical

**Structure:** Motivation (brief, 1 sentence) → What the paper does (1 sentence) → Main findings (2-3 sentences with specific numbers) → Implication (optional, 1 sentence).

**Rules:**
- Over half of abstract sentences (>50%) should describe results
- Specific point estimates appear in roughly half of top-5 abstracts
- No citations in abstracts (waste of space)
- No undefined acronyms
- Simpler words and shorter sentences in abstracts

### 3.2 Introduction (4-8 pages, untitled in AER)
The canonical introduction formula (Head/Bellemare):

1. **Hook** (1-2 paragraphs): Broad fact, policy puzzle, or empirical regularity. Frame a major problem, then narrow.
2. **Question** (1 paragraph): Exactly what the paper does. "In this paper, we estimate the effect of X on Y using Z." Crystal clear.
3. **Results preview** (3-4 paragraphs, ~25-30% of introduction): Main findings with specific numbers. Readers should be able to cite the paper after reading only the introduction.
4. **Mechanism/interpretation** (1-2 paragraphs): What explains the results?
5. **Contribution** (1-3 paragraphs): Position relative to existing literature. Enumerated. Specific about nature of contribution.
6. **Roadmap** (1 paragraph): "The remainder of the paper is organized as follows..." This is formulaic and acceptable.

**Flag:** Introduction that buries the research question past page 2. Results preview without specific numbers. Contribution claims without naming specific prior papers.

### 3.3 Related Literature
- Often NOT a separate section in top-5 papers — integrated into introduction's contribution paragraphs.
- When standalone, titled "Related Literature" (not "Literature Review" — the latter sounds like a student paper).
- Organized thematically, not chronologically.
- Each strand connects to the paper's contribution: what gap exists.
- Standard phrasing: "Our paper is most closely related to...", "We build on the work of...", "In contrast to [Author], we..."

**Flag:** Literature that surveys without connecting to contribution. "Literature Review" as section title.

### 3.4 Data
- Sources, sample construction, variable definitions.
- Table 1 is almost always summary statistics.
- Sample restrictions justified.
- Standard phrasing: "We construct our sample by...", "Our main outcome variable is...", "Summary statistics are presented in Table 1."

### 3.5 Empirical framework
- Estimating equation(s) in precise mathematical notation.
- Identification strategy discussed.
- Threats to identification addressed.
- Verbal interpretation alongside math: "The coefficient of interest is β, which captures the effect of X on Y."

**Flag:** Methods that read like a textbook tutorial rather than a paper-specific description.

### 3.6 Results
- Tables discussed in order (Table 2, Table 3...).
- Each table gets its own subsection or paragraph group.
- Pattern per table: specification → key coefficient → magnitude interpretation → significance → robustness comparison across columns.

**Flag:** Results paragraphs that merely narrate figures without interpreting why patterns matter.

### 3.7 Robustness
- Alternative specifications, different samples, placebo tests, different clustering, alternative functional forms.
- Often summarized: "Our results are robust to [list]."
- Detailed robustness tables increasingly in online appendix.

### 3.8 Conclusion (1-2 pages)
- Short. Titled "Conclusion" or "Concluding Remarks."
- Structure: restate question and main finding (1-2 sentences) → key results summary → limitations (honest, brief) → policy implications (hedged) → future research (specific, not vague).
- Does NOT introduce new evidence or arguments.
- Limitations discussed honestly but briefly, often with mitigating factor.
- Future research: specific. "An important question is whether these effects extend to [specific context]." Not "more research is needed."

**Flag:** Conclusion that introduces new arguments. Conclusion longer than 2 pages. Vague future research directions.

---

## 4. Paragraph Structure

### 4.1 Topic sentence first
Almost every paragraph opens with a claim or framing statement, not throat-clearing.

**Good openers:**
- A claim or finding: "We find that X has a significant effect on Y."
- A framing statement: "A key concern with our identification strategy is..."
- A brief transition: "We now turn to the question of heterogeneity."
- A factual statement: "Between 2000 and 2015, manufacturing employment fell by 25%."

**Bad openers (flag):**
- "It is important to note that..."
- "It is widely known that..."
- "It goes without saying that..."
- "In the previous section, we showed that... In this section, we will show that..." (too much meta-narration)

### 4.2 Paragraph discipline
- One idea per paragraph. Enforced rigorously in top-5 papers.
- Typical length: 4-8 sentences.
- Supporting evidence follows the topic sentence.
- Final sentence often transitions or provides interpretation.
- Paragraph length varies naturally. Uniform paragraph length is a red flag.

### 4.3 Transitions
- Minimal. Section headings do most transition work.
- Within sections, transitions are brief: "We now turn to...", "Next, we examine...", "Having established X, we investigate Y."
- No heavy connective tissue between paragraphs.
- **Flag:** "In the previous section, we showed that... In this section, we will show that..."

---

## 5. Contribution Framing

### 5.1 How top-5 papers frame contributions
- Direct and enumerated: "This paper makes three contributions."
- Relative to specific papers: "Unlike Autor (2003), who studies X, we focus on Y."
- Specific about nature: "better data", "cleaner identification", "first estimates of X", "new mechanism", "novel theoretical prediction."
- Common formula: "To the best of our knowledge, this is the first paper to..."
- Additive: "We contribute to the growing literature on X by..."

### 5.2 Contribution red flags (flag these)
- Vague: "important contribution to our understanding"
- Inflated: "revolutionizes", "groundbreaking", "fills a crucial gap"
- Not anchored: contribution claimed without naming what prior work missed
- Generic: "sheds new light on" without specifying what the new light is

---

## 6. Formatting Conventions

### 6.1 Tables
- Horizontal rules only (top, bottom, header separator). No vertical rules. No shading.
- Portrait orientation only.
- Maximum ~9 columns including row headings.
- Panels labeled "Panel A:", "Panel B:".
- Variable names are descriptive words, not Stata codes.
- Dependent variable stated in title or column header.
- Notes below table: general notes → source → significance levels → lettered footnotes.
- All table footnotes end with a period (JPE rule).

Must report:
- Number of observations (N)
- R-squared (or pseudo-R-squared)
- Mean of dependent variable (increasingly standard)
- Fixed effects included (Yes/No rows)
- What is in parentheses (standard errors)
- Clustering level

### 6.2 Statistical reporting
- Standard errors in parentheses beneath coefficients (dominant convention).
- AER officially discourages asterisks; prefers reporting standard errors only.
- When asterisks used: * p<0.10, ** p<0.05, *** p<0.01.
- Leading zeros required: 0.357, never .357.
- 2-4 significant digits for coefficients.
- "Percent" vs "percentage points" used precisely (these are different quantities).

### 6.3 Figures
- Vector graphics preferred (PDF, EPS).
- Axis labels descriptive (not variable codes).
- Grayscale-friendly designs preferred.
- Panel labels: "(a)", "(b)" or "Panel A", "Panel B".
- Caption states: what is plotted, sample, statistic, error bar definition.
- Caption does NOT: restate conclusion, argue policy, read like slide notes.

### 6.4 Heading structure
- AER: Introduction has NO heading. Major sections in Roman numerals (I, II, III). Subsections in capital letters (A, B, C).
- QJE/REStud: Arabic numerals (1, 2, 3) with subsections (1.1, 1.2).
- Econometrica: Arabic numerals with subsections.
- JPE: Roman numerals (Chicago style).

### 6.5 Citations
- Author-date system across all five journals.
- In-text: "Smith (2020)" or "(Smith 2020)" or "(Smith 2020; Jones 2021)."
- Multiple citations in chronological order.
- 1-3 authors: list all. 4+ (AER: 5+): first author et al.

---

## 7. Journal-Specific Tendencies

| Journal | Tendency |
|---|---|
| AER | Broadest scope; accessible prose; emphasis on economic significance; no heading on introduction |
| QJE | Highly polished prose; longer introductions; "big idea" papers; strong narrative arc |
| Econometrica | Most mathematical; theorem-proof structure; notation-heavy; supplemental appendix max 25 pages |
| JPE | Chicago tradition; compact efficient writing; strong data replication requirements |
| REStud | Strict page limits (45 pages total); technically rigorous; both theory and empirics |

---

## 8. Positive Markers (presence indicates journal quality)

1. Specific table/column references in results discussion
2. Quantitative coefficient interpretation with units ("implies a 3.2 pp increase")
3. Calibrated hedging varying by claim type
4. Present tense for results, past for procedures
5. Varied sentence length (8-35 word range across a page)
6. Topic sentences that make claims, not meta-statements
7. Canonical section structure (hook → question → results → mechanism → contribution → roadmap)
8. Standard errors in parentheses with clear labeling
9. Leading zeros on all decimals
10. Disciplinary shorthand used naturally (IV, DiD, FE, RDD)
11. First-person plural "we" as default voice
12. One idea per paragraph, 4-8 sentences
13. Contributions enumerated and anchored to specific prior papers
14. Mechanism discussion: evidence → interpretation → alternatives
15. Economic significance discussed alongside statistical significance

---

## 9. Negative Markers (presence indicates quality failure)

### Vocabulary failures
- "delve into" — never appears in top-5 papers
- "it is important to note that" — filler
- "crucial", "pivotal", "groundbreaking" — hyperbolic
- "in today's world", "in the modern economy" — vague framing
- "various", "numerous", "a plethora of" — imprecise quantifiers
- "utilize" instead of "use"
- "Firstly/Secondly/Thirdly" instead of "First/Second/Third"
- "in order to" instead of "to"
- "whether or not" instead of "whether"
- "basically/essentially/fundamentally" — filler adverbs
- "this study aims to" — off-register for top-5

### Structural failures
- Standalone "Literature Review" section (should be "Related Literature" or integrated into introduction)
- Research question buried past page 2 of introduction
- Results discussed without table/column references
- Conclusion that introduces new arguments
- Excessive bullet points in running text
- Sections too short (<2 paragraphs) or too long (>15 pages without subsections)
- Footnotes longer than 3 sentences

### Tone failures
- Excessive uniform hedging: "tentatively suggest that preliminary results might possibly indicate"
- Insufficient hedging: "We prove that X causes Y" in observational study
- Evaluative adjectives: "interesting finding", "remarkable result"
- Emotional language: "Sadly, unemployment rose"
- Grandiose claims: "revolutionizes our understanding"
- Rhetorical questions (almost never in top-5)
- Exclamation marks (never)

### Uniformity failures (both AI marker and quality failure)
- Uniform sentence length throughout
- Uniform paragraph length throughout
- Perfectly parallel structures repeated mechanically
- Synonym cycling: "effect/impact/influence" in rotation
- Generic hedging applied uniformly

---

## 10. Standard Phrases Whitelist

These phrases are common in published top-5 papers. Do NOT flag them.

### Results
- "We find that..."
- "Our results suggest that..."
- "The estimates are consistent with..."
- "The point estimate implies..."
- "The coefficient is statistically significant at the X percent level."
- "The magnitude implies that..."
- "Column (1) reports results from..."
- "The dependent variable in all columns is..."
- "Results are robust to..."
- "Adding controls in column (X) reduces the estimate slightly."

### Methods
- "We exploit variation in..."
- "We instrument for X using Z..."
- "Conditional on [controls]..."
- "In our preferred specification..."
- "Standard errors, clustered at the [level], are reported in parentheses."
- "We include [entity] and [time] fixed effects."
- "We regress Y on X."

### Contribution
- "This paper makes [N] contributions."
- "To the best of our knowledge..."
- "We contribute to the literature on X by..."
- "Unlike [Author], who studies X, we focus on Y."
- "We provide the first estimates of..."
- "The remainder of the paper is organized as follows."

### Mechanism and interpretation
- "One possible mechanism is..."
- "This is consistent with a model in which..."
- "A natural interpretation is that..."
- "An alternative explanation is that... However, this seems unlikely because..."
- "We cannot rule out that..."
- "The evidence indicates that..."

### Limitations
- "Our analysis is subject to several limitations."
- "The results should be interpreted with caution because..."
- "We cannot rule out the possibility that... though the robustness checks in Section X suggest this is unlikely."

### Transitions (brief, structural)
- "We now turn to..."
- "Next, we examine..."
- "Having established X, we investigate Y."

---

## 11. Limitations Discussion Standard

Limitations in top-5 papers follow a specific pattern:
- Honest but not apologetic
- Specific about what the limitation is
- Each limitation often paired with a mitigating factor
- Brief: 1-3 sentences per limitation
- Constructive: lead to specific future research suggestions

**Good:** "We cannot rule out the possibility that unobserved confounders drive our results, though the robustness checks in Section V suggest this is unlikely."

**Bad (too apologetic):** "A major limitation of our study is that we were unable to control for every possible confounder, which means our results should be interpreted with extreme caution."

**Bad (too defensive):** "Despite what critics might say, our identification strategy is sound."
