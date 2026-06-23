# 本地记忆与记录系统

本文件定义 Life Coach skill pack 的可选本地记录层。目标不是一开始建立很多文件，而是让 agent 在长期使用中逐渐更懂用户：先稳定记录，再从重复经验中提炼洞察，必要时再拆分。

默认方案使用本地 Markdown 文件，不要求数据库、Notion、待办软件或 MCP。读者可以先用纯文件跑通，再按自己的工具栈改造成外部连接，例如待办事项接滴答清单，愿景接 Notion，长期笔记接 Obsidian。

## 核心原则

1. **先少后多**：一开始只建核心文件，不急着拆很多画像。
2. **单一事实源**：同一条稳定信息只维护在一个主文件，不在多个地方复制。
3. **先记录，再提炼**：单次观察先放每日记录或复盘；多次出现后再沉淀为长期规律。
4. **写入前确认**：长期画像、价值观、身份描述、敏感信息、外部工具操作，写入前先向用户确认。
5. **能不拆就不拆**：只有某类内容持续增长、被频繁单独读取、或让 `user.md` 变得臃肿时，才拆成新文件。

## 推荐最小目录

先从这套结构开始：

```text
life-coach-data/
├── profile/
│   ├── user.md
│   └── life-compass.md
├── planning/
│   ├── weekly-plan.md
│   └── daily-plan.md
├── projects/
│   └── projects.md
├── habits/
│   └── habit-tracker.md
├── reviews/
│   └── review-log.md
├── memory/
│   ├── long-term.md
│   └── daily/
│       └── YYYY-MM-DD.md
└── integrations/
    └── tools.md
```

公开仓库不应包含真实用户数据。若在仓库内创建 `life-coach-data/`，应确保它被 `.gitignore` 排除。

## 核心文件职责

| 文件 | 职责 | 不放什么 |
|---|---|---|
| `profile/user.md` | 用户稳定底图：作息、固定承诺、可用窗口、沟通偏好、精力线索、执行/拖延线索 | 项目流水、每日计划、单次情绪、未经确认的长期结论 |
| `profile/life-compass.md` | 愿景、价值、人生 8+1、阶段主题、不做什么、人生实验 | 每日任务、短期情绪、未确认的使命宣言 |
| `projects/projects.md` | 项目、等待、暂停、以后、已完成或放弃 | 单步任务流水 |
| `planning/daily-plan.md` | 今日计划、实际记录、偏离和校准 | 长期人格判断 |
| `planning/weekly-plan.md` | 本周主题、关键成果、容量、周复盘 | 过细的每日流水 |
| `reviews/review-log.md` | 周/月/项目复盘，记录偏离、有效策略、下一轮调整 | 直接替代长期画像 |
| `memory/daily/YYYY-MM-DD.md` | 当天原始事实、状态、行动、候选洞察 | 长期结论 |
| `memory/long-term.md` | 跨文件综合洞察、通用策略、索引 | 第二份用户画像 |
| `integrations/tools.md` | 外部工具、MCP/API、读写规则 | 用户生活事实 |

## user.md 的边界

`profile/user.md` 是用户的稳定底图，不是所有记忆的总仓库。它适合记录：

- **现实角色与稳定限制**：工作/学习状态、照护责任、通勤、地点约束、长期健康或环境限制。
- **基本作息与固定承诺**：工作日/周末节律、固定会议、运动、睡眠窗口、可自由支配时段。
- **沟通偏好与雷区**：喜欢表格还是简短总结，讨厌被催还是喜欢提醒，哪些表达会带来羞耻感。
- **精力线索**：常见高/低能量窗口、恢复方式、透支信号。先简要记录在 user.md；只有内容变多再拆到 `profile/energy-profile.md`。
- **执行与拖延线索**：常见启动阻力、有效启动方式、反效果方法。先简要记录在 user.md；只有反复积累后再考虑拆成专项画像。

判断句：如果这条信息会影响很多计划和对话，而且短期内不常变化，就可以写进 `user.md`。如果只是今天发生、这周尝试、一次情绪或一个项目细节，不写进 `user.md`。

