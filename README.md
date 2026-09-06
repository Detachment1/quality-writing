# quality-writing

让 dsh / pi / zcode 写出高质量文字的统一规范与技能包。

核心思想：**质量能力不是独立工具，而是 agent 的默认行为**——通过「仓库公约 + 统一方法论 + 场景技能 + openwiki 知识」四层，无缝嵌入 SE 与开发的日常使用，不增加额外使用成本。

## 为什么是这个架构

四个痛点（自造词、啰嗦、条理乱、结构乱）是横切关注点，任何文字产出都存在。
所以采用：**一份统一方法论（唯一权威）+ 薄场景技能（只放场景特有信息）**。
技能引用方法论而非各自内嵌规则，避免规则漂移、改一处全生效。

## 目录结构

```
quality-writing/
├── methodology/
│   └── writing-methodology.md      # ★ 统一写作方法论（双阶段：拆解 → 展开），唯一权威
├── skills/
│   ├── _template.md                # 场景技能统一薄模板（新技能照它填）
│   └── write-design-doc.md         # 示例场景技能
├── openwiki/
│   └── INSTRUCTIONS.example.md     # openwiki 指令示例（生成高质量术语表）
└── repo-config/
    └── AGENTS.md                   # 放进两个 git 仓的公约，agent 启动自动加载
```

## 四层协作关系

```
AGENTS.md（公约，agent 启动自动加载）
   ↓ 指向
writing-methodology.md（唯一权威：拆解→展开 + 通用四问）
   ↑ 被引用
skills/*（薄适配：只填读者用途/骨架/术语域/范例）
   ↑ 术语来源
openwiki（术语表：中文术语/English/代码真实命名/定义/别名禁用词/出处）
```

## 怎么用（无缝衔接，零额外成本）

1. 把 `repo-config/AGENTS.md` 放进**代码仓**和**文档仓**各一份（或 git submodule / 路径引用）。
2. 代码仓用 openwiki 生成**术语表**（真实命名 + 证据），方法见 `openwiki/INSTRUCTIONS.example.md`。
3. dsh / pi / zcode 启动自动加载 AGENTS.md，写任何文字自动遵守方法论。
4. 需要写正式文档时，agent 调用对应 `skills/*`，按「拆解 → 展开」执行。

## 方法论核心（一句话）

> 写作 = 拆解（为自己，无损压缩）→ 展开（为读者，零跳跃读懂）

详见 `methodology/writing-methodology.md`。

## 内网离线部署

- 本仓库是纯 Markdown + 文本，**无需安装任何依赖**。
- 有网机器：`git clone` 或下载 zip → 拷入公司内网 → 放进 git 仓 / 挂到 agent 可读路径即可。

## 待办（按优先级）

1. 补其余场景技能：性能分析、SQL 分析、项目汇报、wiki、日常回复（套 `skills/_template.md`）。
2. 为 `write-design-doc` 补一份团队认可的范例（gold exemplar）。
3. 到公司把 `repo-config/AGENTS.md` 里的方法论路径填死，并跑一篇真实设计文档验证。
