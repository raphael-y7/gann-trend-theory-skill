<h1 align="center">江恩股市趋势理论 Skill</h1>

<p align="center">中文 | <a href="README.en.md">English</a></p>

一套可直接使用的 AI skill 工具包——把威廉·D.江恩《江恩股市趋势理论》里那套「用月/周/日行情变化图、成交量与时间复盘旧高低位，判断趋势与吸筹派发，再用止损单、资金管理与金字塔加码控住风险」的作业系统，蒸馏成 12 张可单独触发、也可组合调用的能力卡。

它不是原书摘要，也不是读后感，而是把书中可复用的方法论拆成可触发、可执行、可测试的 skill 模块。

## 这套 skills 能解决什么问题

- 一只票横了几个月，说不清是吸筹还是派发，只能等突破以后再追，追进去才发现是出货
- 知道"要止损"，但说不清止损放哪、放多宽；被扫掉一次之后不敢再进，也不知道什么条件才能重新入场
- 月线、周线、日线信号互相打架，不知道该信哪个周期；创新高不敢追，怕假突破，又怕错过主升段
- 手里一堆候选股，排不出先买哪只；也不知道该不该卖掉弱势股换强势股
- 利好消息出来股价反而跌，不知道该信消息还是信图表；突发利空大幅低开，不知道当天该不该动手
- 亏了之后只能总结成"心态不好"，说不清具体违反了哪一条规则，下一次照旧

## 蒸馏了什么

12 张能力卡，按"先判势、再定位、最后管钱"的顺序组织。7 张在 pack 模式下晋级为独立 skill，5 张留在路由入口内按需加载：

- **判势与定位**（4 张）：`trend-judgment-skill`（趋势判断：多周期＋累进高低位＋突破旧位）、`support-resistance-stops-skill`（支撑/阻力复盘与止损体系）、`accumulation-distribution-skill`（吸筹/派发识别：量价×区间×时间三维）、`seven-action-zones`（七个行动区域位置判别）
- **选股与买卖时机**（2 张）：`strength-based-selection-skill`（强弱判别与选股：只做活跃领头股、突破上年高点名单、卖弱买强）、`entry-exit-timing-skill`（买卖点位与时机：距底 10 点买、距顶 10 点卖、获利四问、拿不准就退出）
- **仓位、纪律与排障**（3 张）：`twelve-trading-rules-skill`（十二条交易规则与资金管理）、`pyramid-scaling`（金字塔式加码：逐级减量 100→50→30→20→10）、`failure-mode-triage-skill`（失败模式排障检查表：三大致命错误＋35 条已验证失败模式）
- **消息、流程与持仓看护**（3 张）：`news-discounting`（消息贴现处理）、`tape-review-workflow`（看盘复盘工作流：不盯盘、三层图表、量除以流通股本）、`portfolio-annual-checkup`（持仓年度体检）

每张卡的完整定义（触发意图、关键词、依赖关系、去向）都在 [`bundle/verified.yaml`](./bundle/verified.yaml)，能力之间的依赖图与加载顺序见 [`INDEX.md`](./INDEX.md)。

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
- `support-resistance-stops-skill` — 支撑/阻力复盘与止损体系
- `accumulation-distribution-skill` — 吸筹/派发识别
- `strength-based-selection-skill` — 强弱判别与选股
- `twelve-trading-rules-skill` — 十二条交易规则与资金管理
- `entry-exit-timing-skill` — 买卖点位与时机
- `failure-mode-triage-skill` — 失败模式排障检查表

留在路由入口里的 5 张：`seven-action-zones`、`pyramid-scaling`、`news-discounting`、`tape-review-workflow`、`portfolio-annual-checkup`。

### 该装哪一种

按你的工作方式选，**只装一种**：

