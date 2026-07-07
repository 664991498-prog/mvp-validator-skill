# MVP Validator - Detailed Guide

This reference provides detailed templates, search patterns, and calculation
frameworks for each module of the MVP validation workflow.

## Section 1: Requirement Interpretation Templates

### Core Value Chain Template

```
User does X -> System does Y -> User gets Z
```

Fill in X, Y, Z in one sentence. Example:
- "User uploads sheet music image -> System identifies notes via CV and colors
  them by pitch -> User downloads a colored PDF"

### Negative Space Analysis Checklist

Ask these questions about the requirement document:
1. Does it ask for user accounts/authentication?
2. Does it ask for payment/billing?
3. Does it ask for real-time interaction (playback, live feedback)?
4. Does it ask for multi-user collaboration?
5. Does it ask for mobile/native app (vs. web only)?
6. Does it ask for data persistence beyond session?
7. Does it ask for admin/management dashboard?

If the answer to most is "no", the product may be a utility tool, not a
platform. This affects ROI significantly.

### Technical Risk Assessment Matrix

| Risk Level | Criteria | Example |
|-----------|----------|---------|
| Low | Standard CRUD, well-documented APIs | User registration, form submission |
| Medium | Integration of established libraries | PDF generation, image processing |
| High | Custom algorithm requiring domain expertise | CV pipeline, NLP model training |
| Very High | Novel research, no prior art | New ML architecture, proprietary algorithm |

## Section 2: Technology Feasibility Templates

### Functional Layer Breakdown

For any product, identify layers:
1. **Input layer**: How users interact (upload, type, click)
2. **Processing layer**: Core logic (AI/ML, computation, transformation)
3. **Output layer**: What users receive (file, visualization, report)
4. **Infrastructure**: Hosting, deployment, scaling

### AI vs. Human Work Split

| Work Type | AI Capability | Human Needed For |
|-----------|---------------|-----------------|
| Boilerplate code (CRUD, UI, config) | 95% | Edge case review |
| API integration | 90% | Auth/edge case testing |
| Algorithm framework | 70% | Parameter tuning, precision validation |
| Domain-specific logic | 50% | Expert verification |
| Real-world testing | 20% | Full testing required |
| UI/UX polish | 60% | User testing, iteration |

### Architecture Diagram Guidelines

When generating architecture diagrams via `show_widget`:
- Use layered architecture (top-down or left-right)
- Color-code by layer type (AI-generated = green, human-tuned = orange, critical
  risk = red)
- Show data flow arrows between components
- Include technology names in each box
- Use 680px width viewBox for SVG

## Section 3: Competitive Analysis Search Patterns

### General Search Keyword Templates

```
"[product domain] [core feature] tool product"
"[product domain] [core feature] software commercial"
"[Chinese equivalent] 商业产品"
"[Chinese equivalent] 工具"
```

### Domain-Specific Search Examples

**Music Technology:**
```
"music score colorization tool CV optical music recognition product"
"optical music recognition OMR commercial product"
"乐谱识别着色软件 商业产品"
"colored music notation software"
```

**Fintech:**
```
"personal finance management app AI"
"budget tracking tool commercial"
"个人财务管理 应用 商业产品"
```

**EdTech:**
```
"adaptive learning platform AI"
"intelligent tutoring system product"
"智能教育平台 商业产品"
```

**HealthTech:**
```
"health monitoring app computer vision"
"medical image analysis tool commercial"
"医疗影像分析 软件"
```

### Competitor Data Collection Checklist

For each competitor, fetch and record:
1. Product name and URL
2. Pricing model (free/freemium/subscription/one-time)
3. Price point (monthly/annual)
4. Platform (Web/iOS/Android/Desktop)
5. Key features (list top 5)
6. Technology approach (if discernible)
7. Target user segment
8. Notable limitations
9. Last updated / maintenance status

### Market Gap Identification

After collecting all competitors:
1. List all capability dimensions (e.g., "CV recognition", "auto-coloring",
   "real-time playback", "export format")
2. Create a matrix: competitors (rows) x capabilities (columns), mark
   check/cross
3. Find capability combinations where ALL competitors have at least one cross
4. Validate: is this gap because (a) no one thought of it, (b) it's
   technically hard, or (c) there's no demand?
