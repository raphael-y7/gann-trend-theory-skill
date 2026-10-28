<h1 align="center">江恩趋势理论 Skill</h1>

<p align="center">中文 | <a href="README.en.md">English</a></p>

一套可直接使用的 AI skill 工具包——把《江恩趋势理论》里的趋势判读与交易作业系统，蒸馏成 12 张可单独触发、也可组合调用的能力卡。

它不是原书摘要，也不是读后感，而是把书中可复用的方法论拆成可触发、可执行、可测试的 skill 模块。

## 这套 skills 能解决什么问题

- 月线说涨、周线说跌、日线又跳了一下，不知道该信哪个周期；也不知道"顶底节节抬高"到底该怎么在图上排出来
- 一只票横盘几个月，分不清是在吸筹还是派发；只看成交量的绝对股数，没除以流通股本，把地量当成了没人要
- 止损凭感觉放，不知道锚在哪个结构位；浮盈之后该不该上移、被止损出局后什么条件可以再进
- 刚创出新高不敢追，又怕是假突破；长期窄幅区间突然放量突破，判断不了这是不是大行情的起点
- 仓位没有定额，亏了就摊薄加仓；浮盈了想加码，却不知道金字塔该怎么递减、什么时候禁止加
- 利好公布股价反而跌、股息提高或增发不知道该怎么读；亏完之后只能说"心态不好"，归不到具体的失败模式

## 蒸馏了什么

12 张能力卡（每个 slug 对应 `references/capabilities/<slug>-skill.md`），按"先判方向、再定位置、最后管钱与纪律"的顺序组织：

- **判势与区间性质**：`trend-judgment`（趋势判断：多周期图表 + 累进高低位 + 突破旧位）、`seven-action-zones`（七个行动区域位置判别）、`accumulation-distribution`（吸筹 / 派发识别：量价 × 区间 × 时间三维）
- **关键价位与风控**：`support-resistance-stops`（支撑 / 阻力复盘与止损体系）
- **选股**：`strength-based-selection`（强弱判别与选股）
- **仓位与加码**：`twelve-trading-rules`（十二条交易规则与资金管理）、`pyramid-scaling`（金字塔式加码）
- **时机与消息**：`entry-exit-timing`（买卖点位与时机）、`news-discounting`（消息贴现处理）
- **复盘、排障与体检**：`tape-review-workflow`（看盘复盘工作流）、`failure-mode-triage`（失败模式排障检查表）、`portfolio-annual-checkup`（持仓年度体检）

每张卡都按 R / I / A1 / A2 / E / B 六段组织：原文引用、自述、书中案例、未来触发场景、可执行步骤、边界与盲点。

## 两种打包模式：single 与 pack

同一套 12 张能力卡，按两种粒度各编译了一次。两者内容完全相同，区别只在"agent 能看到几个入口"。

| | single（单一入口） | pack（compact pack，多入口） |
|---|---|---|
| 可发现入口 | **1 个**：`gann-trend-theory-skill` | **8 个**：1 个来源路由入口 + 7 个已晋级独立 skill |
| 12 张能力卡放在哪 | 全部在入口的 `references/capabilities/` 里，由入口按路由表按需加载 1–2 张 | 7 张高频卡各自独立成 skill；其余 5 张仍在 router 的 `references/` 里 |
| 触发方式 | 只有入口的 description 参与匹配，进入后靠路由表分流 | 7 个高频能力可被 description 直接命中，少一跳 |
| 升级维护 | 替换 1 个目录 | 替换 8 个目录 |

pack 里被晋级为独立 skill 的 7 张卡：

- `trend-judgment-skill` — 趋势判断
- `support-resistance-stops-skill` — 支撑 / 阻力复盘与止损体系
- `accumulation-distribution-skill` — 吸筹 / 派发识别
- `strength-based-selection-skill` — 强弱判别与选股
- `twelve-trading-rules-skill` — 十二条交易规则与资金管理
- `entry-exit-timing-skill` — 买卖点位与时机
- `failure-mode-triage-skill` — 失败模式排障检查表

