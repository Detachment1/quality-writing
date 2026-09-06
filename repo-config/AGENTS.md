# AGENTS.md — 写作与质量公约（全局 / 项目通用）

> 本文件由 agent（dsh / pi / zcode）自动加载，写任何文字都必须遵守。
> 可放用户级全局位置（dsh 为 `~/.dsh/AGENTS.md`），也可放单个仓库根；内容相同。
> 仓库内 openwiki 会在本文件维护一段 `<!-- OPENWIKI:START --> … <!-- OPENWIKI:END -->` 指针块，本公约写在那个块之外，openwiki 更新时不会覆盖。

## 全局铁律（回复 / 文档 / 注释 / PR 描述一律适用）

1. **读者模型**：假设读者有基础代码知识 + 前序需求知识，但没有本次内容的任何先验知识。
2. **结论先行**：先给结论/总览，再展开；去套话，每句话都有信息，不写废话。
3. **术语唯一**：一词一义；术语必须来自「当前项目的 openwiki 术语表」；查不到就标 `[待定]`，严禁自造词。
4. **结构可见**：先总览后细节、零跳跃、从简到繁，像受欢迎技术博客一样通俗言简。

## 进入写作前（强制）

- **阶段一 · 拆解 = 思考**：可以自己按 A1–A5 拆解，也可以用思考类 skill（grill-me、openspec-explore、brainstorming 等）辅助；这些 skill 同属阶段一，不需要在它们之前再插一步脑图。
- **阶段一的产物**（无论怎么思考出来的）必须固化为脑图 / 结构化骨架，停下等我确认；**不确认，不进入阶段二**。
- **阶段二 · 展开 = 写文档**（design / spec / 分析 / 汇报 / wiki 等），确认脑图后才开始，写完过「通用五问」。

> 拆解与验收的完整规范，动手前先 read 对应路径的 `writing-methodology.md`，严格按其「阶段一」的 A1–A5 和验收标准执行：
> - 全局：`/Users/detachment/future/AI/quality-writing/methodology/writing-methodology.md`（绝对路径，每台机器按实际 clone 位置改）
> - 项目：`quality-writing/methodology/writing-methodology.md`（quality-writing 以 git submodule 挂入仓库时）
>
> 日常聊天回复走轻量版（读者模型 + 结论先行 + 言简 + 术语准），不强制脑图。

## 与第三方 skill 的对接（映射）

思考类 skill 属于阶段一，写文档类 skill 属于阶段二；脑图卡在两者之间，而非思考之前：

| 第三方 skill | 所属阶段 | 用法 |
|---|---|---|
| superpowers / brainstorming | 阶段一 · 思考输入 | 发散后把产出做 MECE 归类，固化成脑图 |
| openspec / explore | 阶段一 · 思考 | 探索完把理解固化成脑图，确认后再进 proposal / 写作 |
| grill-me | 阶段一 · 骨架验证 | 对脑图做压力测试（同属阶段一，不单独再插脑图） |
| 任何写文档的 skill（如 openspec/proposal） | 阶段二 · 展开 | 进入前必须先有已确认的脑图 |

三原则：
1. 不改第三方 skill 本身（其升级会覆盖本地改动）。
2. 映射只写在本公约，不写进第三方 skill。
3. 任何 skill 的产出最终都要过「通用五问」，不满足就回炉。

典型链：思考（A1–A5 或 brainstorming / explore）→ 固化成脑图 → grill-me 验证 → 确认 → 展开（proposal / 写文档）→ 通用五问自检。

## 评审一篇既有文档时（不新造技能）

用方法论的「通用五问」逐条检查，列出所有需要脑补/跳跃的点，并给出修改建议。

## 术语源（治自造词）

- 术语必须来自「当前项目的 openwiki 术语表」，术语表六列：中文术语 / English / 代码真实命名 / 定义 / 别名禁用词 / 出处。
- 代码里不存在、且团队尚未约定的术语，禁止凭空创造；必须提及时标 `[待定]`。
