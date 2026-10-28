---
name: gann-trend-theory-skill
description: |
  当用户带着《江恩股市趋势理论》（威廉·D.江恩，New Stock Trend Detector，正文1923年）的方法论做股票投资分析时使用：判断趋势与顶底结构（多周期图表、累进高低位、突破旧位）、复盘支撑阻力并锚定止损、识别吸筹/派发（量价×区间×时间）、七个行动区域定位、强弱判别与选股（相对强度、突破上年高点名单）、十二条交易规则与资金管理、金字塔加码、买卖点位与时机、消息贴现处理、看盘复盘工作流、失败模式排障、持仓年度体检。适用问题如“这波是吸筹还是出货”“止损设哪”“该不该追新高”“这条消息怎么解读”“仓位怎么管理”“我又亏了，错在哪”。不适用于：与本方法论无关的通用财经问答、基本面估值建模（原书明确否定账面价值路线）、日内高频交易执行、具体未来点位预测（时间周期算法原书未公开且不可检验）。
metadata:
  cangjie.generated-by: cangjie-tools v2.5.0
  cangjie.variant: single
  cangjie.bundle-id: bundle.gann-trend-theory-skill
  cangjie.capability-count: 12
  cangjie.entrypoint-count: 1
---
# 江恩股市趋势理论（专业解读版） — 全书能力入口

## 触发与不触发

**适用**：与本书能力域相关的咨询与任务（见下方路由表的意图列）。
**不适用**：
- 与本书方法论无关的通用财经问答与基本面估值建模（原书否定账面价值路线）
- 日内高频交易执行与具体未来点位预测（时间周期算法原书未公开）
- 期货专有操作细则（交割选择、季节性等仅作参考域）

## 核心原则（常驻速览，概览类问题读到这里即可回答）

1. 价格由供求决定；大行情前必有长时间的吸筹或派发，痕迹留在价位区间、时间、成交量三者上。
2. 趋势=顶底节节抬高/降低；月周定方向、日线只择时；突破旧位入新区间，二次新高比第一次更安全。
3. 每笔交易必须挂止损单：旧底下方3点/旧顶上方1—3点，G.T.C.，绝不取消或放宽，浮盈后上移保护利润；三大致命错误=过度交易、不下止损单、摊薄亏损。
4. 顺势而为：熊市反弹做空、牛市回挡做多；拿不准就退出。
5. 金字塔加码逐级减量（100→50→30→20→10）、只顺浮盈方向；吸筹派发区内禁止加码。
6. 消息几乎总是已被贴现：利好出现而股价下跌=已贴现；图表与消息抵触时信图表。
7. 固定点数参数绑定1920年代价位，用于现代市场前必须按波动率/流通盘归一化（换算非原书内容）。

## 能力路由（先读本表，按意图加载 1 张能力卡）

