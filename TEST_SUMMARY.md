# Stage 4 压力测试摘要

> 本书：《江恩股市趋势理论（专业解读版）》（*New Stock Trend Detector*）
> 数据来源：归档 `审计过程/test-prompts/`（9 份用例）、`审计过程/test-results.md`（盲测评分）、`审计过程/PIPELINE_STATE.md`（阶段 4 记录）。本文件只汇总，不新增结论。

## 测试范围

- **skill 数量**：9 个入口。1 个 single 入口（`gann-trend-theory-skill`）、1 个 pack 来源路由入口（`gann-trend-theory-skill-router`）、7 个 pack 晋级独立 skill（trend-judgment、support-resistance-stops、accumulation-distribution、strength-based-selection、twelve-trading-rules、entry-exit-timing、failure-mode-triage）。
- **test-prompts 文件**：9 份，共 **65 条用例**。每份随所属 skill 目录发布为 `test-prompts.json`。
- **覆盖类型**（按用例文件里的 `type` 字段统计）：

| 类型 | 条数 | 说明 |
|---|---|---|
| `should_trigger` | 36 | 该触发时必须触发，含复合问题（判势＋择时、吸筹＋止损、排障＋资金管理） |
| `should_not_trigger` | 18 | 诱饵题：无关领域（写脚本）、越界请求（预测点位）等，必须沉默 |
| `edge_case` | 11 | 元问题与已知来源缺口（时间周期算法原书不公开、成书年代口径） |
| `output_case` | 0 | 用例 JSON 中**不存在**该 type；输出测试不走 JSON，按 [`test-results.md`](./test-results.md) 的「输出测试」列逐卡记录 |

逐入口用例分布：

| 入口 | 用例数 | should_trigger | should_not_trigger | edge_case |
|---|---|---|---|---|
| gann-trend-theory-skill | 7 | 3 | 2 | 2 |
| gann-trend-theory-skill-router | 8 | 5 | 2 | 1 |
| trend-judgment-skill | 8 | 4 | 2 | 2 |
| support-resistance-stops-skill | 7 | 4 | 2 | 1 |
| accumulation-distribution-skill | 7 | 4 | 2 | 1 |
| strength-based-selection-skill | 7 | 4 | 2 | 1 |
| twelve-trading-rules-skill | 7 | 4 | 2 | 1 |
| entry-exit-timing-skill | 7 | 4 | 2 | 1 |
| failure-mode-triage-skill | 7 | 4 | 2 | 1 |

## 结构检查

以下为对仓库当前文件的实测结果（2026-10-29 复核）：

- **JSON 可解析性**：全仓 12 个 JSON 全部可解析，0 失败。构成为 9 份 `test-prompts.json`、`pack/BUILD_MANIFEST.json`、`pack/capability-destinations.json`、`single/gann-trend-theory-skill/BUILD_MANIFEST.json`。
- **frontmatter**：9 份 `SKILL.md` 全部带 YAML frontmatter，`name` 字段与所在目录名一致（含 `-router` 后缀）。
- **六段完整性**：`bundle/cards/` 下 12 张能力卡均含 R（原文）/ I（自述）/ A1（书中案例）/ A2（未来触发）/ E（执行步骤）/ B（边界）六段，无缺段；`single` 与 `pack` 的 `references/capabilities/` 为同名副本。
- **用例自洽**：每份 `test-prompts.json` 的 `skill` 字段与其所在目录名一致；`id` 前缀与 `type` 字段一一对应（`should_trigger-NN` / `should_not_trigger-NN` / `edge_case-NN`）。
- **一处原文笔误（已如实记录，未改动原文件）**：[`test-results.md`](./test-results.md) 正文写「诱饵（should_not_trigger）：共 17 条」，但其表格逐行相加为 18 条，用例文件实测也是 18 条。以 18 条为准，正文的 17 应为笔误。

## 结果

- skills: 9
- test_json: 9
- **通过情况：64 / 65（98.5%）**，诱饵 18 条零误触发。方法为 3 个干净 sub-agent 盲测 ＋ 主流程判卷（判卷时不提供预期答案）。
- 唯一失败项：`gann-trend-theory-skill::should_trigger-03`（判势＋择时复合句）被盲测判给 `trend-judgment-skill`；修复方式是在 single 入口的 `description` 补入该复合场景，不改预期答案。
- 已记录的缺口（原样转录，未粉饰）：
  - `strength-based-selection-skill` 的独立输出测试为补做（PASS-with-notes，修 5 处卡片缺口），触发测试本身通过。
  - `run_trigger_evals.py` 的 train/validation 切分未执行（`eval-suite.json` 里 `split_seed=42`、`train_ratio=0.6` 已定义，但未实际运行）。
  - 跨模型复测未做。

## 可接入 darwin-skill 的后续动作

1. **作为回归样本直接接入**：9 份 `test-prompts.json` 已是「skill 名 → 用例」的现成映射，可直接作为 darwin-skill 的触发回归集，无需再加工。判分口径沿用原文：`should_trigger` 必须命中本 skill、`should_not_trigger` 必须沉默、`edge_case` 必须按既定边界作答而非硬套能力卡。
2. **改 `description` 后必跑**：本次唯一失败项的根因是入口 description 的覆盖不足，说明触发类改动对 description 最敏感。任何对 `SKILL.md` frontmatter `description` 的修改，都应重跑该入口的 7—8 条用例。
3. **补齐 train/validation 切分**：`eval-suite.json` 已给出切分参数但未执行，接入时应补上多次采样的 train/validation 划分，避免同一批题既调 description 又用来验收。
4. **补跨模型复测**：现有结果只来自单模型下的 sub-agent 盲测，跨模型一致性未验证，属已知缺口。
5. **输出测试独立化**：输出质量目前靠 `test-results.md` 的人工记录，尚未固化成可自动判分的 `output_case`。若要长期回归，建议把这些场景转成带评分点的 JSON 用例。