5. If (a) or (b), it's a real opportunity. If (c), it's a trap.

## Section 4: Open-Source License Risk Guide

### License Compatibility Matrix

| License | Commercial Use | Modification | Distribution | Network Service | Risk Level |
|---------|---------------|-------------|-------------|----------------|------------|
| MIT | Yes | Yes | Yes (with notice) | No restriction | Safe |
| Apache 2.0 | Yes | Yes | Yes (with notice) | No restriction | Safe |
| BSD-3 | Yes | Yes | Yes (with notice) | No restriction | Safe |
| LGPL | Yes | Limited | Yes (with source) | No restriction | Low Risk |
| GPL v3 | Yes (with source) | Yes | Yes (with source) | No restriction | Medium Risk |
| AGPL v3 | Yes (with source) | Yes | Yes (with source) | **MUST open source** | High Risk |
| Proprietary | No | No | No | N/A | Prohibited |

### AGPL Mitigation Strategies

If the best open-source tool uses AGPL:
1. **Strategy A**: Contact author for commercial license
2. **Strategy B**: Use as external CLI tool (call via subprocess, not import)
   - Legal basis: AGPL applies to derivative works, not separate programs
   - Risk: Gray area, depends on integration depth
3. **Strategy C**: Find MIT/Apache alternative (possibly lower quality)
4. **Strategy D**: Self-build the component (highest cost, zero license risk)

### Open-Source Evaluation Checklist

For each candidate tool:
1. [ ] Star count (popularity indicator)
2. [ ] Last commit date (maintenance indicator)
3. [ ] License type (commercial compatibility)
4. [ ] Installation method (pip/npm/Docker/source)
5. [ ] API quality (can it be called as a library?)
6. [ ] Documentation quality
7. [ ] Precision/accuracy metrics (if applicable)
8. [ ] Community activity (issues, PRs, discussions)
9. [ ] Dependencies (transitive dependency risk)
10. [ ] Platform support (Windows/Mac/Linux/Docker)

## Section 5: MVP Investment Framework Details

### Phase Gate Criteria Templates

#### Phase 0: Tech Verification
- **Input**: Requirement document
- **Activity**: AI generates proof-of-concept code for the riskiest technical
  component
- **Output**: 3-5 test cases with results
- **Gate**: "Does the core technology produce acceptable results on test
  inputs?"
  - GO: Results are 70%+ of target quality
  - NO-GO: Results below 50% - technology not viable or too expensive
  - PARTIAL: 50-70% - proceed but flag risk, consider alternatives

#### Phase 1: User Validation
- **Input**: Phase 0 results
- **Activity**: Show results to 20+ target users (interview or survey)
- **Questions to ask**:
  1. "Does this solve a real problem for you?"
  2. "How do you currently solve this problem?"
  3. "Would you pay for this? How much?"
  4. "What's missing that would make you definitely pay?"
- **Gate**: "Do 30%+ of interviewees express willingness to pay?"
  - GO: 30%+ willing to pay at proposed price
  - NO-GO: <10% willing to pay - rethink value proposition
  - PARTIAL: 10-30% - refine target segment and retry

#### Phase 2: MVP Product
- **Input**: Validated demand from Phase 1
- **Activity**: Build minimum viable product (Streamlit/FastAPI + basic UI)
- **Scope**: Core feature only, no auth/payment/admin
- **Gate**: "Do early users retain after 1 month?"
  - GO: 30%+ retention at 1 month
  - NO-GO: <10% retention - product-market fit not achieved
  - PARTIAL: 10-30% - iterate on UX, reduce friction

#### Phase 3: Full Product
- **Input**: Validated MVP from Phase 2
- **Activity**: Add Docker, CI/CD, user system, payment, polish
- **Gate**: "Is unit economics positive?"
  - GO: LTV > 3x CAC
  - NO-GO: LTV < CAC - business model not viable
  - PARTIAL: 1x < LTV/CAC < 3x - optimize acquisition or pricing

### Keep/Cut Decision Framework

**Keep if**: The feature is essential to validate the core hypothesis.
**Cut if**: The feature would be "nice to have" but doesn't change the
validation conclusion.

