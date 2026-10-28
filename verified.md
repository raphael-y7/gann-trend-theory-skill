# verified.md — 阶段 1.5 三重验证汇总

判定日期：2026-10-11。详细逐单元判定表见 verified-part1/2/3.md（审计过程归档）。

## 总量与分流

| 候选域 | 单元数 | verified | reference | needs_review | rejected |
|---|---|---|---|---|---|
| 框架（candidates/frameworks.md） | 38 | 30 | 6 | 1 (f13) | 1 (f33) |
| 原则/口径（candidates/principles.md） | 136 | 112 | 24 | 0 | 0 |
| 案例（candidates/cases.md） | 87 | 73 | 6 | 8 | 0 |
| 反例（candidates/counter-examples.md） | 37 | 35 | 2 | 0 | 0 |
| 术语（candidates/glossary.md） | 83 | 83（抽验36条全过，g49/g33 微修） | — | — | — |
| **合计** | **381** | **333** | **38** | **9** | **1** |

> 计数口径：f13（needs_review）与 f33（rejected）单独计列，不重复计入 reference 栏，故 reference 合计为 38，且 381 = 333 + 38 + 9 + 1。各域单元数与 `candidates/` 下实测条目数一致（38 / 136 / 87 / 37 / 83）。

## 能力级归并骨架（阶段 1.6 采纳版，12 个能力）

验证阶段骨架为 F1–F15；按"参数层并入相邻能力"的验证结论（F5/F9/F12 内容薄、与相邻能力交叠），定案为 12 个能力级单元：

| # | capability_id | slug | 名称 | 吸收的验证骨架 | 依据（verified 单元数） |
|---|---|---|---|---|---|
| 1 | C01-trend-judgment-skill | trend-judgment-skill | 趋势判断（多周期+累进高低位+突破旧位） | F1 + F5 顶底形态部分 | 框架4+原则10 |
| 2 | C02-levels-and-stops | support-resistance-stops-skill | 支撑/阻力复盘与止损体系 | F2 + F8 | 框架2+原则10 |
| 3 | C03-accumulation-distribution-skill | accumulation-distribution-skill | 吸筹/派发识别（量价×区间×时间） | F3 + F5 派发位置/时间部分 | 框架3+原则19 |
| 4 | C04-seven-zones | seven-action-zones | 七个行动区域位置判别 | F4 | 框架2+原则4 |
| 5 | C05-strength-selection | strength-based-selection-skill | 强弱判别与选股 | F6 | 框架2+原则12 |
| 6 | C06-twelve-rules-capital | twelve-trading-rules-skill | 十二条交易规则与资金管理 | F7（含资本分档/均摊风险） | 框架4+原则12 |
| 7 | C07-pyramid-scaling | pyramid-scaling | 金字塔式加码 | F9 | 框架2+原则2+例题3 |
| 8 | C08-entry-exit-timing-skill | entry-exit-timing-skill | 买卖点位与时机 | F10 + F12 作壁上观/数周确认 + f13 | 框架6+原则11 |
| 9 | C09-news-discounting | news-discounting | 消息贴现处理 | F11 | 框架2+原则10 |
| 10 | C10-tape-review-workflow | tape-review-workflow | 看盘复盘工作流（不盯盘+记录粒度+盘速判量） | F14 | 框架3+原则7 |
| 11 | C11-failure-triage | failure-mode-triage-skill | 失败模式排障检查表 | F13 ← 35 条 verified 反例 | 反例35 |
| 12 | C12-portfolio-checkup | portfolio-annual-checkup | 持仓年度体检（投资看护） | F15 | 框架2+原则9 |

reference 类 38 项去向：期货专有 17 项 → 能力卡"参考域 R"段；7 项股票侧历史节奏/不可核查断言 → BOOK_OVERVIEW 第 5 节；术语→GLOSSARY；D 级轶事 6 项 → 卡片背景叙述。明细见 references.md。

## 抽查与质量记录

- 框架+反例域：50+ 处原文定位复核（含"18 只名单"清点、"不泄漏这一秘密"证实、账面价值 250 美元等）。
- 原则域：55 处逐字抽查一致；136 单元逐一判定无批量通过。
- 案例域：87 例全部回原文比对，约 40 例数据链逐点核对；c07 斯图特贝克 30+ 数据点全符。
- 术语域：36 条重点抽验全部通过；单位口径表验算成立（棉 40 点=200 美元/手、粮 4 点×5000 蒲=200 美元）。