### 该装哪一种

按你的工作方式选，**只装一种**：

| 你的工作方式 | 推荐 | 原因 |
|---|---|---|
| 用 DSH / Codex / Claude Code 等有 skills 目录，希望列表干净 | single | 只占 1 个入口，能力一张不少 |
| 日常问题高度集中在"趋势怎么判 / 止损放哪 / 吸筹还是派发 / 选哪只强 / 仓位多少 / 该不该追 / 亏在哪" | pack | 这 7 类正是被晋级的独立 skill，能直接命中 |
| 要分发给多个 agent 或团队，各自按需取用 | pack | 可以只装其中几个独立 skill，不必整包 |
| 只想装一次、不想维护多个目录 | single | 升级时只替换 1 个目录 |

> 两版由同一个 Bundle 编译，能力内容一致。**同时安装会重复触发**，请只装一种。

## 效果示例

### 示例 1：横盘四个月，是吸筹还是派发

**用户问题**

"这票在 18 到 21 块之间横了四个月，成交量有时候很大，中间还宣布了提高分红。是主力在吸筹还是出货？"

**skill 如何判断**

- 进 `accumulation-distribution`：第一步不是看绝对成交量，而是把区间累计成交量除以流通股本，算换手次数——原书的口径是"量必须除以发售总量看"，美国钢铁 500 万股本要出现大波动"必须要有 100 多万股换手"
- 数区间往返：原书以 5 点级震荡计数，同一区间反复震荡 10—20 次、或区间内累计易手 15—20 次，才算强信号
- 核事件：原书把"交易量很大但迅速反复地跌涨、增加红利股息、派发额外权利"列为最确定的派发信号——提高分红在这里是**诱饵证据**，不是利好
- 定位置：领涨股在顶部下方 5—10 点内派发，后发股在低于高位 20—30 点处派发；同样的窄幅死寂，在顶部附近是买力枯竭，在底部附近才是吸筹
- 判停：顶部死寂与底部死寂无法区分时，输出"位置无法判定"，不默认安全

**最终回答示例**

> 先别急着叫它吸筹。三个维度要各有数字：一是换手，把区间累计成交量除以流通股本，看易手了几次；二是往返，5 点级别以上的震荡数了几次；三是时间，这四个月相对该股自己的历史算长还是短。原书的强信号门槛是区间内易手 15—20 次或 5 点级震荡 10—20 次，你这两项如果都远不到，那就只是"无信号"，既不是吸筹也不是派发。
>
> 提高分红这条要单独记一笔：原书把"增加红利股息、派发额外权利"直接列为最确定的派发信号之一，属于诱饵，不能当作看多理由。
>
> 还有一个必须换算的地方：书里的"5 点""15—20 次"是 1920 年代的固定点数，直接套到 18—21 块这个区间会得出荒谬结论。要按这只票的 ATR 或波幅百分比重新定"一摆"的阈值，并在结论里写明你用的换算基准——这是整理者的补丁，不是原书内容。
>
> 最后，即便三项都够，结论也只能写成"证据强度评估"，不能写成"主力正在出货"。原书"量价无法伪造"的前提在今天的算法拆单、高频做市环境下不严格成立。位置定不了就先判停，等突破方向出来再定性。

### 示例 2：刚创出新高，能不能追；止损放哪

**用户问题**

"这票突破了横了两年的箱体，创了新高，我追进去了，止损该放哪？创新高追进去是不是太冒险？"

**skill 如何判断**

