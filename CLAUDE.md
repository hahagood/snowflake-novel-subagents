# CLAUDE.md

本项目是**雪花写作法 Claude Code Subagent 工具集**，基于兰迪·英格曼森（Randy Ingermanson）的雪花写作法，通过 15 个专业 subagent + 1 个编排器实现 AI 辅助小说创作的完整流程。

## 项目结构

```
.claude/agents/
├── snowflake-orchestrator.md          # 编排器（项目管理入口）
├── story-concept-designer.md          # 步骤1：故事核心概念设计
├── three-act-architect.md             # 步骤2：三幕式结构设计
├── character-storyline-weaver.md      # 步骤3：人物故事线编织
├── synopsis-writer.md                 # 步骤4：故事概要撰写
├── character-profiler.md              # 步骤5：人物档案构建
├── outline-expander.md                # 步骤6：大纲扩展
├── character-bible-creator.md         # 步骤7：人物宝典编纂
├── scene-planner.md                   # 步骤8：场景规划
├── scene-designer.md                  # 步骤9：场景设计
├── manuscript-writer.md               # 步骤10：正文撰写
├── genre-specialist.md                # 辅助：类型专家
├── dialogue-master.md                 # 辅助：对话大师
├── pacing-controller.md               # 辅助：节奏控制师
├── consistency-checker.md             # 辅助：一致性检查师
└── editor-reviewer.md                 # 辅助：编辑审阅师

templates/                             # 输出模板（只读参考）
├── step01-one-sentence.md
├── step02-one-paragraph.md
├── step03-character-summary.md
├── step04-synopsis.md
├── step05-character-synopsis.md
├── step06-full-outline.md
├── step07-character-bible.md
├── step08-scene-list.md
├── step09-scene.md
├── step10-first-draft.md
├── project-status.md
└── README.md
```

## 标准项目输出目录

每个小说项目使用以下统一目录结构：

```
{小说项目}/
└── snowflake/
    ├── 项目状态.md                    # 进度追踪（编排器管理）
    ├── 01-一句话概括.md               # Step 1 输出
    ├── 02-一段式概括.md               # Step 2 输出
    ├── 03-人物简介.md                 # Step 3 输出
    ├── 04-故事梗概.md                 # Step 4 输出
    ├── 05-人物小传.md                 # Step 5 输出
    ├── 06-完整大纲.md                 # Step 6 输出
    ├── 07-人物宝典.md                 # Step 7 输出
    ├── 08-场景清单.md                 # Step 8 输出
    ├── 09-场景描写/                   # Step 9 输出（目录）
    │   ├── 场景01.md
    │   ├── 场景02.md
    │   └── ...
    └── 10-正文/                       # Step 10 输出（目录）
        ├── 第01章.md
        ├── 第02章.md
        └── ...
```

**路径约定：** 所有 agent 使用 `{项目路径}/snowflake/` 作为根目录，`{项目路径}` 由编排器在初始化时确定。

## Agent 调用指南

### 推荐入口

使用 `snowflake-orchestrator` 作为项目管理入口，它会：
- 初始化项目目录结构
- 追踪各步骤进度
- 验证步骤前置条件
- 推荐下一步操作和辅助 agent

### 步骤依赖关系

```
Step 1 → Step 2 → Step 3 → Step 4 → Step 5 → Step 6 → Step 7 → Step 8 → Step 9 → Step 10
                     ↓                   ↓                  ↓
                  Step 4 需要          Step 6 需要        Step 8 需要
                  1+2+3 一致          4+5 一致           6+7 一致
```

注意：雪花写作法鼓励迭代，修改前面步骤时应检查后续受影响的步骤。

### 辅助 Agent 使用时机

| 辅助 Agent | 推荐使用步骤 | 触发时机 |
|-----------|-------------|---------|
| genre-specialist | 1、2、4、6 | 需要类型规范指导时 |
| dialogue-master | 7、9、10 | 打磨角色对话时 |
| pacing-controller | 6、8、9 | 调整叙事节奏时 |
| consistency-checker | 4、6、8 完成后 | 阶段性一致性检查 |
| editor-reviewer | 10 完成后 | 完稿审阅 |

## 质量评分标准

所有步骤输出采用统一的 1-5 分评分制：

| 分数 | 含义 |
|------|------|
| 5 | 优秀——专业水准，无需修改 |
| 4 | 良好——小幅调整即可 |
| 3 | 合格——基本达标，有改进空间 |
| 2 | 不足——存在明显问题 |
| 1 | 需重做——未达到基本要求 |

- **Step 1：** 3 个维度（有趣度、突兀度、合理度），满分 15，合格 12
- **Steps 2-10：** 各 4 个维度，满分 20，合格 14
- **辅助 agent：** 各 3 个维度，满分 15，合格 10

## 标点规范

本项目所有中文行文统一使用全角中文标点：

- 逗号：`，`（非 `,`）
- 句号：`。`（非 `.`）
- 冒号：`：`（非 `:`）
- 问号：`？`（非 `?`）
- 叹号：`！`（非 `!`）
- 分号：`；`（非 `;`）
- 顿号：`、`

**例外保留半角的情况：**
- YAML frontmatter 中的标点
- 代码块和文件路径
- 英文文本
- Markdown 格式符号（`#`、`-`、`|` 等）

## 开发规范

### Agent 文件结构

每个 agent 文件应包含以下段落（按顺序）：

1. YAML frontmatter（`name`、`description`、`tools`）
2. 标题与角色定位
3. 核心职责 / 工作流程
4. 文件输入与输出（核心 agent）
5. 输出格式（含模板引用）
6. 质量评分
7. 工作流集成（辅助 agent）

### 模板使用

`templates/` 目录下的模板文件为只读参考，agent 应读取模板内容并据此生成输出文件。模板中的 `{占位符}` 在实际输出中替换为具体内容。
