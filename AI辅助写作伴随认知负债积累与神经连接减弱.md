---
type: 证据单元
origin: AI起草（待验收）
confidence: 待验证
source_ref: "Kosmyna, N. et al., “Your Brain on ChatGPT: Accumulation of Cognitive Debt when Using an AI Assistant for Essay Writing Task”, arXiv:2506.08872（v2，2025-12-31 修订），MIT Media Lab"
url: https://arxiv.org/abs/2506.08872
supports:
  - "[[AI原生笔记系统的设计原则]]"
contradicts:
related_to:
  - "[[生成式AI深度使用与批判性思维投入下降相关]]"
Confidence: 待验证
---

# AI辅助写作伴随认知负债积累与神经连接减弱

**断言**：MIT Media Lab 的脑电（EEG）写作实验（n=54，三期同条件 + 第四期交叉换组）发现：全程用 ChatGPT 写论文的一组神经连接最弱、对自己文章的所有权感最低、且难以准确引用自己刚写的内容；第四期把 LLM 用户换回纯脑写作时，其 alpha/beta 连接显著偏低。作者称之为"认知负债"（cognitive debt）的积累——外包给 AI 的认知活动没有消失，而是以更弱的神经常态与更低的记忆占有形式欠着。

## 出处

MIT Media Lab（Kosmyna, Hauptmann, Yuan, Situ, Liao, Beresnitzky, Braunstein, Maes），arXiv:2506.08872，2025-06-10 提交、2025-12-31 出 v2 修订版（216 页）。设计：LLM / 搜索引擎 / 纯脑三组，前三期每组同条件共 54 人完成；第四期交叉换组（LLM→纯脑、纯脑→LLM）仅 18 人完成。测量：EEG 连接性、NLP 文本分析、人类教师 + AI 评审评分、自报告所有权与访谈。

## 原文

> "EEG revealed significant differences in brain connectivity: Brain-only participants exhibited the strongest, most distributed networks; Search Engine users showed moderate engagement; and LLM users displayed the weakest connectivity. Cognitive activity scaled down in relation to external tool use."
>
> "Self-reported ownership of essays was the lowest in the LLM group and the highest in the Brain-only group. LLM users also struggled to accurately quote their own work."
>
> "While LLMs offer immediate convenience, our findings highlight potential cognitive costs. Over four months, LLM users consistently underperformed at neural, linguistic, and behavioral levels."

（引文为官方摘要原文，AI 已于 2026-11-12 从 arXiv 摘要页（v2）直接回源抓取，链接见 `url`；按验收协议，未经你过目，`confidence` 仍为待验证。）

## 我的批判

- 样本极小：前三期每组约 18 人、第四期交叉仅 18 人——效应量估计不稳，任何亚组结论都缺乏统计功效；
- 仍为 preprint：v2 修订后 arXiv 页面未见同行评审发表记录，216 页的单实验室报告未经独立复制；媒体标题（"ChatGPT 把大脑写傻了"）远跑在数据前面；
- 构念效度存疑：EEG"连接性强弱"作为认知投入/质量的代理指标本身有争议——弱连接也可能只反映熟练或省力，不必然是损伤；
- 任务与人群单一：议论文写作、单一实验室、数月窗口，外推到长期、多任务的真实知识工作还需更多证据；
- 最值得重视的设计是第四期交叉：纯脑→LLM 组的记忆回溯与枕顶/前额激活反而更高，提示效应可随工具切换立即变化——既支持"负债"存在，也提示它可能是**状态性、可逆的**（这个细节对"不可逆损伤"的论证是反向的，值得诚实记下）；
- 对本库的含义：与 [[生成式AI深度使用与批判性思维投入下降相关]] 构成方法三角（自报告调查 × 神经生理实验，不同人群、不同任务，方向一致）；本库引它们作 [[AI原生笔记系统的设计原则]] 强制原则的经验佐证——但原则的最终依据是"判断不外包"的逻辑论证与不可逆损伤的边界，不押注这两条 2025 年初步研究的效应量，即使日后被推翻，原则清单本身不塌。
