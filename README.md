# Adaptive Learning Mentor

> 一个面向 Roo Code 的「动态自适应学习导师」Agent Skill，用于把大模型变成高强度、可迭代、能主动摸底和纠偏的学习教练。

## 项目简介

`adaptive-learning-mentor` 是一个可直接导入 Roo Code 的 Skill 项目。它提供了一套「动态自适应学习导师」提示词框架，核心目标是：

- 不按传统教材线性灌输知识，而是从反直觉、关键、可迁移的底层逻辑切入。
- 通过 2-3 个场景化问题动态摸底，判断学习者当前认知水平。
- 用日常生活、商业逻辑、通识科学或游戏机制做降维类比，降低理解门槛。
- 对正确理解快速跳过，对错误理解精准指出偏差并补齐核心逻辑。
- 根据学习者反馈自动升级难度，循环推进。
- 在学习接近完成时输出结构化长篇笔记，便于沉淀到 NotebookLM 等知识库中。

本项目适合用于：

- 学习一本书的核心思想。
- 快速掌握某个技术领域、商业领域或专业领域的底层框架。
- 让 AI 从「回答问题」升级为「主动诊断、主动提问、主动训练」的导师。
- 在 Roo Code 中沉淀可复用的个人学习工作流。

## 项目结构

```text
.
├── README.md
├── LICENSE
└── adaptive-learning-mentor/
    └── SKILL.md
```

说明：

- `README.md`：项目说明与 Roo Code 使用教程。
- `LICENSE`：MIT 开源许可证。
- `adaptive-learning-mentor/SKILL.md`：核心 Skill 文件，包含动态自适应学习导师提示词框架。

## Skill 能力概览

当前 Skill 的核心配置位于 `adaptive-learning-mentor/SKILL.md`，主要包含以下模块：

1. **角色设定与定位**
   - 将 AI 设定为指定领域或指定书籍的资深导师。
   - 使用直接、高密度、少废话的沟通风格。
   - 以达成具体学习目标为导向。

2. **核心执行规则**
   - 跳过冗长前言和线性章节讲解。
   - 通过场景题动态摸底。
   - 强制使用降维类比解释抽象概念。
   - 对认知偏差进行精准反馈。
   - 根据学习者水平自动提速和升级难度。

3. **终止机制与全景收网**
   - 当 AI 判断学习者掌握核心底层逻辑后，主动停止提问。
   - 输出完整结构化总结，包含底层逻辑、推演过程、思维导图或分析框架。

4. **知识沉淀提醒**
   - 学习结束后提醒用户保存最终笔记到 NotebookLM 或其他知识管理工具。

## 快速开始

### 1. 准备环境

你需要：

- 已安装 Visual Studio Code。
- 已安装 Roo Code 插件。
- 已配置可用的大模型服务，例如 OpenAI、Anthropic、OpenRouter、DeepSeek、Google Gemini、本地模型或其他 Roo Code 支持的 Provider。
- 已克隆或下载本项目。

### 2. 获取项目

如果你使用 Git，可以执行：

```bash
git clone https://github.com/ShiDongZhao/adaptive-learning-mentor
cd adaptive-learning-mentor
```

如果你是直接下载 ZIP 文件，解压后用 VS Code 打开项目根目录即可。

### 3. 在 VS Code 中打开项目

1. 打开 VS Code。
2. 点击 `File` → `Open Folder...`。
3. 选择本项目根目录。
4. 确认目录中包含：
   - `README.md`
   - `LICENSE`
   - `adaptive-learning-mentor/SKILL.md`

## Roo Code 插件详细使用教程

> 说明：Roo Code 的界面和菜单名称可能会随版本变化。以下流程以常见的 Roo Code 工作方式为准。如果你的界面略有不同，请优先参考插件当前版本的实际按钮名称。

### 一、安装 Roo Code 插件

1. 打开 VS Code。
2. 点击左侧扩展图标，或使用快捷键：
   - Windows / Linux：`Ctrl + Shift + X`
   - macOS：`Cmd + Shift + X`
3. 在扩展市场搜索：`Roo Code` 或 `Roo-Code`。
4. 找到 Roo Code 插件后点击 `Install`。
5. 安装完成后，VS Code 左侧活动栏通常会出现 Roo Code 图标。

### 二、配置模型 Provider

Roo Code 需要连接一个可用的大模型服务。常见配置流程如下：

