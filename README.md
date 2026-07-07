<div align="center">

# MVP Validator Skill

### 在投入开发资源之前，先验证产品值不值得做

**Expert-level AI agent skill that validates product ideas BEFORE committing development resources.**

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Skill Type](https://img.shields.io/badge/Type-WorkBuddy%20Skill-blue)](https://www.codebuddy.cn)
[![Modules](https://img.shields.io/badge/Modules-6-green)](#workflow)
[![Platform](https://img.shields.io/badge/Platform-WorkBuddy-orange)](https://www.codebuddy.cn)

### 如果这个技能对你有帮助，请点个 Star 支持一下！

### If this skill helps you, please give it a Star!

[Star 历史](https://star-history.com/#664991498-prog/mvp-validator-skill) | [报告问题](../../issues) | [功能建议](../../issues/new)

---

</div>

## 这是什么 / What is this?

**MVP Validator** 是一个可复用的 [WorkBuddy](https://www.codebuddy.cn/docs/workbuddy/Overview) AI 智能体技能，用于在大规模投入开发资源之前，深度验证产品价值主张。它输出结构化的 6 模块评估框架，回答三个关键问题：

**MVP Validator** is a reusable [WorkBuddy](https://www.codebuddy.cn/docs/workbuddy/Overview) skill that performs deep product validation analysis before you invest development resources. It produces a structured 6-module assessment answering three critical questions:

1. **值得做吗？** —— 市场需求、竞品格局分析
2. **能做吗？怎么做？** —— 技术可行性、开源方案调研
3. **最小投入路径是什么？** —— 分阶段 MVP 计划、ROI 预测

---

## 为什么要用它 / Why use it?

大多数产品失败不是因为技术方向错误，而是**在验证产品是否值得做之前就已经花了钱**。这个技能将验证过程系统化：

Most product failures happen not because the technology is wrong, but because **money is spent before validating whether the product is worth building**. This skill systematizes the validation process:

| 阶段 | 费用 | 说明 |
|------|------|------|
| Phase 0 技术验证 | **¥0** | AI 生成概念验证代码 |
| Phase 1 用户验证 | **¥0** | 调研真实用户需求 |
| Phase 2 MVP 产品 | 低 | 确认需求后再投入 |
| Phase 3 完整产品 | 中高 | 验证留存后再扩展 |

每个阶段都有 **Go/No-Go 门槛** —— 如果验证失败，以最小损失止损。

---

## 工作流程（6 模块）/ Workflow (6 Modules)

| 模块 | 做什么 | 核心输出 |
|------|--------|---------|
| **1. 需求解读** | 剥离术语，提炼核心价值链，分析"负空间"（文档没要求的） | 一句话价值链 + 头号技术风险 |
| **2. 技术可行性** | 拆解功能层，评估难度，区分 AI/人工分工 | 技术栈推荐 + 架构图 |
| **3. 竞品分析** | 联网搜索竞品，定位二维矩阵，识别市场空白 | 竞品矩阵 + 市场空白判断 |
| **4. 开源调研** | 搜索 GitHub/PyPI/npm，评估许可证，提出组合架构 | 开源工具对比 + 自研vs魔改分析 |
| **5. 递进投资** | 设计四阶段递进投资框架，设 Go/No-Go 门槛 | Keep/Cut 清单 + 期望损失计算 |
| **6. ROI 预测** | 三档费用 × 三场景收入 + 盈亏平衡 + 风险矩阵 | ROI 图表 + 战略建议 |

### 最终输出

6 个模块完成后，技能会输出：

1. **一句话判断**："这个产品值得 / 不值得 / 有条件值得投入，因为……"
2. **3 个可执行的下一步**
3. **最大单一风险** 及其应对方案
4. **推荐投资档位** 和预期周期

---

## 安装 / Installation

### 方式 A：通过 WorkBuddy 技能管理器安装

1. 下载 `mvp-validator.zip`
2. 打开 WorkBuddy > Skills > Import
3. 选择 zip 文件导入

### 方式 B：手动安装

```bash
# 克隆仓库
git clone https://github.com/664991498-prog/mvp-validator-skill.git

# 复制到 WorkBuddy 技能目录
cp -r mvp-validator-skill ~/.workbuddy/skills/mvp-validator
```

---

## 使用方法 / Usage

安装后，技能会在以下触发词出现时自动启动：

- **中文**："MVP验证"、"产品价值验证"、"开发前评估"、"竞品分析"、"开源方案调研"、"ROI预测"、"这个产品值不值得做"
- **English**: "validate this product idea", "should I build this", "MVP validation", "product feasibility assessment"

或者直接提供一个需求文档（PDF/Word/MD），然后说"评估一下"。

### 示例

```
用户: "这是一份产品需求PDF，帮我验证值不值得做"

AI: [自动触发 MVP Validator 技能]
    → 模块1: 读取并解读需求
    → 模块2: 评估技术可行性
    → 模块3: 联网搜索 10+ 竞品
    → 模块4: 找到 3 个开源替代方案
    → 模块5: 设计四阶段投资计划
    → 模块6: 计算 3 种场景 ROI
    → 最终: "有条件值得投入。建议从 Phase 0（零成本）开始..."
```

---

## 技能结构 / Skill Structure

```
mvp-validator/
├── SKILL.md                          # 核心流程指令（6 模块）
└── references/
    └── mvp-detailed-guide.md         # 详细模板、搜索模式、ROI 计算框架
```

## 参考文档包含 / Reference Guide Contents

`references/mvp-detailed-guide.md` 文件包含：

- **第1节**: 需求解读模板（价值链、负空间检查清单）
- **第2节**: 技术可行性模板（AI/人工分工、架构图指南）
- **第3节**: 竞品分析搜索模式（按领域分类的关键词模板）
- **第4节**: 开源许可证风险指南（MIT 到 AGPL 对比、AGPL 缓解策略）
- **第5节**: MVP 投资框架详情（阶段门槛、Keep/Cut 决策、期望损失计算）
- **第6节**: ROI 计算模板（成本模型、收入模型、盈亏平衡、风险矩阵）
- **第7节**: 输出格式指南（可视化图表要求、报告生成）

---

## 兼容性 / Compatibility

- **平台**: [WorkBuddy](https://www.codebuddy.cn/docs/workbuddy/Overview)（AI 智能体桌面应用）
- **技能格式**: 标准 WorkBuddy Skill（SKILL.md + references）
- **依赖**: 无（使用 WorkBuddy 内置工具：WebSearch、WebFetch、show_widget）

---

## 许可证 / License

MIT License - 自由使用、修改和分发。

---

## 贡献 / Contributing

发现 Bug 或想改进验证框架？欢迎提 PR！

1. Fork 本仓库
2. 创建功能分支（`git checkout -b feature/improvement`）
3. 提交修改（`git commit -m 'Add some improvement'`）
4. 推送到分支（`git push origin feature/improvement`）
5. 发起 Pull Request

---

## 致谢 / Acknowledgments

本技能通过真实产品验证会话开发，包括：
- 音乐教育 CV 平台可行性评估
- 10+ OMR（光学乐谱识别）产品竞品分析
- 开源方案调研（HOMR、oemer、Audiveris、OSMD）
- 三档成本/收入场景 ROI 建模

---

<div align="center">

### 如果这个技能对你有帮助

### 请点个 Star 支持开发者

**If this skill helps you, please give it a Star!**

</div>
