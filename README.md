# quality-writing

让 dsh / pi / zcode 写出高质量文字的统一规范与技能包。

核心思路：**质量能力不是独立工具，而是 agent 的默认行为**——由「仓库公约 + 统一方法论 + 场景技能 + openwiki 术语表」四层协作实现（见下方总览图）。

## 30 秒速览

**四层协作关系（总览图）：**

```
AGENTS.md（公约，agent 启动自动加载）
   ↓ 指向
writing-methodology.md（唯一权威：拆解 → 展开 + 通用四问）
   ↑ 被引用
skills/*（薄适配：只填读者用途/骨架/术语域/范例）
   ↑ 术语来源
openwiki（术语表：中文术语/English/代码真实命名/定义/别名禁用词/出处）
```

**三步上手：**

1. 把 `repo-config/AGENTS.md` 放进代码仓、文档仓各一份；
2. 用 openwiki 给代码仓生成术语表（真实命名 + 指向代码的 repo:// 证据）；
3. 让 agent 写文档时调用 `skills/*`，其余由它自动遵守。

> 前置：openwiki 是 LangChain 的仓库 wiki 生成 CLI，需单独安装并配置内网 OpenAI 兼容接口（见「前置条件与离线部署」）。

## 快速上手

1. **放公约**：把 `repo-config/AGENTS.md` 放进代码仓和文档仓各一份；若两仓都要用，建议用 git submodule 指向本仓库，避免两份公约各自漂移。
2. **建术语表**：把 `openwiki/INSTRUCTIONS.example.md` 内容复制进代码仓的 `openwiki/INSTRUCTIONS.md`，运行 `openwiki --update --language zh-CN`，产出 `术语表.md`（每条术语带指向代码的 repo:// 证据）。
3. **写文档**：需要写正式文档时让 agent 调用 `skills/write-design-doc.md`（其余场景照 `skills/_template.md` 新增），按「拆解 → 展开 → 四问自检」执行。

## 目录结构

```
quality-writing/
├── methodology/
│   └── writing-methodology.md      # ★ 统一写作方法论（双阶段：拆解 → 展开）
├── skills/
│   ├── _template.md                # 场景技能统一薄模板（新技能照它填）
│   └── write-design-doc.md         # 示例场景技能
├── openwiki/
│   └── INSTRUCTIONS.example.md     # openwiki 指令示例（生成高质量术语表）
└── repo-config/
    └── AGENTS.md                   # 放进两个 git 仓的公约，agent 启动自动加载
```

## 为什么是这个架构

四个痛点（自造词、啰嗦、条理乱、结构乱）是横切关注点，任何文字产出都存在。
所以采用：**一份统一方法论（唯一权威）+ 薄场景技能（只放场景特有信息）**。
技能引用方法论而非各自内嵌规则，避免规则漂移、改一处全生效。

## 方法论核心（一句话）

> 写作 = 拆解（为自己，无损压缩）→ 展开（为读者，零跳跃读懂）

详见 `methodology/writing-methodology.md`。

## 前置条件与离线部署

- **本仓库**：纯 Markdown + 文本，无任何依赖，`git clone` 或下载 zip 即用。
- **生成术语表**：需另装 openwiki（LangChain 开源 CLI）并配置内网 OpenAI 兼容接口；到公司后 `openwiki --update` 即可，全程不联网。

## 待办（按优先级）

1. 补其余场景技能：性能分析、SQL 分析、项目汇报、wiki、日常回复（套 `skills/_template.md`）。
2. 为 `write-design-doc` 补一份团队认可的范例（gold exemplar）。
3. 到公司把 `repo-config/AGENTS.md` 里的方法论路径填死，并跑一篇真实设计文档验证。
