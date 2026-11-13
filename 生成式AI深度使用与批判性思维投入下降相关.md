---
type: 证据单元
origin: AI起草（待验收）
confidence: 待验证
source_ref: "Lee, H-P. et al., “The Impact of Generative AI on Critical Thinking: Self-Reported Reductions in Cognitive Effort and Confidence Effects From a Survey of Knowledge Workers”, CHI 2025（Microsoft Research & Carnegie Mellon University，n=319，936 个一手用例，DOI: 10.1145/3706598.3713778）"
url: https://doi.org/10.1145/3706598.3713778
supports:
  - "[[AI原生笔记系统的设计原则]]"
contradicts:
related_to:
  - "[[AI辅助写作伴随认知负债积累与神经连接减弱]]"
---

# 生成式AI深度使用与批判性思维投入下降相关

**断言**：对 319 名每周使用生成式 AI 的知识工作者的调查显示，对 AI 信心越强的受访者，自报告的批判性思维投入越少——角色从"思考者"退为"校对者"，认知重心从执行转向验证、整合与任务监护；对自身能力信心越强者，投入反而越多。

## 出处

Microsoft Research 与 Carnegie Mellon University 联合调查，发表于 CHI 2025（官方页与 DOI 见 `url`），样本 n=319 名每周使用 GenAI 的知识工作者，收集 936 个一手用例。定量结论：对 GenAI 信心越高，批判性思维投入越少；对自身能力信心越高，投入越多。定性结论：批判性思维的重心从执行转向信息验证、回应整合与任务监护。

## 原文

> "Specifically, higher confidence in GenAI is associated with less critical thinking, while higher self-confidence is associated with more critical thinking."
>
> "Qualitatively, GenAI shifts the nature of critical thinking toward information verification, response integration, and task stewardship."

（引文来自官方摘要，AI 已于 2026-11-12 从 Microsoft Research 页面与 ACM DL 回源抓取，链接见 `url`；按验收协议，未经你过目，`confidence` 仍为待验证。另注：官方标题为 "Reduction**s**"（复数），此前 `source_ref` 的单数拼写已在本轮回源时修正，断言措辞也已从"使用频率"校准为摘要实际报告的"信心效应"。）

## 我的批判

- 方法论弱点：自我报告 + 相关性设计，不能证明因果——也可能是批判性投入本来就低的人更爱用 AI；
- 与 [[AI辅助写作伴随认知负债积累与神经连接减弱]]（MIT Media Lab 脑电实验，2025）互为方法三角佐证——自报告调查与神经生理实验在人群、任务、测量方式上互补而方向一致，但两者都是 2025 年的初步研究，效应量与可复制性待后续文献检验；
- 对本库的含义：[[AI原生笔记系统的设计原则]] 用它作强制原则的经验佐证——佐证方向成立，但"强制"的最终依据是不可逆损伤的逻辑论证，不依赖本研究的强度，即使本研究日后被推翻，原则清单本身不塌。
