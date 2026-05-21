# research-weekly-report

一个用于整理中文科研周报的 Codex Skill。它可以根据 Notion 中的科研推进记录、科研工作记录、既往周报、实验日志、文献笔记或用户草稿，生成结构清晰、便于复制到 Notion 的三段式科研周报。

## 适用场景

适合以下任务：

- 从 Notion 科研推进记录整理周报；
- 根据零散实验记录、文献笔记、截图和草稿生成周报；
- 将已有周报压缩、润色或改成更清晰的结构；
- 检查周报是否适合提交；
- 保持不同周报之间的术语、风格和内容边界一致。

## 输出结构

周报固定使用三段式：

```markdown
## 1. 本周工作

### 1.1 工作项标题

## 2. 后续计划

### 2.1 计划项标题

## 3. 相关问题

### 3.1 问题标题
```

如果直接写入 Notion，标题应使用 Notion 折叠标题块；如果只是输出可复制草稿，则使用干净 Markdown 标题，不输出 `{toggle=true}` 这类伪语法。

## 核心特点

- **优先贴近用户草稿**：如果用户已经写了草稿，Skill 会在原结构上补齐和优化，而不是重写成另一套叙事。
- **避免重复旧周报内容**：会参考既往周报和科研工作记录，区分历史背景和本周新增工作。
- **强调实际产出**：优先写清楚本周具体做了什么、产出了什么、对论文或项目有什么意义。
- **支持图表整理**：可以整理文献调研表、实验结果表、术语替换表、技术框架图和结果截图说明。
- **控制学术化扩写**：不会主动添加用户材料中没有出现的论文、算法名、实验结论或问题方向。
- **检查输出格式**：避免未闭合代码块、伪 Notion 语法、伪表格和标题层级损坏。

## Notion 工作流

如果用户没有提供材料，Skill 会优先检索以下 Notion 内容：

1. `科研推进`：目标周的主要工作记录；
2. `科研工作记录`：长期背景、术语边界和研究主线；
3. `周报`：最新周报的写法、详略程度和内容取舍；
4. 用户指定日期、关键词或页面。

如果 Notion 不可用或用户未授权，则会要求用户粘贴记录或提供导出文件。

## 使用示例

### 生成本周周报

```text
用 research-weekly-report 整理 5.20 周报。
材料来源优先 Notion 的科研推进、科研工作记录和最新周报。
固定三段式：本周工作、后续计划、相关问题。
以本周新增工作为主，避免重复上周已经写过的内容。
```

### 根据草稿优化

```text
用 research-weekly-report 帮我优化下面这版周报。
以我的草稿为主，只补齐表达和结构，不要重写成另一套论文综述。
标题保持三段式，输出可复制到 Notion 的 Markdown 草稿。
```

### 检查是否可以提交

```text
用 research-weekly-report 检查这版周报能不能交。
只给结论和最重要的修改建议，不要生成多个版本。
```

## 写作原则

- 使用中文，必要的论文名、模型名、指标名保留英文；
- 不夸大工作量，不把计划写成已完成；
- 不编造文献、指标、实验结果或结论；
- 本周工作优先写实际新增动作和产出；
- 后续计划要写具体动作和验证目标；
- 相关问题要写成需要讨论、验证或决策的问题；
- 有明确来源的图表优先引用或整理，没有来源不硬加；
- 不使用未闭合代码块承载流程图。

## 目录结构

```text
research-weekly-report/
├── SKILL.md
├── agents/
│   └── openai.yaml
└── references/
    ├── notion-workflow.md
    ├── terminology.md
    ├── weekly-template.md
    └── writing-rules.md
```

## 安装方式

### Windows 一行安装

```powershell
git clone https://github.com/cs-xdu-dev-001/weekly-report-skills.git `
  "$env:USERPROFILE\.codex\skills\research-weekly-report"
```

安装后重新打开 Codex，在对话中直接提到 `research-weekly-report` 即可触发该 Skill。

### macOS / Linux 一行安装

```bash
git clone https://github.com/cs-xdu-dev-001/weekly-report-skills.git \
  "$HOME/.codex/skills/research-weekly-report"
```

### 更新 Skill

Windows:

```powershell
cd "$env:USERPROFILE\.codex\skills\research-weekly-report"
git pull
```

macOS / Linux:

```bash
cd "$HOME/.codex/skills/research-weekly-report"
git pull
```

### 手动安装

也可以下载本仓库 ZIP，解压后将整个目录放到 Codex skills 目录下：

```text
Windows: %USERPROFILE%\.codex\skills\research-weekly-report
macOS/Linux: ~/.codex/skills/research-weekly-report
```

确保目录中直接包含 `SKILL.md`，而不是多套一层目录。

### 卸载

删除对应目录即可：

```text
Windows: %USERPROFILE%\.codex\skills\research-weekly-report
macOS/Linux: ~/.codex/skills/research-weekly-report
```

## 注意事项

- 该 Skill 不包含具体项目数据、实验结果或私有论文内容；
- 如果需要使用 Notion，需要当前 Codex 环境已经启用 Notion 相关能力并获得授权；