1. 点击 VS Code 左侧 Roo Code 图标，打开 Roo Code 面板。
2. 进入设置或 Provider 配置页面。
3. 选择你要使用的模型服务，例如：
   - OpenAI
   - Anthropic
   - OpenRouter
   - DeepSeek
   - Google Gemini
   - Ollama / LM Studio 等本地模型
4. 填入对应的 API Key、Base URL、模型名称等信息。
5. 保存配置。
6. 发送一条简单消息测试模型是否可用，例如：

```text
你好，请用一句话介绍 Roo Code。
```

如果模型正常回复，说明基础配置完成。

### 三、理解 Roo Code 的几种常用模式

Roo Code 通常支持不同工作模式，用于处理不同类型任务。常见模式包括：

| 模式 | 适合场景 |
| --- | --- |
| Code | 编写、修改、重构代码 |
| Architect | 规划方案、设计架构、拆解复杂任务 |
| Ask | 提问、解释、阅读代码、不直接修改文件 |
| Debug | 排查错误、分析日志、定位问题 |
| Orchestrator | 拆分复杂任务并协调多个子任务 |

使用本项目的学习导师 Skill 时，建议优先使用：

- `Ask`：只想学习、提问、训练认知，不希望 AI 修改项目文件。
- `Code`：希望 AI 帮你安装、调整、维护 Skill 文件或 README。
- `Orchestrator`：希望围绕某个大目标制定长期学习计划。

### 四、什么是 Roo Code Skill

Skill 可以理解为一套可复用的 AI 行为说明书。它通常包含：

- Skill 名称。
- Skill 描述。
- 触发或使用场景。
- AI 在该场景下应遵循的角色、流程和约束。

本项目中的 `adaptive-learning-mentor/SKILL.md` 就是一个 Skill 文件。它定义了一个「动态自适应学习导师」，让 AI 按照固定教学框架与你互动。

### 五、导入本项目 Skill

不同版本 Roo Code 对 Skill 的管理入口可能不同，常见方式有两类。

#### 方式 A：通过 Roo Code Skills 管理界面导入

1. 打开 VS Code。
2. 打开 Roo Code 面板。
3. 找到 Skills、Prompts、Marketplace 或类似入口。
4. 选择导入本地 Skill。
5. 选择本项目中的目录：

```text
adaptive-learning-mentor/
```

6. 确认导入后，Roo Code 应能识别其中的 `SKILL.md`。
7. 在对话中启用或调用 `adaptive-learning-mentor`。

#### 方式 B：复制到 Roo Code 的本地 Skills 目录

如果你的 Roo Code 版本使用本地 Skills 目录管理 Skill，可以将整个目录复制到 Roo Code 指定的 Skills 路径中：

```text
adaptive-learning-mentor/
└── SKILL.md
```

复制后建议：

1. 重启 VS Code，或刷新 Roo Code。
2. 打开 Roo Code 的 Skill 列表。
3. 确认能看到 `adaptive-learning-mentor`。
4. 在会话中选择或调用该 Skill。

> 注意：不同系统、不同 Roo Code 版本的 Skills 路径可能不同。请以插件设置页或官方文档显示的路径为准。

### 六、在 Roo Code 中调用学习导师

导入 Skill 后，你可以在 Roo Code 对话中这样启动：

```text
使用 adaptive-learning-mentor 这个 Skill。
我想学习《原则》这本书，目标是能把它的方法论用于个人决策和团队管理。
请直接开始第一轮动态摸底。
```

也可以学习一个技术领域：

```text
使用 adaptive-learning-mentor 这个 Skill。
领域：React 性能优化。
目标：达到能独立诊断中大型前端项目性能瓶颈，并设计优化方案的水平。
请从反直觉的核心问题开始摸底。
```

还可以学习一个商业主题：

```text
使用 adaptive-learning-mentor 这个 Skill。
领域：商业模式设计。
目标：能分析一个产品为什么赚钱、为什么不赚钱，以及如何重构增长飞轮。
请开始高强度场景化测试。
```

### 七、推荐提问模板

你可以直接复制下面模板到 Roo Code：

```text
使用 adaptive-learning-mentor 这个 Skill。

【学习对象】：填写书名、领域、课程、技术或问题域
【当前水平】：零基础 / 入门 / 有实践经验 / 中高级
【最终目标】：填写你希望达到的能力水平
【约束条件】：例如时间有限、只要实战、不想听概念、希望多举例

请不要按教材目录讲解。
请先用 2-3 个场景问题摸底，然后根据我的回答进行纠偏、降维类比和递进训练。
```

示例：