| 用户意图 | 先读 | 补读/备注 |
|---|---|---|
| 判断这只股票/指数现在是涨势还是跌势；横盘很久突然放量突破，是不是大行情起点；创新高能追吗，会不会是假突破；月线周线日线信号矛盾该信哪个；复盘高低点序列给个股画趋势结构 | references/capabilities/trend-judgment-skill.md | references/capabilities/support-resistance-stops-skill.md、references/capabilities/accumulation-distribution-skill.md、references/capabilities/seven-action-zones.md |
| 这笔交易的止损设在哪儿、放多宽；这个价位是支撑还是阻力、破了怎么办；浮盈了怎么用移动止损保护利润；被止损出局后什么条件可以再入场；这个关键位历史上被测试过几次 | references/capabilities/support-resistance-stops-skill.md | references/capabilities/trend-judgment-skill.md、references/capabilities/accumulation-distribution-skill.md、references/capabilities/pyramid-scaling.md |
| 这只票横盘数月，是在吸筹还是派发/洗盘还是出货；放量滞涨、单周天量还能拿吗；高位宣布增加股息/额外派息意味着什么；连跌后缩量横盘，抛压是否枯竭、能不能进场；用成交量和流通股本独立核验主力出货说法 | references/capabilities/accumulation-distribution-skill.md | references/capabilities/trend-judgment-skill.md、references/capabilities/seven-action-zones.md、references/capabilities/support-resistance-stops-skill.md |
| 现在市场是高位还是低位、贵不贵；涨了这么多是不是过热、该不该清仓；跌成这样是不是底部区域、能开始抄底吗；无消息跳空低开、利好频出说明什么；给仓位决策定一个贪婪/恐惧的位置语境 | references/capabilities/seven-action-zones.md | references/capabilities/trend-judgment-skill.md、references/capabilities/accumulation-distribution-skill.md |
| 在候选股票池里筛选最强/最弱标的并排序；按突破上年高点（52周新高）做年度动量名单；判断某股相对大盘/板块是强是弱、要不要换仓；为做空筛选安全标的；识别新股、昔日领头股、攻旧高不克等选股陷阱 | references/capabilities/strength-based-selection-skill.md | references/capabilities/trend-judgment-skill.md、references/capabilities/accumulation-distribution-skill.md、references/capabilities/entry-exit-timing-skill.md |
| 制定仓位与资金管理计划（买多少、一次最多亏多少）；设计跨类别4-5只等量的分散持股组合；排查过度交易/摊薄亏损/无止损等致命行为；评估是否应为分红买进或持有高息股；连续亏损后判断能否继续交易与扩大规模 | references/capabilities/twelve-trading-rules-skill.md | references/capabilities/support-resistance-stops-skill.md、references/capabilities/pyramid-scaling.md、references/capabilities/portfolio-annual-checkup.md |
| 制定顺势金字塔加码计划（数量序列与间隔）；判断是否具备加码资格（脱离吸筹/派发区、首次转向）；区分顺势加码与摊薄亏损（浮亏加码一律否决）；设定每档加码的止损跟进与停止条件 | references/capabilities/pyramid-scaling.md | references/capabilities/support-resistance-stops-skill.md、references/capabilities/twelve-trading-rules-skill.md、references/capabilities/failure-mode-triage-skill.md |
| 判断当前应买入、卖出还是等待的位置；制定极端位后两日回调买进计划；决定行情启动时是否立即追入（不等回落）；用获利四问决定是否止盈、拒绝预设目标价；大利润后执行作壁上观空仓纪律 | references/capabilities/entry-exit-timing-skill.md | references/capabilities/trend-judgment-skill.md、references/capabilities/support-resistance-stops-skill.md、references/capabilities/failure-mode-triage-skill.md |
| 利好/利空消息公布后该买还是该卖；股息降低/提高、停息与增发事件怎么解读；突发利空大幅低开后的应对流程；评估报纸、权威言论与内幕消息的可信度 | references/capabilities/news-discounting.md | references/capabilities/accumulation-distribution-skill.md、references/capabilities/support-resistance-stops-skill.md、references/capabilities/portfolio-annual-checkup.md |
| 建立每日记录与每周复盘流程；诊断盯盘被日内行情反复洗出的毛病；判断日线信号可信度与多周期权重；无成交量数据时判断有无大资金活动 | references/capabilities/tape-review-workflow.md | references/capabilities/trend-judgment-skill.md、references/capabilities/accumulation-distribution-skill.md、references/capabilities/twelve-trading-rules-skill.md |
| 亏损后归因：这笔交易错在哪；判断当前操作是否属于已知失败模式；开仓前自查（风险/位置/信息源）；止损、补仓摊薄、对锁等纠结的处置 | references/capabilities/failure-mode-triage-skill.md | references/capabilities/twelve-trading-rules-skill.md、references/capabilities/support-resistance-stops-skill.md、references/capabilities/entry-exit-timing-skill.md |
| 年度/季度持仓体检与清仓判定；高息债券/高息股的风险预警；评估代销/承销机构名声的担保力；投资仓与投机仓的风险错配检查 | references/capabilities/portfolio-annual-checkup.md | references/capabilities/strength-based-selection-skill.md、references/capabilities/support-resistance-stops-skill.md、references/capabilities/failure-mode-triage-skill.md |

**非能力类查询**：
- 书名/作者/章节/整书概览 → references/overview.md
- 术语解释 → references/glossary.md
- 决策规则速查（不需要原文依据时） → references/cheatsheet.md
- 完整意图与关键词索引（本表未覆盖的意图先查这里） → references/capability-index.md

## 加载规则

- 每次任务先读本文件，再按路由表加载 **1** 张能力卡；任务明确跨域时最多加载 2 张。
- 概览/书名类问题不加载能力卡，用「核心原则」与 overview.md 回答。
- 路由表与 capability-index.md 都无法命中的意图，明确告知超出本书范围，不要硬套。

## 边界与判停

- 用户要求保证盈利或确定点位预测时：声明本方法论无统计检验、作者断言不可证伪，不提供保证。
- 拒绝把1920年代固定点数（3-5点止损、5-7点回调等）直接套用于现代市场，必须先归一化并声明换算为整理者补丁。
- 吸筹/派发判断在现代市场只能作证据强度评估（量价可被伪造的前提差异），不得当作确定结论。
- 原书数据存在两写矛盾（如鲍德温62.375年份、小麦126.875/126.75），引用时按“原文两写”呈现，不得静默采信一方。
- 路由顺序：先检查本节与 out_of_scope（拒答类），再匹配能力意图；凡含“预测点位/保证盈利”类请求直接触发第一条判停，不进入能力匹配。
- 复合意图句（如“止损设哪+拿多少钱买”）按主从裁决：资金/仓位类主卡 twelve-trading-rules-skill，点位/止损类主卡 support-resistance-stops-skill，其余能力经 also_read 级联，单次任务最多加载 2 张卡。
