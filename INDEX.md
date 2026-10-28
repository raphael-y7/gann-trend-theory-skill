# Skill 地图 — 江恩股市趋势理论

一本书蒸馏出的 12 个能力单元：其中 7 个在 pack 模式下晋级为独立 skill，另 5 个由来源路由入口 `gann-trend-theory-skill-router` 承接。本页是它们的关系图、去向与加载顺序，内容逐项取自 [`bundle/verified.yaml`](./bundle/verified.yaml)。

## 能力总表

| capability_id | slug | 中文标题 | 重要度 | 去向 |
|---|---|---|---|---|
| `cap.gann-trend-theory-skill.trend-judgment-skill` | `trend-judgment-skill` | 趋势判断（多周期+累进高低位+突破旧位） | high | promoted → 独立 skill |
| `cap.gann-trend-theory-skill.support-resistance-stops-skill` | `support-resistance-stops-skill` | 支撑/阻力复盘与止损体系 | high | promoted → 独立 skill |
| `cap.gann-trend-theory-skill.accumulation-distribution-skill` | `accumulation-distribution-skill` | 吸筹/派发识别（量价×区间×时间三维） | high | promoted → 独立 skill |
| `cap.gann-trend-theory-skill.seven-action-zones` | `seven-action-zones` | 七个行动区域位置判别 | medium | router → 路由入口 |
| `cap.gann-trend-theory-skill.strength-based-selection-skill` | `strength-based-selection-skill` | 强弱判别与选股 | high | promoted → 独立 skill |
| `cap.gann-trend-theory-skill.twelve-trading-rules-skill` | `twelve-trading-rules-skill` | 十二条交易规则与资金管理 | critical | promoted → 独立 skill |
| `cap.gann-trend-theory-skill.pyramid-scaling` | `pyramid-scaling` | 金字塔式加码 | high | router → 路由入口 |
| `cap.gann-trend-theory-skill.entry-exit-timing-skill` | `entry-exit-timing-skill` | 买卖点位与时机 | critical | promoted → 独立 skill |
| `cap.gann-trend-theory-skill.news-discounting` | `news-discounting` | 消息贴现处理 | high | router → 路由入口 |
| `cap.gann-trend-theory-skill.tape-review-workflow` | `tape-review-workflow` | 看盘复盘工作流 | high | router → 路由入口 |
| `cap.gann-trend-theory-skill.failure-mode-triage-skill` | `failure-mode-triage-skill` | 失败模式排障检查表 | critical | promoted → 独立 skill |
| `cap.gann-trend-theory-skill.portfolio-annual-checkup` | `portfolio-annual-checkup` | 持仓年度体检 | medium | router → 路由入口 |

- **7 个 promoted**：`trend-judgment-skill`、`support-resistance-stops-skill`、`accumulation-distribution-skill`、`strength-based-selection-skill`、`twelve-trading-rules-skill`、`entry-exit-timing-skill`、`failure-mode-triage-skill`——在 pack 里各自是带 `SKILL.md` 的独立目录，可被 description 直接命中。
- **5 个 router**：`seven-action-zones`、`pyramid-scaling`、`news-discounting`、`tape-review-workflow`、`portfolio-annual-checkup`——不单独成 skill，卡片仍放在入口的 `references/capabilities/` 里，由路由表按需加载。
- 每张卡都在 [`bundle/cards/`](./bundle/cards) 留了一份规范副本（12 个文件），`verified.yaml` 的 `capabilities` 也是 12 条，两边一一对应。

## 依赖关系

依赖来自 `verified.yaml` 每个能力的 `also_read` 字段（有向：A 的 `also_read` 含 B，表示做 A 的事时 B 会被级联读取）。共 35 条边。

| 能力（slug） | also_read（会被级联加载） |
|---|---|
| `trend-judgment-skill` | `support-resistance-stops-skill`、`accumulation-distribution-skill`、`seven-action-zones` |
| `support-resistance-stops-skill` | `trend-judgment-skill`、`accumulation-distribution-skill`、`pyramid-scaling` |
| `accumulation-distribution-skill` | `trend-judgment-skill`、`seven-action-zones`、`support-resistance-stops-skill` |
| `seven-action-zones` | `trend-judgment-skill`、`accumulation-distribution-skill` |
| `strength-based-selection-skill` | `trend-judgment-skill`、`accumulation-distribution-skill`、`entry-exit-timing-skill` |
| `twelve-trading-rules-skill` | `support-resistance-stops-skill`、`pyramid-scaling`、`portfolio-annual-checkup` |
| `pyramid-scaling` | `support-resistance-stops-skill`、`twelve-trading-rules-skill`、`failure-mode-triage-skill` |
| `entry-exit-timing-skill` | `trend-judgment-skill`、`support-resistance-stops-skill`、`failure-mode-triage-skill` |
| `news-discounting` | `accumulation-distribution-skill`、`support-resistance-stops-skill`、`portfolio-annual-checkup` |
| `tape-review-workflow` | `trend-judgment-skill`、`accumulation-distribution-skill`、`twelve-trading-rules-skill` |
| `failure-mode-triage-skill` | `twelve-trading-rules-skill`、`support-resistance-stops-skill`、`entry-exit-timing-skill` |
| `portfolio-annual-checkup` | `strength-based-selection-skill`、`support-resistance-stops-skill`、`failure-mode-triage-skill` |

被引用次数（入度）标出三处枢纽，可据此判断先读哪张：

- `support-resistance-stops-skill`（8 次）、`trend-judgment-skill`（6 次）、`accumulation-distribution-skill`（6 次）——判势、止损、吸筹派发是全书的地基，几乎每个能力都会回读。
- `twelve-trading-rules-skill`、`failure-mode-triage-skill`（各 3 次）——仓位纪律与排障是执行层的兜底。
- `news-discounting`、`tape-review-workflow` 入度为 0：它们是入口级能力，不被别的卡级联，只能被路由表直接命中。

## 加载顺序

1. **先读入口 SKILL.md**。装 single 时读 `single/gann-trend-theory-skill/SKILL.md`；装 pack 时读 `pack/gann-trend-theory-skill-router/SKILL.md`，若问题正好命中某个 promoted 能力，则直接读那个 skill 的 `SKILL.md`。
2. **先过判停，再匹配意图**。入口会先检查 `out_of_scope` 与 `stop_conditions`（要求预测具体点位、保证盈利的请求在这里就被拦下），之后才匹配能力意图。
3. **按路由表加载 1–2 张卡**。单次任务最多加载 2 张：主卡由意图决定，第二张取该卡 `also_read` 里最贴合的那一条。复合意图（例如"止损设哪＋拿多少钱买"）按主从裁决——资金/仓位归 `twelve-trading-rules-skill`，点位/止损归 `support-resistance-stops-skill`，其余走 `also_read` 级联。
4. **卡内再读 `references/`**。术语不明查 `glossary.md`，要规则速查查 `cheatsheet.md`，要整书语境查 `overview.md`，要完整意图与关键词索引查 `capability-index.md`。
