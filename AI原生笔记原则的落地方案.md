---
status: Active
origin: AI起草（待验收）
confidence: 待验证
related_to:
  - "[[AI原生笔记系统的设计原则]]"
  - "[[AI时代关于笔记设计的问题]]"
  - "[[个人知识管理方法论全景图]]"
  - "[[落地方案的差距审计]]"
type: Note
---

# AI原生笔记原则的落地方案

回答一个递进的问题：[[AI原生笔记系统的设计原则]] 给出了十条原则，但原则要活下来，必须住进一个具体软件的日常流程里。本文回答两件事：**在 Obsidian / Logseq / Tolaria / Capacities 四款软件里选哪款做主库**，以及**选定之后，十条原则分别落成什么文件、什么属性、什么流程**。

## 一、选型：把强制原则当硬门槛

选软件的判据不是功能清单，而是十条原则里的五条强制项——违反一次就不可逆的那五条。推荐原则（顺不顺手）不该当门槛：体验可以忍，信任坏了救不回来。

### 逐款对照

**Capacities——被原则 4（数据主权）一票否决。** 它的 object types 是四款里概念上最接近"属性是 AI 的 API"的设计（类型化对象 + 属性，甚至内置 AI 属性自动填充），但笔记存在云端专有数据库里——官方文档原话：*"stores your notes in its own database format, not as traditional markdown files in folders"*。offline-first ≠ 本地文件。强制原则 4（本地优先、纯文本、可整体导出）直接出局。若喜欢它的捕获体验，最多当"采集端"，但 provenance 会被劈成两半，得不偿失。

**Logseq——转型期风险，暂不主投。** markdown 版（OG）纯文本、git 友好，本是原则 4 的模范生；但官方重心已转到 DB 版（2026 年进入 beta），**源真相从 markdown 文件移进 SQLite 数据库**，markdown 变成单向镜像（"Markdown Mirror"），双向同步仍在开发——恰好踩中原则 4 的后半句和原则 5 的 git 叙事（论坛里社区反复在问"DB 版 git 怎么办"）。同时 OG 版维护明显放缓（2026 年 4 月后无新版本，社区已在讨论"是否永远留在 OG"）。在仓库换地基的节点上把长期库放上去，时机不对。观望，等 DB 版 md 双向同步落地再评估。

**Obsidian——最强的次选，也是最好的平移保险。** 纯 md 本地、免费核心、2000+ 插件，原则 4 满分；git 插件成熟，原则 5 可满足；2025 年起 Bases 成为核心功能（属性表格视图、可直接编辑），加上 Properties 面板，"属性 + 视图"有了官方形态。AI 靠插件生态（Copilot、Smart Connections 等，2026 年的 Copilot 4 甚至能驱动 Claude Code / Codex / OpenCode 这类 coding agent），能力上限很高；但**每条强制原则都靠"自己装插件 + 自己守纪律"实现**：没有类型系统强制 schema，属性是自由文本，AI 写库的 review 边界由插件决定。纪律可达，结构不保。

**Tolaria——五条强制原则里唯一"靠结构而非纪律"满足的。**

- **原则 3 / 属性即 API**：Type 文档把属性与关系变成每个类型的声明式 schema（本库 [[概念]]、[[哲学家]] 已在用），关系一律受控 wikilink；
- **原则 2 / 人确认**：AI 通道结构上分层——direct model 只读聊天（拿到上下文，没有写入工具），coding agent 才可写（Vault Safe 限文件工具，Power User 才开 shell）；外部 MCP 的 `update_note` 还带修改时间守卫防覆盖；
- **原则 5 / 可撤销**：内置 git 客户端（逐笔记 diff / history / 一键 commit），官方文档直接写了"Why Git Matters For AI"一节；
- **原则 4 / 数据主权**：vault 就是普通 md 文件夹（本库在 iCloud），且不锁 AI 供应商——agent 可换 Claude Code / Codex / OpenCode；
- **原则 6 / 派生可再生成**：`views/` 目录是派生层的官方形态——视图是文件，可删可重建。

**结论：Tolaria 做主库，Obsidian 做"第二读者"和生态补充，同一文件夹可双开。** 这不是功能对比的结论（论插件生态 Obsidian 远胜），而是**风险结构**的结论：Tolaria 把强制原则做进了产品结构，纪律成本最低；同时因为库就是纯 md，选 Tolaria 的下行风险有界——哪天 Tolaria 停更，整个库平移到 Obsidian 只是复制文件夹，损失仅为 Type 文档和 views 两个薄层（纯文本，半天可重建）。反过来，从 Capacities 或 Logseq DB 迁出就没这么便宜。

诚实的风险栏：Tolaria 是年轻产品，single-vendor 风险真实存在。缓解措施恰好就是原则 4 本身：纯文本 + git + 随时可走。

## 二、Tolaria 落地方案

### 1. 类型系统：属性是 AI 的 API（原则 3 的落地）

| 类型 | 属性（✦ 为本次新增） | 关系 | 说明 |
|---|---|---|---|
| [[note]] | ✦origin、✦confidence、✦related_to | related_to | 研究笔记的主力类型，provenance 落在这里 |
| [[证据单元]]（本次新建） | source_ref、origin、confidence | supports、contradicts、related_to | 文献笔记的重构形态：断言 + 出处 + 批判 |
| [[概念]] | proposed_by、era（**不加** provenance） | related_to | 概念是立场沉淀，不是待验证据——需要验证的内容走证据单元，用 supports/contradicts 挂回概念 |
| [[哲学家]] | 维持现状 | related_to | 人物卡，不加 |
| [[问题]]（本次新建） | ✦status（Open / Resolved，默认 Open）、origin | raised_by、related_to | 给开放问题安家，避免好问题淹死在长文的"开放问题"一节里；不设 confidence（问题不是断言） |

