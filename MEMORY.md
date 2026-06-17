---
summary: "OI-Agent-Teacher 项目笔记 — 本地运行环境与依赖"
read_when:
  - 首次配置或排查运行问题
---

## 运行平台

- **主平台**: Claude Code（当前）
- **兼容平台**: Cherry Studio（`.claude/` 标准目录结构）
- **原始平台**: QwenPaw（早期版本，配置已迁移到 `CLAUDE.md`）

## Skills 依赖

只列本仓库维护的 5 个教学核心技能。文档/浏览器/定时任务等通用技能由宿主环境注入，依赖见各官方技能说明。

### 需要系统工具

| Skill | 依赖 |
|-------|------|
| 搬题助手 | g++ (C++17) |

### 不需要额外依赖

备课、命题工坊、积步、ppt-creator、problem-set-generator

## 路径约定

- Skills 定义: `.claude/skills/<name>/SKILL.md`
- 资源文件: `resource/<name>/`（脚本、模板、参考文档）
- 学生数据: `memory/student/`（每次会话后自动更新）

## 注意

- `.claude/skills/` 中混入的 `find-skills` 和 `skill-creator` 是 Claude Code 环境自动注入的，不属于本项目
- 原始 QwenPaw 版本的 `skills/` 目录已迁移：SKILL.md → `.claude/skills/`，资源文件 → `resource/`
