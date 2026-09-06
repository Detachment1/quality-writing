# quality-writing

让 dsh / pi / zcode 写出高质量文字的统一规范。

核心思路：**质量能力不是独立工具，而是 agent 的默认行为**——由「仓库公约 + 统一方法论 + openwiki 术语表」三层协作实现（见下方总览图）。

## 30 秒速览

**三层协作关系（总览图）：**

```
AGENTS.md（公约，agent 启动自动加载；含「进入写作前」强制门）
   ↓ 引用
writing-methodology.md（唯一权威：拆解 → 展开 + 通用四问 + 总览层形态表）
   ↑ 术语来源
openwiki（术语表：中文术语/English/代码真实命名/定义/别名禁用词/出处）
```

**三步上手：**

1. 把 `repo-config/AGENTS.md` 放到全局位置（dsh 为 `~/.dsh/AGENTS.md`）或仓库根；
2. 用 openwiki 给代码仓生成术语表（真实命名 + 指向代码的 repo:// 证据）；
3. 直接让 agent 写文档，公约会自动走「拆解 → 脑图确认 → 展开 → 四问」，无需调用任何技能。

> 前置：openwiki 是 LangChain 的仓库 wiki 生成 CLI，需单独安装并配置内网 OpenAI 兼容接口（见「前置条件与离线部署」）。

## 快速上手

1. **放公约**：推荐先放全局（见下节「全局配置」，一次生效）；只针对单仓时，把 `repo-config/AGENTS.md` 放进该仓库根即可。
2. **建术语表**：把 `openwiki/INSTRUCTIONS.example.md` 内容复制进代码仓的 `openwiki/INSTRUCTIONS.md`，运行 `openwiki --update --language zh-CN`，产出 `术语表.md`（每条术语带指向代码的 repo:// 证据）。
3. **写文档**：直接让 agent 写即可。公约自动执行「阶段一思考 → 固化脑图 → 你确认 → 阶段二展开 → 四问自检」。不同文档的总览层形态见方法论里的「总览层形态」表，新场景加一行即可。

## 全局配置（推荐：一次配置，所有回复生效）

把公约放到 agent 的用户级全局位置后，它对该 agent 下的**所有项目、所有文字产出**（回复 / 文档 / 注释 / PR 描述）自动生效，无需每个仓库复制：

| agent | 全局文件位置 |
|---|---|
| dsh | `~/.dsh/AGENTS.md`（或 `$DSH_HOME/AGENTS.md`） |
| pi / zcode | 各自的用户级全局指令文件（路径待确认，机制相同） |

两层分工：

- **全局文件**：四条铁律 + 方法论引用 + 「进入写作前」门 + 第三方 skill 映射 —— "怎么写字"的规则，只放一次。
- **项目文件**：只留「术语源 → 本仓 openwiki」一句 —— "用什么词"的来源，随项目变。

## 目录结构

```
quality-writing/
├── methodology/
│   └── writing-methodology.md      # ★ 统一写作方法论（拆解 → 展开 + 四问 + 总览层形态表）
├── openwiki/
│   └── INSTRUCTIONS.example.md     # openwiki 指令示例（生成高质量术语表）
└── repo-config/
    └── AGENTS.md                   # 全局 / 项目通用公约（agent 启动自动加载）
```

## 为什么是这个架构

四个痛点（自造词、啰嗦、条理乱、结构乱）是横切关注点，任何文字产出都存在。
所以采用：**一份统一方法论（唯一权威），全局强制生效**。场景差异（总览层形态、术语域）只体现在方法论的一张表 + openwiki 术语表里，**不另设技能**——避免规则在多处漂移。

## 方法论核心（一句话）

> 写作 = 拆解（为自己，无损压缩）→ 展开（为读者，零跳跃读懂）

详见 `methodology/writing-methodology.md`。

## 前置条件与离线部署

- **本仓库**：纯 Markdown + 文本，无任何依赖，`git clone` 或下载 zip 即用。
- **生成术语表**：需另装 openwiki（LangChain 开源 CLI）并配置内网 OpenAI 兼容接口；到公司后 `openwiki --update` 即可，全程不联网。
