# 🧑‍🏫 OI-Teacher

> AI 信息学竞赛教练 —— 启发式教学，耐心引导，越用越懂孩子。

[![License](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)
[![Platform](https://img.shields.io/badge/platform-Claude%20Code%20%7C%20Cherry%20Studio-7c3aed.svg)]()

[English Version](README_en.md)

---

## 目录

- [OI-Teacher 是什么](#oi-teacher-是什么)
- [核心特色](#核心特色)
- [快速开始](#快速开始)
- [项目结构](#项目结构)
- [可用 Skills](#可用-skills)
- [知识点覆盖](#知识点覆盖)
- [记忆系统](#记忆系统)
- [参与贡献](#参与贡献)

---

## OI-Teacher 是什么

**OI-Teacher** 不是一个问答机器人。它是一个**有温度的竞赛教练**，运行在 Claude Code 或 Cherry Studio 中。

它不会直接抛出答案，而是用问题引导学生自己找到解法；它不会千篇一律，而是在每一次对话中不断了解这个孩子——从第一次打招呼，到第 50 次对话时已经能预判学生会在哪里卡壳。

> _每个孩子都是潜在的冠军，我们需要做的就是点燃他们心中的火。_

---

## 核心特色

### 🎯 启发式教学
- 不给答案，用提问引导学生自己发现解法
- 把复杂问题拆成小步骤，让每个小成功都积累信心
- 善用类比和生活例子解释抽象的算法概念

### 📈 越用越懂孩子
内置完整的记忆追踪系统，回复学生后按需更新；积步（知识沉淀技能）负责提炼知识卡片、安排间隔复习、给出画像诊断：

| 文件 | 用途 |
|------|------|
| `profile.md` | 学生画像：性格、学习风格、优势与薄弱点 |
| `knowledge_matrix.md` | 知识掌握矩阵：每个知识点的状态追踪 |
| `templates.md` | 算法模板库：模板熟练度、能否闭眼写出 |
| `error_log.md` | 错题本：错误原因分类、高频模式识别 |
| `contest_log.md` | 比赛记录：成绩、心态、赛后 upsolving 进度 |

**累积效应：** 第 1 次知道名字和目标 → 第 50 次能预判会卡在什么题上。

### 📋 智能题单与训练计划
- 根据学生水平、目标比赛、可用时间，生成个性化题单
- 入门 / 基础 / 提高 / 冲刺四阶段训练模板
- 支持 Upsolving（赛后补题）计划和模板训练计划

### 🔥 比赛策略与训练方法论
- **Upsolving 最重要：** 做过的题不复盘，等于白做；赛后补题，等于白比
- **模板建设：** 每个模板亲手敲过 3 遍以上才算数
- **刻意练习：** Consistency beats intensity —— 每天 1 小时 > 周末突击 10 小时

---

## 快速开始

### Claude Code

```bash
git clone git@github.com:alatzr/OI-Agent-Teacher.git
cd OI-Agent-Teacher
# 在项目目录下启动 Claude Code 即可自动加载 CLAUDE.md 和 .claude/skills/
```

### Cherry Studio

1. 克隆仓库到本地
2. 在 Cherry Studio 中创建 Agent，选择 OI-Teacher 目录作为工作目录
3. 系统自动识别 `.claude/` 下的所有配置和 skills

### 前置依赖

本仓库 5 个教学核心技能几乎零依赖：

- **搬题助手**：g++（C++17）
- 备课 / 命题工坊 / 积步 / problem-set-generator：无外部依赖

宿主环境注入的官方技能（docx/pdf/pptx/xlsx/浏览器等）各自有依赖，见各技能说明。

---

## 项目结构

```
OI-Teacher/
├── CLAUDE.md                       # 主配置（身份 + 教学流程 + 说话风格 + 比赛策略，唯一规则源）
├── SOUL.md                         # 说话风格展开与话术示范（CLAUDE.md 的语感补充）
├── PROFILE.md                      # 教练身份与学生资料模板
├── MEMORY.md                       # 运行时笔记
│
├── .claude/                        # Claude Code / Cherry Studio 配置
│   ├── settings.json               # 工具权限
│   └── skills/                     # 5 个教学核心 skills
│       ├── 搬题助手/                   # OJ 题目自动化生成
│       ├── 备课/                     # 讲义材料准备
│       ├── 命题工坊/                 # OI/CSP 题目创作
│       ├── 积步/                     # 知识沉淀与复习调度
│       └── problem-set-generator/   # 题单与训练计划
│
├── resource/                       # Skills 依赖的资源（脚本、模板、参考文档）
│   ├── 搬题助手/                       # 参考文档 + question 模板
│   ├── 备课/                         # references/ + assets/
│   ├── 积步/                         # 复习调度规则 + 知识卡片模板
│   └── problem_set_generator/       # knowledge_map + templates/
│
└── memory/
    ├── student/                    # 真实学生数据（隐私，不入 git，本地使用）
    │   ├── profile.md              # 学生画像
    │   ├── knowledge_matrix.md     # 知识掌握矩阵
    │   ├── templates.md            # 算法模板库
    │   ├── error_log.md            # 错题本
    │   ├── contest_log.md          # 比赛记录
    │   ├── conversation_log.md     # 对话记录（定期归档）
    │   └── INDEX.md                # 更新时序、触发与归档规则
    └── student.example/            # 干净空模板（入 git，复制为 student/ 开始使用）
```

---

## 可用 Skills

### 教学核心
| Skill | 用途 |
|-------|------|
| **搬题助手** | OJ 题目自动化生成，支持 URL/文本输入，GESP 难度判定，AI 蜜罐防作弊 |
| **备课** | 信息学奥赛讲义准备，去 AI 味，叙事设计（情绪曲线/植入-揭示/赌注阶梯） |
| **命题工坊** | OI/CSP 题目创作，注重思维深度和算法本质 |
| **积步** | 知识沉淀（知识卡片）、间隔复习调度、学习画像诊断 |
| **problem-set-generator** | 个性化题单、训练计划、Upsolving 计划、模板训练计划 |

> 文档处理（docx/pdf/pptx/xlsx）、浏览器控制、定时任务等通用能力由宿主环境（Claude Code / Cherry Studio）注入的官方技能提供，本仓库只维护上述 5 个教学核心技能。

---

## 知识点覆盖

| 阶段 | 核心内容 |
|------|---------|
| 🟢 入门 | 变量、循环、条件、数组、字符串、基础函数 |
| 🟡 基础 | 排序、二分、栈/队列、贪心、简单搜索、线性 DP |
| 🟠 提高 | 图论、最短路、MST、背包 DP、区间/树形 DP、并查集 |
| 🔴 进阶 | 高级 DP、强连通分量、线段树、KMP、数论 |
| ⚫ 冲刺 | 网络流、后缀自动机、平衡树、计算几何、博弈论 |

---

## 记忆系统

OI-Teacher 在 `memory/student/` 下维护分层记忆架构，**回复学生后**按需更新（寒暄类对话不触发）。规则见 `memory/student/INDEX.md`：

- **更新时序：** 先回复、再记忆——在同一次会话内完成，不拖到下一次
- **分级触发：** 只有学习相关的对话才写档（问知识点、做题、错题、比赛等）；寒暄/确认不写
- **按需检索：** 只读与当前话题相关的记忆条目，不全量读历史
- **定期归档：** `conversation_log.md` 按月压缩为摘要，避免越积越长

记忆内容分层：

- **学生画像** — 性格、沟通风格、优势与薄弱点
- **知识矩阵** — 每个知识点的掌握状态
- **错题本** — 错误原因分类、高频模式、复习排期
- **比赛记录** — 成绩、心态、upsolving 进度
- **对话日志** — 会话要点、下一步

> 真实学生数据写在 `memory/student/`（不入 git）；仓库提供 `memory/student.example/` 空模板供复制使用。

---

## 参与贡献

欢迎提交 Issue 和 Pull Request！

- **报告 Bug 或提出功能建议** → [Issue](https://github.com/alatzr/OI-Agent-Teacher/issues)
- **贡献代码或文档** → [Pull Request](https://github.com/alatzr/OI-Agent-Teacher/pulls)
- **想法与交流** → [Discussions](https://github.com/alatzr/OI-Agent-Teacher/discussions)

---

## 开源协议

本项目采用 [MIT License](LICENSE) 开源协议。

---

<p align="center">
  <em>不怕你不会，就怕你不敢试。</em>
</p>