Common cuts in MVP:
- User authentication (use hardcoded demo users)
- Payment integration (manual billing for early adopters)
- Docker/CI-CD (local development is fine)
- Advanced UI frameworks (Streamlit/Gradio suffices)
- Database (SQLite or in-memory for MVP)
- Microservices (monolith is fine)
- Automated testing (manual testing for MVP)
- Monitoring/logging (basic prints suffice)

### Expected Loss Calculation

```
All-in approach:
  Expected loss = Total_investment x failure_probability

MVP approach:
  Expected loss = Phase_0_cost x P(Phase_0_fails)
                + Phase_1_cost x P(Phase_0_passes) x P(Phase_1_fails)
                + Phase_2_cost x P(Phase_0+1_pass) x P(Phase_2_fails)
```

Typical failure probabilities for new products:
- Phase 0: 20% (tech doesn't work)
- Phase 1: 30% (no demand)
- Phase 2: 20% (no retention)
- Phase 3: 10% (no unit economics)

Example: Total investment 150K CNY
- All-in expected loss: 150K x 40% = 60K
- MVP expected loss: 0 x 20% + 0 x 30% + 50K x 20% = 10K
- Savings: 83% reduction in expected loss

## Section 6: ROI Calculation Templates

### Cost Model Template

| Cost Category | Conservative | Standard | Premium |
|--------------|-------------|----------|---------|
| Lead Developer (monthly) | X | Y | Z |
| Second Developer (monthly) | X | Y | Z |
| Part-time Consultant (monthly) | X | Y | Z |
| Subtotal monthly | | | |
| Social insurance (~15%) | | | |
| Monthly total | | | |
| Cloud infrastructure (total) | | | |
| Other (domain, SSL, samples) | | | |
| **Grand total** | | | |

### Revenue Model Template

| Scenario | Users | Price | Annual Revenue | Assumption |
|----------|-------|-------|---------------|------------|
| Pessimistic | 50 | 99 | 5K | Low awareness, novelty fades |
| Realistic | 500 | 199 | 100K | Moderate marketing, organic growth |
| Optimistic | 2000 | 299 | 600K | Platform features, high retention |

### Break-Even Calculation

```
Break-even months = Total Investment / Monthly Revenue

Monthly Revenue = Users x Price / 12
```

For staged investment:
```
Break-even (staged) = (Phase_2_cost + Phase_3_cost) / Monthly Revenue
```

### ROI Formula

```
ROI (N years) = (N_year_revenue - Total_investment) / Total_investment x 100%
```

### Risk Matrix Template

| Risk | Probability | Impact (cost) | Impact (time) | Mitigation |
|------|------------|--------------|--------------|------------|
| [Risk 1] | High/Med/Low | +X CNY | +Y weeks | [Action] |
| [Risk 2] | | | | |
| [Risk 3] | | | | |
| [Risk 4] | | | | |
| [Risk 5] | | | | |

### Strategic Insight Template

Always include this assessment at the end:

```
Is this product a "feature" or a "platform"?

Feature (single function):
  - Lower ROI, user retention challenge
  - Consider per-use pricing instead of subscription
  - ROI tends toward pessimistic scenario

Platform (core tech enables multiple features):
  - Higher ROI, multiple revenue streams
  - Subscription model viable
  - ROI can reach optimistic scenario
  - Recommend: identify 3-4 features the core technology enables
```

## Section 7: Output Formatting Guidelines

### Visual Diagram Requirements

Use `show_widget` with appropriate modules:
- **Architecture diagrams**: Load `diagram` module, use layered SVG
- **Team/org charts**: Load `diagram` module, use hierarchical SVG
- **Timeline/Gantt**: Load `chart` module, use horizontal bar chart
- **ROI/break-even**: Load `chart` module, use line chart with 3 revenue lines
- **Competitive matrix**: Load `diagram` module, use 2D scatter/positioning SVG

All SVGs should use viewBox starting with "0 0 680".

### Report Generation

If user requests a Word document:
1. Use the `docx` skill to generate a .docx file
2. Structure: Executive Summary -> 6 Modules -> Risk Matrix -> Recommendation
3. Include all visual diagrams as images
4. Target length: 15-30 pages depending on complexity
