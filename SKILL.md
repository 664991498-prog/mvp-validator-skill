---
name: mvp-validator
description: "Expert-level MVP product validation skill that performs deep analysis before committing development resources. This skill should be used when evaluating a new product idea, requirement document, or business concept before investing in development. It produces a structured 6-module validation framework: requirement analysis, technical feasibility, competitive landscape, open-source solution research, MVP progressive investment plan, and ROI prediction with risk matrix. Triggers include: MVP validation, product value proposition, validate before building, product feasibility, should I build this, MVP落地框架, 产品价值验证, 开发前评估, 竞品分析, 开源方案调研, ROI预测, or any request to evaluate whether a product idea is worth investing development resources into. Also triggers when a user provides a requirement document (PDF/Word/MD) and asks for assessment before development."
agent_created: true
---

# MVP Validator

## Overview

Validate product ideas before committing development resources. This skill
produces a structured 6-module assessment that answers three questions: (1) Is
this worth building? (2) Can it be built, and how? (3) What is the minimum
viable investment path with the best risk-adjusted ROI?

## When to Use

- A user provides a requirement document, product spec, or job description and
  asks for assessment before committing to development.
- A user asks "should I build this?" or "is this product idea viable?"
- A user wants competitive analysis, open-source solution research, or ROI
  prediction for a product concept.
- A user explicitly requests "MVP validation" or "product value proposition
  validation."

## Workflow

Execute the following 6 modules **in order**. Each module builds on the previous
one. After each module, present findings to the user before continuing. Load
`references/mvp-detailed-guide.md` for detailed templates, search query
patterns, and calculation tables.

### Module 1: Requirement Interpretation

**Goal**: Understand what the product actually does, stripping away jargon.

1. If a document (PDF/Word/MD) is provided, read it fully first.
2. Summarize the core value chain in one sentence: "User does X -> System does Y
   -> User gets Z."
3. Identify explicit requirements vs. implicit assumptions.
4. List what the document does NOT ask for (negative space analysis) - these
   gaps often reveal product scope boundaries and future expansion potential.
5. Identify the single biggest technical risk.

**Output**: A concise requirement summary with core value chain, scope
boundaries, and top technical risk.

### Module 2: Technical Feasibility Assessment

**Goal**: Determine if the product can be built and with what technology.

1. Break down the product into functional layers (e.g., CV pipeline, backend
   API, frontend rendering).
2. For each layer, identify candidate technology stacks.
3. Assess build difficulty (Easy / Medium / Hard / Very Hard) for each layer.
4. Identify which layers can be AI-generated vs. which require human expertise.
5. If the user asks about a specific technology (e.g., "what is CV pipeline?",
   "why Docker?"), provide a plain-language explanation with visual diagrams.

**Output**: Technology stack recommendation with difficulty assessment and
AI-vs-human work split.

**Visual**: Generate an architecture diagram using `show_widget` (load `diagram`
module first via `read_me`).

### Module 3: Competitive Analysis

**Goal**: Map the competitive landscape and identify market gaps.

1. Search the web for competing products using `WebSearch`. Use
   `query_keyword_groups` with 3-5 keyword variants (English + Chinese) to
   broaden coverage.
2. For each competitor found, fetch detailed info via `WebFetch` to extract:
   pricing, features, platform, accuracy/quality claims.
3. Position all competitors on a 2D matrix: X-axis = one capability dimension,
   Y-axis = another capability dimension specific to the product domain.
4. Identify the **market gap**: what combination of capabilities does NO
   existing product offer?
5. Assess whether the gap represents real unmet demand or just an empty niche.

**Output**: Competitor comparison table + market gap identification.

**Visual**: Generate a competitive landscape diagram using `show_widget`.

**Search patterns**: See `references/mvp-detailed-guide.md` Section 3 for
domain-specific search keyword templates.

### Module 4: Open-Source Solution Research

**Goal**: Find existing open-source tools that can be adapted instead of
building from scratch.

1. Search GitHub, PyPI, npm for relevant open-source projects:
   - `WebSearch` with queries like "open source [domain] [technology] github"
   - `WebFetch` GitHub repo pages to extract: stars, license, last update,
     language, installation method, accuracy/precision metrics.
   - `WebFetch` PyPI/npm pages for package details.
