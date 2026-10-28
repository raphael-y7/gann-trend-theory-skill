# test-results.md — 全书 9 个入口汇总

- 总用例：65 条；通过 64 条（98.5%）
- 诱饵（should_not_trigger）：共 17 条，零误触发
- 方法：3 个干净 sub-agent 盲测 + 主流程判卷（不给预期答案）

| skill | 通过 | should_trigger | should_not_trigger | edge_case | 输出测试 |
|---|---|---|---|---|---|
| gann-trend-theory-skill | 6/7 | 3 | 2 | 2 | 覆盖于路由 |
| gann-trend-theory-skill-router | 8/8 | 5 | 2 | 1 | 覆盖于路由 |
| trend-judgment-skill | 8/8 | 4 | 2 | 2 | 有 |
| support-resistance-stops-skill | 7/7 | 4 | 2 | 1 | 有 |
| accumulation-distribution-skill | 7/7 | 4 | 2 | 1 | 有 |
| strength-based-selection-skill | 7/7 | 4 | 2 | 1 | 有（补做，PASS-with-notes，修5处） |
| twelve-trading-rules-skill | 7/7 | 4 | 2 | 1 | 有 |
| entry-exit-timing-skill | 7/7 | 4 | 2 | 1 | 有 |
| failure-mode-triage-skill | 7/7 | 4 | 2 | 1 | 有 |

## 失败项与修复
- `gann-trend-theory-skill::should_trigger-03`（判势+择时复合）：盲测判给 trend-judgment-skill。修复：在 single 入口 description 补入该复合场景（不改预期答案）。

## 缺口
- strength-based-selection-skill 未做独立代表任务输出测试（触发测试通过）。
- run_trigger_evals.py 的 train/validation 切分未执行（需多次采样）。
- 跨模型复测未做。