```text
使用 adaptive-learning-mentor 这个 Skill。

【学习对象】：大模型 Agent 设计
【当前水平】：会写 Prompt，但缺少系统方法
【最终目标】：能独立设计一个可执行、可调试、可复用的 Agent 工作流
【约束条件】：不要泛泛解释概念，要用真实产品场景测试我

请开始第一轮摸底。
```

### 八、一次完整学习流程示例

1. 你提出学习目标：

```text
我想学习数据库索引优化，目标是能看懂慢查询并设计索引方案。
```

2. Roo Code 根据 Skill 发起摸底问题：

```text
场景 1：一个订单表有 1000 万行，查询经常按 user_id 和 created_at 筛选，你会怎么建索引？为什么？
场景 2：为什么有了索引，某些查询仍然很慢？
场景 3：联合索引里字段顺序为什么会影响性能？
```

3. 你回答自己的判断。
4. AI 判断你理解正确和错误的部分。
5. 对错误部分用生活类比讲透。
6. AI 自动提高难度，继续下一轮。
7. 达到掌握阈值后，AI 输出完整结构化总结。
8. 你把最终笔记保存到 NotebookLM、Obsidian、Notion 或其他知识库。

### 九、如何让学习效果更好

建议你在使用时遵守以下原则：

- 不要只说「教我 XX」，而要说明目标水平。
- 尽量暴露自己的真实判断，不要害怕答错。
- 让 AI 多用场景题测试你，而不是直接讲概念。
- 如果觉得解释太抽象，要求它换成更日常的类比。
- 如果觉得太简单，要求它提高难度并加入真实案例。
- 每轮结束后，让 AI 总结你的认知盲区。
- 学完后一定要求输出结构化笔记。

可用追加指令：

```text
你刚才讲得太抽象，请换成一个普通人也能懂的生活类比。
```

```text
提高难度，不要再问定义题，直接用真实业务场景考我。
```

```text
请指出我回答里最危险的误区，只讲关键逻辑。
```

```text
请把目前为止的内容整理成可保存到 NotebookLM 的结构化笔记。
```

### 十、常见问题

#### 1. Roo Code 没有识别到 Skill 怎么办？

可以检查：

- `SKILL.md` 是否位于 `adaptive-learning-mentor/` 目录下。
- `SKILL.md` 顶部是否存在 YAML Front Matter，例如 `name` 和 `description`。
- 是否导入了整个 `adaptive-learning-mentor/` 文件夹，而不是只导入了单个文件。
- 是否需要重启 VS Code 或刷新 Roo Code。
- 当前 Roo Code 版本是否支持 Skills 功能。

#### 2. AI 没有按导师流程执行怎么办？

可以在对话中明确提醒：

```text
请严格按照 adaptive-learning-mentor 的 Skill 规则执行：先场景化摸底，再纠偏，再用降维类比解释，最后递进下一轮。
```

#### 3. 回答太啰嗦怎么办？

可以追加：

```text
压缩废话，只保留核心判断、错误原因和一个精准类比。
```

#### 4. 问题太简单怎么办？

可以追加：

```text
把难度提升到专业实战水平，用真实复杂场景测试我。
```

#### 5. 我想学习一本书，应该怎么说？

推荐格式：

```text
使用 adaptive-learning-mentor 这个 Skill。
我想学习《纳瓦尔宝典》，目标是能把财富、杠杆、判断力这些概念迁移到自己的职业决策中。
请不要按章节讲，直接用场景题测试我的直觉。
```

## 自定义与二次开发

你可以直接编辑 `adaptive-learning-mentor/SKILL.md` 来调整导师风格。

常见可调整项：

- 语气强度：更温和或更犀利。
- 摸底问题数量：从 2-3 个改为 3-5 个。
- 学习终止标准：从掌握 90% 调整为 80% 或 95%。
- 总结格式：增加表格、行动清单、复盘问题或 Anki 卡片。
- 知识沉淀工具：从 NotebookLM 改为 Obsidian、Notion、Logseq 等。

修改后建议重新打开 Roo Code 会话，确保新规则生效。

## 版本说明

当前 Skill 名称：`adaptive-learning-mentor`

当前框架版本：`Adaptive Learning Mentor V3.2`

## 许可证

本项目使用 MIT License。你可以自由使用、复制、修改、分发和二次开发，但需要保留原始版权与许可证声明。

## 致谢

本项目旨在把 Roo Code 从代码助手扩展为个人学习系统的一部分。通过 Skill 化的方式，你可以把高质量学习方法沉淀为可复用、可迁移、可持续迭代的 AI 工作流。