## memory 的边界

`memory/` 不是另一套 profile。

- `memory/daily/` 是原始记录和候选洞察。它回答：“今天实际发生了什么？”
- `memory/long-term.md` 是跨文件综合洞察和索引。它回答：“这些分散记录合在一起，说明了什么？”

如果一条信息能归入 `profile/user.md` 或 `profile/life-compass.md`，不要再复制到 `memory/long-term.md`。`long-term` 最多写索引，例如：

```markdown
- 启动阻力的稳定记录见 `profile/user.md#执行与拖延线索`。
- 价值与阶段主题见 `profile/life-compass.md`。
```

## 何时拆分新文件

不要一开始就拆。满足以下任意两条，再考虑拆分：

- 某一节已经超过约 10 条稳定记录，`user.md` 变得难扫。
- 某类信息经常被单独读取，例如每次计划都要读精力规律。
- 这类信息有独立更新节奏，例如每月校准精力画像。
- 这类信息已经形成稳定结构，例如“触发线索 -> 反应 -> 有效策略”。
- 用户明确希望单独维护。

常见拆分方向：

- `profile/energy-profile.md`：当精力规律已经多次被验证，并且计划时需要频繁读取。
- `profile/execution-profile.md`：当拖延、启动阻力和有效启动方式积累较多。
- 互动偏好专项文件：当用户对沟通、提醒、追踪方式有很多明确偏好时，再由用户决定是否拆出。

拆分后要遵守单一事实源：从 `user.md` 中保留一句索引，不再复制全文。

## 启动时读取什么

不要为了读取而读取。简单问题直接回答；涉及延续上下文、计划、复盘、习惯或日程时，再读取对应记录。

### 默认读取

在需要连续陪伴时，读取：

1. `profile/user.md`：稳定个人情况、作息、偏好、精力与执行线索。
2. `memory/long-term.md`：跨文件综合洞察和索引。
3. `memory/daily/YYYY-MM-DD.md`：今天和昨天的状态、行动、偏离。

### 按场景读取

| 场景 | 读取 |
|---|---|
| 人生方向、价值观、阶段选择 | `profile/life-compass.md` |
| 安排今天、明天、本周 | `profile/user.md`、`planning/weekly-plan.md`、`planning/daily-plan.md`、`projects/projects.md`、外部日历/待办摘要 |
| 项目拆解和优先级 | `projects/projects.md`、`profile/life-compass.md`、`planning/weekly-plan.md` |
| 拖延、启动困难、反复失败 | `profile/user.md` 中的执行线索、`reviews/review-log.md`、相关项目和日计划；需要综合判断时再读 `memory/long-term.md` |
| 习惯设计 | `habits/habit-tracker.md`、`profile/user.md` |
| 周/月/项目复盘 | `planning/weekly-plan.md`、`planning/daily-plan.md`、`reviews/review-log.md`、`projects/projects.md` |
| 工具接入或数据来源不清 | `integrations/tools.md` |

## 写入规则

### 每次收尾的记录检查

计划、拖延应对、习惯设计和复盘结束前，agent 应做一次简短检查：

1. **稳定底图**：这次是否确认了作息、固定承诺、沟通偏好、精力线索或执行线索？如果是，候选写入 `profile/user.md`。
2. **方向变化**：这次是否确认了价值、阶段主题、人生领域或不做什么？如果是，候选写入 `profile/life-compass.md`。
3. **运行记录**：这次是否只是今天/本周的实际、偏离或尝试？如果是，写入 `planning/*`、`reviews/review-log.md` 或 `memory/daily/*`。
4. **长期洞察**：这次是否形成了跨多个文件都适用的综合洞察或通用策略？如果是，候选写入 `memory/long-term.md`。
5. **是否需要拆分**：某一类记录是否已经多到影响阅读？如果是，建议用户拆分，而不是自动创建新文件。

### 事实、假设、洞察分开

- **事实**：用户明确说过，或工具中已经存在的数据。
- **假设**：agent 为了推进计划做出的临时估计，必须标注“暂时假设”。
- **洞察**：经过对话确认的理解。
- **规律**：多次复盘后稳定出现的模式，优先写入现有文件；只有超过拆分阈值，才建议拆新文件。

### 写入前确认

以下内容写入前应先向用户确认：

- 人生价值、身份描述、长期愿景。
- 对用户性格、模式、关系的总结。
- 健康、心理、关系、财务等敏感信息。
- 会影响外部工具的操作，例如创建日历块、修改任务截止、归档项目。

可以直接写入的内容：

- 用户刚刚确认的计划。
- 明确的日程草案和日终实际记录。
- 用户要求记录的偏好、策略或复盘结论。

### 不记录什么

- 未经确认的心理诊断、人格标签或病理判断。
- 对他人的隐私细节，除非它直接影响用户行动且用户要求保留。
- 一次性情绪宣泄中的强烈措辞，除非用户确认它是长期模式。
- 可能伤害用户安全的敏感信息，除非有明确用途和保护方式。
- 密码、密钥、身份证件、银行卡等高敏感信息。

## 模板

本仓库在 `templates/` 目录下提供可复制的空模板。建议先复制最小核心模板，后续确有需要再增加拆分文件。

| 记录类型 | 模板路径 | 使用建议 |
|---|---|---|
| 用户画像 | [`templates/profile/user.md`](../templates/profile/user.md) | 必备 |
| 人生罗盘 | [`templates/profile/life-compass.md`](../templates/profile/life-compass.md) | 需要愿景/长期方向时使用 |
| 日计划 | [`templates/planning/daily-plan.md`](../templates/planning/daily-plan.md) | 做日程时使用 |
| 周计划 | [`templates/planning/weekly-plan.md`](../templates/planning/weekly-plan.md) | 做周计划时使用 |
| 项目清单 | [`templates/projects/projects.md`](../templates/projects/projects.md) | 有多步项目时使用 |
| 习惯追踪 | [`templates/habits/habit-tracker.md`](../templates/habits/habit-tracker.md) | 需要习惯实验时使用 |
| 复盘记录 | [`templates/reviews/review-log.md`](../templates/reviews/review-log.md) | 做复盘时使用 |
| 长期记忆 | [`templates/memory/long-term.md`](../templates/memory/long-term.md) | 只放跨文件洞察和索引 |
| 每日记忆 | [`templates/memory/daily.md`](../templates/memory/daily.md) | 可选，适合高频记录 |
| 工具与数据来源 | [`templates/integrations/tools.md`](../templates/integrations/tools.md) | 接外部工具时使用 |
| 精力画像 | [`templates/profile/energy-profile.md`](../templates/profile/energy-profile.md) | 可选拆分模板，不建议一开始创建 |

## 外部 MCP 和工具接入

本地 Markdown 是默认低门槛方案，不是唯一方案。读者可以让 AI 根据自己的工具栈改造 `integrations/tools.md` 和相关读写规则。

常见改造：

- 待办事项接滴答清单、Todoist、Things、Linear、Notion database。
- 日历接 Google Calendar、Apple Calendar、Outlook。
- 愿景和长期笔记接 Notion、Obsidian、Logseq。
- 复盘和日志保留本地 Markdown，方便版本管理和迁移。

接入外部 MCP 时要保留三个原则：

1. **读写分离**：读取可以更主动，写入必须更谨慎。
2. **确认后写入**：创建、修改、删除外部事项前先让用户确认。
3. **工具失败可降级**：MCP 不可用时，先输出 Markdown 草案，不阻塞教练过程。

## 维护节奏

- 每天：必要时更新 `memory/daily/YYYY-MM-DD.md` 或 `planning/daily-plan.md` 的实际记录。
- 每周：更新 `weekly-plan.md` 和 `review-log.md`。
- 每月或阶段变化：更新 `life-compass.md`、`projects.md`，并整理 `user.md` 中已经稳定的精力/执行线索。
- 当某类记录持续增长：先建议用户拆分，再创建专项文件。

记录系统的目标不是让用户被数据管理，而是让下一次对话更懂上下文，让计划更贴近真实生活。