| 你的工作方式 | 推荐 | 原因 |
|---|---|---|
| 用 DSH / Codex / Claude Code 等有 skills 目录，希望列表干净 | single | 只占 1 个入口，能力一张不少 |
| 日常问题高度集中在"判势 / 止损放哪 / 这是吸筹还是派发 / 选哪只股 / 仓位怎么配 / 现在能不能买 / 我又亏在哪" | pack | 这 7 类正是被晋级的独立 skill，能直接命中 |
| 要分发给多个 agent 或团队，各自按需取用 | pack | 可以只装其中几个独立 skill，不必整包 |
| 只想装一次、不想维护多个目录 | single | 升级时只替换 1 个目录 |

> 两版由同一个 Bundle 编译，能力内容一致。**同时安装会重复触发**，请只装一种。

## 效果示例

### 示例 1：横盘七个月，是吸筹还是派发

**用户问题**

"这只票在 18 到 22 之间横了七个月，最近放量冲了一次 22 又掉回来，是吸筹还是派发？"

**skill 如何判断**

- 入口先过判停：这是区间性质判断，不涉及点位预测，放行；进入 `accumulation-distribution-skill`
- 量必须除以流通股本看：判读口径是换手率，不是绝对股数——书里以美国钢铁 500 万股本、"要有 100 多万股换手才够大波动"为基准
- 区间计数：同区间内 5 点以上的往返算一次，10–20 次不破顶底即为吸筹或派发；方向靠位置分
- 位置定性质：低位窄幅小量偏吸筹，高位大量反复偏派发——调 `seven-action-zones` 看当前处在第几区（`also_read` 级联）
- 收尾看两个结束信号：单周天量＋大利好＝行情结束；缩量见底＝抛压枯竭

**最终回答示例**

> 先别用"横了七个月"直接下结论，按书里的三维证据拆开看。第一，量要除以流通股本：这七个月的周均成交占流通盘几个百分点，和它历史上吸筹、派发时段比是高还是低。第二，数往返：18–22 是 4 个点，按书中口径"5 点以上才算一次"，这个区间本身偏窄，说明更像是窄幅吸筹而不是大区间派发——但前提是量在低位是缩的。第三，看位置：这只票现在离多年旧高旧低哪一端更近，落在七个行动区域的哪一区，直接决定"窄幅小量"该读成吸筹还是"高位滞涨"该读成派发。最后，最近这次放量冲 22 又掉回来，要么是测试上方抛压，要么是诱多，区别在于回落时的量——缩量回落偏前者，放量回落偏后者。按书中前提，现代市场的成交量可被对敲、程序化交易干扰，1920 年代"大盘不可伪造"这条前提不严格成立，所以这里能给的是证据强度评估，不是确定结论。真要动手，位置和止损交给 `support-resistance-stops-skill`，别在这一步定买卖。

### 示例 2：旧底 96，止损放哪

**用户问题**

"我在 104 买进的，前面那个低点是 96，止损放哪？浮盈了要怎么处理？"

**skill 如何判断**

- 入口按主从裁决：问的是点位与止损，主卡 `support-resistance-stops-skill`；趋势方向走 `also_read` 读 `trend-judgment-skill`
- 先复盘旧位再谈止损：调出多年图表，标出所有历史吸筹/派发区与旧顶旧底，同价反复触及要计数（容差 ±1–2 点）
- 挂单位置：买进口径是旧底下方 3 点（周内操作级 1–2 点，合成 1–3 点体系）；做空镜像为旧顶上方 1–3 点
- 委托方式：必须是 G.T.C.（未经取消即有效），与建仓同时挂出，不是事后补
- 两条铁律：绝不取消止损、绝不放宽止损——想承担更大损失时，书里的判断是"99% 的可能是错了"
- 浮盈处理：把止损先推到盈亏平衡，再逐段跟进，绝不让盈利单变亏损单
- 归一化声明：3 点是 1920 年代的价位刻度，直接套到现代市场会失真，必须按波动率换算（这是整理者补丁，不是原书内容）

**最终回答示例**