2. For each candidate, evaluate:
   - **Precision/Quality**: Does it meet the product's quality bar?
   - **License**: AGPL/GPL = risk for commercial use; MIT/Apache/BSD = safe.
   - **Maintainability**: Can it be called as a library, or does it need
     modification?
   - **Integration effort**: How much glue code is needed?
3. Propose a **combination architecture**: which open-source tools to use for
   each layer, plus what custom code must be written.
4. Calculate effort savings: self-build vs. adapt open-source (time, cost,
   code volume, risk reduction).

**Output**: Open-source tool comparison table + recommended combination
architecture + savings analysis.

**Visual**: Generate a 3-layer combination architecture diagram using
`show_widget`.

**License risk guide**: See `references/mvp-detailed-guide.md` Section 4.

### Module 5: MVP Progressive Investment Framework

**Goal**: Design a phased investment plan with Go/No-Go gates.

Design 4 phases with clear gates:

| Phase | Goal | Typical Cost | Duration | Gate Decision |
|-------|------|-------------|----------|---------------|
| Phase 0: Tech Verification | Prove core tech works | ~0 (AI code) | 1 week | Does the core pipeline produce acceptable results? |
| Phase 1: User Validation | Confirm demand exists | ~0 | 1-2 weeks | Do 20+ target users say they would pay? |
| Phase 2: MVP Product | Build usable product | Low | 4-5 weeks | Do early users retain after 1 month? |
| Phase 3: Full Product | Scale to commercial grade | Medium-High | 8-12 weeks | Is unit economics positive? |

**Key principle**: Maximum loss if killed at each gate should decrease
exponentially. Phase 0-1 cost should be near zero.

For each phase, specify:
- What to keep (core functionality needed for validation)
- What to cut (features that don't affect the validation conclusion)
- Go/No-Go criteria (specific, measurable)
- If killed, what was lost (time + money)

**Output**: 4-phase investment plan with Go/No-Go gates and keep/cut lists.

**Visual**: Generate a progressive investment flow diagram using `show_widget`.

### Module 6: ROI Prediction and Risk Matrix

**Goal**: Quantify the financial upside and downside.

1. **Cost model**: Break down costs by category (human resources, cloud
   infrastructure, other). Provide 3 tiers: Conservative / Standard / Premium.
2. **Revenue model**: Define 3 scenarios: Pessimistic / Realistic / Optimistic.
   For each, specify: user count, pricing, annual revenue.
3. **Break-even analysis**: Calculate months to break-even for each scenario.
4. **ROI calculation**: 3-year and 5-year ROI for each scenario.
5. **Risk matrix**: List top 4-5 risks with probability, impact, and mitigation.
6. **MVP risk-hedging value**: Compare "all-in" vs "phased" expected loss.

**Key insight to highlight**: If the product is a single feature (e.g., "coloring
only"), ROI tends toward pessimistic. If the core technology serves as platform
infrastructure enabling multiple features, ROI can jump 5-10x. Always call out
this distinction.

**Output**: Cost-revenue table, break-even analysis, risk matrix, and strategic
recommendation.

**Visual**: Generate an ROI chart showing cumulative investment vs. revenue
lines for 3 scenarios using `show_widget`.

## Output Format

After completing all 6 modules, produce a **final summary** with:

1. **One-sentence verdict**: "This product is worth / not worth / conditionally
   worth investing in, because..."
2. **Top 3 actionable next steps**.
3. **Single biggest risk** and its mitigation.
4. **Recommended investment tier** (Conservative / Standard / Premium) and
   expected timeline.

If the user provided a document, offer to generate a complete Word report
covering all 6 modules.

## Important Notes

- Always search the web for competitors and open-source tools - do not rely on
  training data alone, as the landscape changes rapidly.
- Use `query_keyword_groups` in WebSearch to cover multiple angles in a single
  call.
- Always check license compatibility when recommending open-source tools for
  commercial products.
- Be honest about AI's capabilities: AI can write 70-80% of code, but precision
  tuning, real-world testing, and domain-specific validation require human
  engineers.
- Tailor all cost estimates to the user's market context (China vs.
  international, seniority levels).
- Present visual diagrams (`show_widget`) at key decision points, not just text.
