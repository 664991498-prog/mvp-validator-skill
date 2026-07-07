# MVP Validator Skill

> Expert-level AI agent skill that validates product ideas **before** committing development resources. Avoid wasted investment with a structured 6-module assessment framework.

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Skill Type](https://img.shields.io/badge/Type-WorkBuddy%20Skill-blue)](https://www.codebuddy.cn)
[![Modules](https://img.shields.io/badge/Modules-6-green)](#workflow)

## What is this?

**MVP Validator** is a reusable [WorkBuddy](https://www.codebuddy.cn/docs/workbuddy/Overview) skill that performs deep product validation analysis before you invest development resources. It produces a structured 6-module assessment answering three critical questions:

1. **Is this worth building?** (market demand, competitive landscape)
2. **Can it be built, and how?** (technical feasibility, open-source solutions)
3. **What is the minimum viable investment path?** (phased MVP plan, ROI prediction)

## Why use it?

Most product failures happen not because the technology is wrong, but because **money is spent before validating whether the product is worth building**. This skill systematizes the validation process:

- **Phase 0-1 cost: ~$0** (AI generates proof-of-concept code and surveys users)
- **Phase 2 cost: low** (build MVP only after demand is confirmed)
- **Phase 3 cost: medium-high** (scale only after retention is proven)

Each phase has a **Go/No-Go gate** — if validation fails, you stop with minimal loss.

## Workflow (6 Modules)

| Module | What it does | Key Output |
|--------|-------------|------------|
| **1. Requirement Interpretation** | Strip away jargon, find the core value chain, identify negative space (what's NOT asked for) | Core value chain + top technical risk |
| **2. Technical Feasibility** | Break down into functional layers, assess difficulty, split AI vs. human work | Technology stack recommendation + architecture diagram |
| **3. Competitive Analysis** | Search the web for competing products, position them on a 2D matrix, identify market gaps | Competitor table + market gap analysis |
| **4. Open-Source Research** | Search GitHub/PyPI/npm for existing tools, evaluate licenses, propose combination architecture | Open-source tool comparison + self-build vs. adapt analysis |
| **5. MVP Investment Framework** | Design 4-phase progressive investment with Go/No-Go gates | Keep/Cut lists + expected loss calculation |
| **6. ROI Prediction** | 3-tier cost model x 3 revenue scenarios, break-even analysis, risk matrix | ROI chart + strategic recommendation |

### Final Output

After all 6 modules, the skill produces:
1. **One-sentence verdict**: "This product is worth / not worth / conditionally worth investing in, because..."
2. **Top 3 actionable next steps**
3. **Single biggest risk** and its mitigation
4. **Recommended investment tier** and expected timeline

## Installation

### Option A: Install via WorkBuddy Skill Manager

1. Download `mvp-validator.zip` from the [Releases page](../../releases)
2. Open WorkBuddy > Skills > Import
3. Select the zip file

### Option B: Manual install

```bash
# Clone this repo
git clone https://github.com/YOUR_USERNAME/mvp-validator-skill.git

# Copy to your WorkBuddy skills directory
cp -r mvp-validator-skill ~/.workbuddy/skills/mvp-validator
```

## Usage

Once installed, the skill auto-triggers when you say things like:

- **English**: "validate this product idea", "should I build this", "MVP validation", "product feasibility assessment"
- **Chinese**: "MVP验证", "产品价值验证", "开发前评估", "竞品分析", "开源方案调研", "ROI预测"

Or simply provide a requirement document (PDF/Word/MD) and ask for assessment.

### Example

```
User: "Here's a product requirement PDF. Can you validate whether it's worth building?"

AI: [Auto-triggers MVP Validator skill]
    → Module 1: Reads and interprets the requirement
    → Module 2: Assesses technical feasibility
    → Module 3: Searches web for 10+ competitors
    → Module 4: Finds 3 open-source alternatives
    → Module 5: Designs 4-phase investment plan
    → Module 6: Calculates ROI for 3 scenarios
    → Final: "Worth investing conditionally. Start with Phase 0 (zero cost)..."
```

## Skill Structure

```
mvp-validator/
├── SKILL.md                          # Core workflow instructions (6 modules)
└── references/
    └── mvp-detailed-guide.md         # Detailed templates, search patterns, ROI models
```

## What's in the Reference Guide

The `references/mvp-detailed-guide.md` file contains:

- **Section 1**: Requirement interpretation templates (value chain, negative space checklist)
- **Section 2**: Technology feasibility templates (AI vs. human work split, architecture diagram guidelines)
- **Section 3**: Competitive analysis search patterns (domain-specific keyword templates)
- **Section 4**: Open-source license risk guide (MIT to AGPL comparison, AGPL mitigation strategies)
- **Section 5**: MVP investment framework details (phase gate criteria, keep/cut decision framework, expected loss calculation)
- **Section 6**: ROI calculation templates (cost model, revenue model, break-even, risk matrix)
- **Section 7**: Output formatting guidelines (visual diagram requirements, report generation)

## Compatibility

- **Platform**: [WorkBuddy](https://www.codebuddy.cn/docs/workbuddy/Overview) (AI agent desktop app)
- **Skill format**: Standard WorkBuddy Skill (SKILL.md + references)
- **Dependencies**: None (uses built-in WorkBuddy tools: WebSearch, WebFetch, show_widget)

## License

MIT License - feel free to use, modify, and distribute.

## Contributing

Found a bug or want to improve the validation framework? PRs welcome!

1. Fork this repository
2. Create your feature branch (`git checkout -b feature/improvement`)
3. Commit your changes (`git commit -m 'Add some improvement'`)
4. Push to the branch (`git push origin feature/improvement`)
5. Open a Pull Request

## Acknowledgments

This skill was developed through real-world product validation sessions, including:
- Music education CV platform feasibility assessment
- Competitive analysis of 10+ OMR (Optical Music Recognition) products
- Open-source solution research (HOMR, oemer, Audiveris, OSMD)
- ROI modeling with 3-tier cost/revenue scenarios
