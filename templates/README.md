# 输出模板

本目录包含雪花写作法各步骤的结构化输出模板。

## 模板列表

| 文件 | 步骤 | 对应 Agent | 说明 |
|------|------|-----------|------|
| `step01-one-sentence.md` | 步骤1 | story-concept-designer | 一句话概括模板 |
| `step02-one-paragraph.md` | 步骤2 | three-act-architect | 一段式概括模板 |
| `step03-character-summary.md` | 步骤3 | character-storyline-weaver | 人物简介模板 |
| `step04-synopsis.md` | 步骤4 | synopsis-writer | 故事梗概模板 |
| `step05-character-synopsis.md` | 步骤5 | character-profiler | 人物小传模板 |
| `step06-full-outline.md` | 步骤6 | outline-expander | 完整大纲模板 |
| `step07-character-bible.md` | 步骤7 | character-bible-creator | 人物宝典模板 |
| `step08-scene-list.md` | 步骤8 | scene-planner | 场景清单模板 |
| `step09-scene.md` | 步骤9 | scene-designer | 单个场景描写模板 |
| `step10-first-draft.md` | 步骤10 | manuscript-writer | 第一稿写作指南 |
| `project-status.md` | — | snowflake-orchestrator | 项目状态追踪 |

## 使用方式

模板文件为**只读参考**。各 agent 在执行时会读取对应模板，将 `{占位符}` 替换为实际内容后，输出到项目的 `snowflake/` 目录下。

## 质量评分

每个模板都包含质量评分区域，采用统一的 1-5 分制：

- **步骤1：** 3 个维度，满分 15，合格线 12
- **步骤2-10：** 各 4 个维度，满分 20，合格线 14

评分由对应 agent 在完成输出后自动填写，编排器（`snowflake-orchestrator`）汇总展示。