属性最小化检验：每个属性都要能回答"AI 用它能做什么推理"——origin 支撑"哪些结论还没过人"的过滤；confidence 支撑"别把待验证当定论"的推理；source_ref 支撑"回原文核对"。答不上的属性不加。

### 2. 两个悬而未决的问题，现在拍板

**置信度用枚举，不用数值**（回答原则笔记开放问题 1）：`已验证 / 待验证 / 存疑`。理由：① 视图过滤需要 equals，数值反而建不出"待验证队列"这种视图；② 枚举不制造伪精确——"我 70% 确信"多数时候是自我欺骗；③ AI 起草默认落 `待验证`，人核对后才改 `已验证`——这一个属性就把原则 2 变成了日常动作。

**provenance 笔记级起步，段落级不搞**（回答开放问题 2）：frontmatter 一行 `origin` + `source_ref` 足够；段落级更诚实但维护成本高一个数量级。过渡方案：AI 长文里的关键断言用引用块 + 链接就地标注出处，值得单独核对的升级为独立证据单元——粒度由"这条值不值得单独验证"决定，不由格式决定。

### 3. views/ = 派生层（原则 6 的落地）

已建两个视图（见"本次已落地"）。设计准则：

- 每个视图回答一个问题，不做"全字段全过滤"的大杂烩；
- 综述 / MOC 类派生笔记由 agent 按需生成、标注派生说明、人验收——人只手写两类内容：**例外**（AI 排错了）和**立场**（编排本身是论点）；
- 检验标准：删掉整个 views/ 和所有派生笔记，知识层毫发无损。哪天不满足这条，说明派生物已腐化成资产。

### 4. 工作流：把原则变成日常动作

- **捕获**：随手 note / Inbox，不打断心流——捕获面保持零门槛；
- **研究**：agent 产出 → `origin: AI起草（待验收）` → 人读、改、验收 → `confidence: 已验证`。验收动作就是原则 2 的日常形态——本文自己就标着"AI起草（待验收）"等你验收；
- **可撤销**：agent 批量改动前先 commit（Tolaria git 面板一键）；Vault Safe 模式下 agent 只有文件工具，Power User 才开 shell；
- **每周巡检**（可交给 agent 的例行任务）：报告悬空 wikilink（受控关系零悬空）；提议把 Inbox / 流水日志内容提升为证据单元或概念（**必须带理由、可拒绝**，AI 不得静默移动内容）；报告"待验证"超过两周的证据单元。

### 5. 如果将来要搬走：无损平移路径

到 Obsidian：复制文件夹即用；Type 文档 → Templates + 属性约定，`views/` → Bases，内置 git → git 插件，agent 通道 → Copilot / 自建 MCP。反方向（Obsidian → Tolaria）同样只是复制文件夹。**数据主权的真正含义：选软件的决定永远可逆。**

## 三、本次已落地（等你验收）

- 新建 [[证据单元]] Type 文档（含默认 `confidence: 待验证`）；
- [[note]] 类型文档补 origin / confidence / related_to 占位——此后新建研究笔记自动带 provenance 字段；
- 新建 `views/ai-drafts.yml`（AI 起草待验收队列）与 `views/evidence-unverified.yml`（待验证证据队列）；
- 本方案自身按新规入库：`origin: AI起草（待验收）`、`confidence: 待验证`。

- 新建 [[问题]] Type 文档（默认 `status: Open`）与 `views/open-questions.yml`（Open 队列，Resolved 自动出队）；
- 首批 3 个问题节点入库——把长文里散落的开放问题就地"提升"为类型化节点，原文保留指针：[[属性何时过剩]]、[[多人协作下的判断主权]]（来自 [[AI原生笔记系统的设计原则]] 第六节）、[[是否新建日志类型]]（来自本文）；

未动 [[概念]]、[[哲学家]] 的属性（属性最小化）；"来源"类型仍暂缓（同一来源被 ≥3 条证据单元引用时再立）；"日志"类型已于 2026-11-12 拍板建立：[[日志]]——库里唯一零属性类型 + `views/clog.yml`，提升义务写入 Type 正文，决策记录见 [[是否新建日志类型]]（Resolved）。

- 落地当天追加一次逐原则差距审计：[[落地方案的差距审计]]——五个真实缺口（验收协议未定义、AGENTS.md 仍是出厂模板、origin 默认空、证据单元零实例、巡检无触发器）与补法见该篇；配套新建 [[每周巡检清单]]；
- 审计 P1/P2/P3 已拍板落地（2026-11-12）：**验收协议成文**进 `AGENTS.md`「本库约定」（CLAUDE.md 同步）——验收 = 通读核对断言出处 → origin 改已验收 → confidence 联动 → 异议改正文，且只有用户能执行验收，agent 不得自行盖章；[[note]]、[[问题]] 的 `origin` 默认值改 `人写`；`confidence` 空值语义（空 = 非主张性笔记，不参与验证）写入 [[note]] 正文。

## 参考

- Tolaria agent docs：Types / Properties / AI / Git / Build Custom Views / Portent
- Capacities 官方文档（Offline Support）：专有存储格式声明
- Logseq 官方论坛：What's New with Logseq DB（2026-05，DB 为源真相、Markdown Mirror 单向、双向同步在开发）
- Obsidian Bases（核心功能，2025–）：属性表格视图
- 系列前篇：[[AI原生笔记系统的设计原则]]；问题出处：[[AI时代关于笔记设计的问题]]；全景图：[[个人知识管理方法论全景图]]