- `trend-judgment`：先看这是第几次创新高——原书明确"在一只股票再一次创出新高时买进，总要比在其第一次创出新高时买进更为安全一些"；再看突破前的区间是吸筹区还是派发区（吸筹区向上突破可信度更高），两次突入新区间的间隔越长，冲击力越大
- `trend-judgment` 的假突破分支：创新高后数日内跌回旧高下方，标记"疑似假突破 / 派发未完"，不省略这一步
- `support-resistance-stops`：止损锚在结构位，买进口径是旧底 / 支撑位下方 3 点、做空口径是旧顶上方 1—3 点；止损单 G.T.C.，与建仓同时挂出
- `support-resistance-stops` 的归一化带：书中案例的实际比例落在 2.6%—10%，整理者给出的默认带是 3%—6%（按 ATR 校准），换算基准必须写明
- 时间确认：关键价位须"维持数周不破"才算有效；未确认时方向只能写"初步"，置信度封顶"中"

**最终回答示例**

> 先回答"追新高是不是太冒险"：原书的立场恰好相反——第二次创新高比第一次更安全，因为第一次新高往往会遭遇大量卖出打压，第二次时筹码已被吸纳。所以问题不在"追不追新高"，而在"这是第几次"。
>
> 止损位置：锚在结构位，不是按百分比随手放。买进口径是支撑位 / 旧底下方，书里的原始参数是 3 点；把它换算到你这只票，书中案例的实际比例落在 2.6%—10%，整理者建议的默认带是 3%—6%（按 ATR 校准）。这两个数字都不是原书给的现代参数，用哪个要写进你的预案。
>
> 两条铁律照抄：止损单在建仓同时挂出（G.T.C.，未经取消即有效），成交后绝不取消、绝不放宽——原书说想承担比原来更大的损失时，"99% 的可能是错了"。
>
> 还要留一个分支：如果创新高后几天内跌回旧高下方，这就不是回调，而是"疑似假突破 / 派发未完"的信号，此时该做的是核对派发证据，而不是补仓摊薄。另外，突破是否有效要看有没有"维持数周不破"，刚突破那天只能算初步确认。
>
> 最后一句边界：本书所有案例都是对已完成走势的回看，没有失败率统计，也没有样本外检验。这套流程给你的是可复核的证据链和明确的判停条件，不是胜率承诺。

## 这些 skill 是怎么生成出来的