> 止损锚在结构上，不锚在"我能承受多少"。旧底是 96，按书里的买进口径放在旧底下方 3 点，也就是 93 一带；但这个 3 点是 1920 年代的美元刻度，套到今天的价格上必须归一化——更稳的做法是把它换算成"旧底下方约一个 ATR 或固定百分比"，让 93 这个位置对应到现代的合理宽度，并在下单前把这个换算口径写下来。挂单方式同样重要：建仓的同时就挂 G.T.C. 止损，不是"跌破再手动卖"，因为书里把"不下止损单"列为三大致命错误之一。浮盈之后按规则四处理：先推到成本价（保本），趋势继续有利再逐段跟进。两条不能破：不取消、不放宽——想放宽的那一刻，通常就是判断已经错了。另外提醒一句，止损位只解决"错了损失多少"，"该不该在 104 买"是位置问题，回去看趋势卡和七个行动区域再确认一次。

## 这些 skill 是怎么生成出来的

这套 skill 使用 **[cangjie-skill](https://github.com/kangarooking/cangjie-skill)** 的 RIA-TV++ 流水线生成，整个流程分六个阶段：

1. **整书理解（Adler 分析）**——用 Mortimer Adler 的分析阅读法，对全书做结构、解释、批判、应用四步拆解，产出 [`BOOK_OVERVIEW.md`](./BOOK_OVERVIEW.md)
2. **并行提取**——同时派多个专项提取器（框架、原则、案例、反例、术语），从原文中提取候选方法论单元，本书共得到 381 个候选
3. **三重验证筛选**——每个候选必须通过三项检验：书内至少有 2 处独立佐证（跨域）、能回答书中未明说的新问题（预测力）、不是常识（独特性）；381 个候选中 333 个通过，40 个降为参考域，9 个待复核，1 个否决，结论见 [`verified.md`](./verified.md)
4. **RIA++ 构造**——按 R（原文引用）/ I（用自己的话重写）/ A1（书中案例）/ A2（未来触发场景）/ E（可执行步骤）/ B（边界与盲点）六个维度结构化，381 个单元归并为 12 个能力
5. **Zettelkasten 链接**——找出能力卡之间的依赖、对比、组合关系，生成能力索引与路由表，即 [`bundle/verified.yaml`](./bundle/verified.yaml) 的 `also_read` 字段
6. **触发与输出测试**——为每个入口设计触发盲测题（含诱饵题：该触发时要触发，不该触发时要沉默）与输出评测场景，未通过的卡回炉重做，回炉后再做回归验证

本书还有两处影响蒸馏的特殊情况：一是版本年代错位——封面副题指向 1929—1935，而正文数据与案例止于 1923 年初，拆书引用一律以正文自身表述为准；二是固定点数参数（3 点止损、5–7 点回调、2–3 百万股成交日）绑定 1920 年代价位，复用到现代市场前必须按波动率归一化，这一点写进了每张卡的边界段。

## 测试与验证

本仓库把生成过程的测试材料一起发布：`evals/` 下是 9 个入口的触发用例与逐项评分结果，[`evals/test-results.md`](./evals/test-results.md) 记录了失败与修复的完整过程，不是只留通过记录。

- **触发盲测**：9 个入口共 65 条用例，通过 64 条（98.5%）；其中诱饵（should_not_trigger）17 条，零误触发
- **方法**：3 个干净 sub-agent 盲测 ＋ 主流程判卷，判卷时不提供预期答案
- **唯一失败项**：`gann-trend-theory-skill::should_trigger-03`（判势＋择时复合句）被盲测判给了 `trend-judgment-skill`；修复方式是在 single 入口的 description 里补入该复合场景，不改预期答案
- **输出测试**：9 个入口中 7 个有独立代表任务输出测试，入口与 router 的输出测试覆盖于路由行为
- **已知缺口**（如实记录）：`strength-based-selection-skill` 的独立输出测试是补做的（PASS-with-notes，修 5 处）；`run_trigger_evals.py` 的 train/validation 切分未执行；跨模型复测未做

## 仓库结构

```text
gann-trend-theory-skill/
├── README.md                          ← 你正在看的
├── README.en.md                       ← English version
├── LICENSE                            ← MIT
├── BOOK_OVERVIEW.md                   ← 整书理解（Adler 四步拆解，阶段 0 产出）
├── verified.md                        ← 381 个候选单元的三重验证结论
├── INDEX.md                           ← skill 地图：12 个能力的去向、依赖与加载顺序
├── bundle/                            ← 规范源：能力定义 + 能力卡 + 整书参考
│   ├── verified.yaml                  ← 12 个能力的规范定义（意图/关键词/also_read/去向）
│   ├── cards/                         ← 12 张能力卡规范副本
│   │   ├── trend-judgment-skill.md
│   │   ├── support-resistance-stops-skill.md
│   │   ├── accumulation-distribution-skill.md
│   │   ├── seven-action-zones-skill.md
│   │   ├── strength-based-selection-skill.md
│   │   ├── twelve-trading-rules-skill.md
│   │   ├── pyramid-scaling-skill.md
│   │   ├── entry-exit-timing-skill.md
│   │   ├── news-discounting-skill.md
│   │   ├── tape-review-workflow-skill.md
│   │   ├── failure-mode-triage-skill.md
│   │   └── portfolio-annual-checkup-skill.md
│   └── book/
│       ├── overview.md                ← 整书概览
│       └── glossary.md                ← 术语表
├── single/                            ← 单一入口模式
│   └── gann-trend-theory-skill/
│       ├── SKILL.md                   ← 入口：触发条件 + 路由表 + 加载规则
│       ├── BUILD_MANIFEST.json        ← 编译清单与文件哈希
│       └── references/
│           ├── overview.md
│           ├── capability-index.md    ← 完整意图与关键词索引
│           ├── cheatsheet.md          ← 决策规则速查
│           ├── glossary.md
│           └── capabilities/          ← 12 张能力卡（与 bundle/cards 同名）
├── pack/                              ← 多入口模式（compact pack）
│   ├── BUILD_MANIFEST.json
│   ├── capability-destinations.json   ← 12 个能力各自的去向
│   ├── gann-trend-theory-skill-router/
│   │   ├── SKILL.md                   ← 来源路由入口
│   │   └── references/
│   │       ├── overview.md
│   │       ├── capability-index.md
│   │       ├── cheatsheet.md
│   │       ├── glossary.md
│   │       └── capabilities/          ← 12 张能力卡，供 router 内部调用
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
└── evals/                             ← 触发与输出测试材料
    ├── test-results.md                ← 逐项评分与失败修复记录
    ├── gann-trend-theory-skill.json
    ├── gann-trend-theory-skill-router.json
    ├── trend-judgment-skill.json
    ├── support-resistance-stops-skill.json
    ├── accumulation-distribution-skill.json
    ├── strength-based-selection-skill.json
    ├── twelve-trading-rules-skill.json
    ├── entry-exit-timing-skill.json
    └── failure-mode-triage-skill.json
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

装完问一句"我在 104 买进、旧底 96，止损放哪"，看 agent 是否直接进入止损锚定与 G.T.C. 挂单的核算流程，而不是给你一段泛泛的技术分析。装的是 single 时，它会先读入口再按路由表进能力卡；装的是 pack 时，对应能力会被直接命中。

## 来源

- 《江恩股市趋势理论》（New Stock Trend Detector）威廉·D.江恩（William D. Gann）著

## 声明

本仓库只发布蒸馏后的 skill、索引与规则速查材料，不包含原书 PDF、EPUB、OCR 文件、截图或全书转写稿。能力卡中出现的原文引用仅用于标注方法论出处和保持可审计性。

书中所有数字判据（3 点止损、5–7 点回调、区间往返 10–20 次、2–3 百万股成交日等）都是 1920 年代市场条件下的案例与经验归纳，原书未提供统计回测背书，也不能直接套用到现代市场；复用时须按波动率与流通盘归一化，并声明换算口径。本仓库内容不构成投资建议。


## License

[MIT](./LICENSE)
