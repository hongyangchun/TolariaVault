---
type: Type
_icon: file-text
_color: "#64748b"
_order: 0
_sort: "modified:desc"
_list_properties_display:
  - origin
  - confidence
_pinned_properties:
  - origin
  - confidence
status: Active
origin: 人写
confidence: 待验证
related_to:
_sidebar_label: Notes
---

# Note

A Note is a general-purpose document — research notes, meeting notes, strategy docs, or anything that doesn't fit a more specific type.

研究型笔记的主力类型。`origin` 记 provenance（人写 / AI起草（待验收） / AI起草（已验收） / 混合），**默认 `人写`**——agent 起草时必须改盖 `AI起草（待验收）`；`confidence` 用枚举：已验证 / 待验证 / 存疑，**留空 = 非主张性笔记**（叙事、日程、日志类），不参与验证流程。设计与理由见 [[AI原生笔记原则的落地方案]]，验收协议见 [[落地方案的差距审计]]。