这套 skill 使用 **[cangjie-skill](https://github.com/kangarooking/cangjie-skill)** 的 RIA-TV++ 流水线生成，整个流程分六个阶段：

1. **整书理解（Adler 分析）**——用 Mortimer Adler 的分析阅读法，对全书做结构、解释、批判、应用四步拆解
2. **并行提取**——同时派多个专项提取器（框架、原则、案例、反例、术语），从原文中提取候选方法论单元
3. **三重验证筛选**——每个候选必须通过三项检验：书内至少有 2 处独立佐证（跨域）、能回答书中未明说的新问题（预测力）、不是常识（独特性）
4. **RIA++ 构造**——按 R（原文引用）/ I（用自己的话重写）/ A1（书中案例）/ A2（未来触发场景）/ E（可执行步骤）/ B（边界与盲点）六个维度结构化
5. **Zettelkasten 链接**——找出能力卡之间的依赖、对比、组合关系，生成能力索引与路由表
6. **触发与输出测试**——为每张卡设计触发盲测题（含诱饵题：该触发时要触发，不该触发时要沉默）与输出评测场景，未通过的卡回炉重做，回炉后再做回归验证

## 仓库结构

```text
gann-trend-theory-skill/
├── README.md                      ← 你正在看的
├── README.en.md                   ← English version
├── LICENSE                        ← MIT
├── BOOK_OVERVIEW.md               ← 整书理解（Adler 四步拆解，阶段 0 产出）
├── verified.md                    ← 12 个能力级单元的三重验证结论
├── single/                        ← 单一入口模式
│   └── gann-trend-theory-skill/
│       ├── SKILL.md               ← 入口：触发条件 + 路由表 + 加载规则
│       ├── BUILD_MANIFEST.json    ← 编译清单与文件哈希
│       └── references/
│           ├── overview.md        ← 整书概览
│           ├── capability-index.md  ← 完整意图与关键词索引
│           ├── cheatsheet.md      ← 决策规则速查
│           ├── glossary.md        ← 术语表
│           └── capabilities/      ← 12 张能力卡
├── pack/                          ← 多入口模式（compact pack）
│   ├── BUILD_MANIFEST.json
│   ├── capability-destinations.json
│   ├── gann-trend-theory-skill-router/
│   │   ├── SKILL.md               ← 来源路由入口
│   │   └── references/            ← 12 张卡 + 索引，供 router 内部调用
│   ├── trend-judgment-skill/
│   │   └── SKILL.md
│   ├── support-resistance-stops-skill/
│   │   └── SKILL.md
│   ├── accumulation-distribution-skill/
│   │   └── SKILL.md
│   ├── strength-based-selection-skill/
│   │   └── SKILL.md
│   ├── twelve-trading-rules-skill/
│   │   └── SKILL.md
│   ├── entry-exit-timing-skill/
│   │   └── SKILL.md
│   └── failure-mode-triage-skill/
│       └── SKILL.md
```

## 如何使用

先把仓库克隆下来：

```bash
git clone https://github.com/raphael-y7/gann-trend-theory-skill.git
```

### 装 single（推荐先试这个）

```bash
# macOS / Linux
cp -r gann-trend-theory-skill/single/gann-trend-theory-skill ~/.agents/skills/
```

```powershell
# Windows
Copy-Item -Recurse .\gann-trend-theory-skill\single\gann-trend-theory-skill "$env:USERPROFILE\.agents\skills\"
```

### 装 pack

只复制含 `SKILL.md` 的目录，不要把 `pack/` 下的两个 json 一起拷进 skills 目录：

```bash
# macOS / Linux
cd gann-trend-theory-skill/pack
cp -r gann-trend-theory-skill-router \
      trend-judgment-skill \
      support-resistance-stops-skill \
      accumulation-distribution-skill \
      strength-based-selection-skill \
      twelve-trading-rules-skill \
      entry-exit-timing-skill \
      failure-mode-triage-skill ~/.agents/skills/
```

```powershell
# Windows
$pack = ".\gann-trend-theory-skill\pack"
$dest = "$env:USERPROFILE\.agents\skills"
@('gann-trend-theory-skill-router','trend-judgment-skill','support-resistance-stops-skill','accumulation-distribution-skill','strength-based-selection-skill','twelve-trading-rules-skill','entry-exit-timing-skill','failure-mode-triage-skill') |
  ForEach-Object { Copy-Item -Recurse -LiteralPath (Join-Path $pack $_) -Destination $dest }
```

> `~/.agents/skills` 是 DSH 的 skill 目录；用别的 agent 时换成它自己的 skills 目录即可（例如 Claude Code 是 `~/.claude/skills`）。

### 怎么确认装好了

装完问一句"这票横了四个月，是吸筹还是派发"，看 agent 是否先要流通股本、开始算换手次数与区间往返，而不是直接给结论。装的是 single 时，它会先读入口再按路由表进能力卡；装的是 pack 时，对应能力会被直接命中。

## 来源

- 《江恩趋势理论》威廉·D.江恩 著
- 全书蒸馏，共产出 12 张能力卡

## 声明

本仓库只发布蒸馏后的 skill、索引与规则速查材料，不包含原书 PDF、EPUB、OCR 文件、截图或全书转写稿。能力卡中出现的原文引用仅用于标注方法论出处和保持可审计性。

书中所有数字判据（3 点止损、5 点级震荡、15—20 次换手、200—300 万股天量、100→50→30→20→10 的加码序列等）都绑定 1920 年代的价位与股本口径，原书未提供统计回测背书，用于现代市场前必须按波动率与流通盘归一化，并在输出中声明所用换算基准；换算本身是整理者的补丁，不是原书内容。原书的时间周期算法作者明确未公开，本仓库不补造任何周期数字。本仓库内容不构成投资建议。

## License

[MIT](https://opensource.org/licenses/MIT)
