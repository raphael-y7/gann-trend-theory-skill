<h1 align="center">Gann Trend Theory Skill</h1>

<p align="center"><a href="README.md">中文</a> | English</p>

An AI skill pack for immediate use — it distills the operating system in William D. Gann's *New Stock Trend Detector*: review old highs and lows with monthly/weekly/daily movement charts, volume and time, judge the trend and whether a range is accumulation or distribution, then control risk with stop orders, capital management and pyramid scaling. The result is 12 capability cards that can be triggered individually or combined.

It is not a book summary, nor a reading response — it breaks the reusable methodology in the book into skill modules that can be triggered, executed and tested.

## What these skills solve

- A stock has moved sideways for months and you cannot tell accumulation from distribution, so you wait for the breakout and buy into what turns out to be distribution
- You know you "need a stop" but cannot say where it goes or how wide it should be; after being stopped out once you dare not re-enter, and you do not know what condition would justify it
- Monthly, weekly and daily signals contradict each other and you do not know which timeframe to trust; you dare not chase a new high for fear of a false breakout, and you fear missing the main move
- You hold a list of candidates, cannot rank which one to buy first, and cannot decide whether to sell the weak ones for the strong ones
- Good news arrives and the stock falls; you cannot decide whether to trust the news or the chart. After a sudden shock gaps the stock down, you do not know whether to act that day
- After a loss you can only conclude "my mindset was bad", cannot name the rule you broke, and repeat it next time

## What was distilled

12 capability cards, organized in the order "judge the trend first, locate the level second, manage the money last". 7 of them become standalone skills in the pack build; the other 5 stay inside the router entry and are loaded on demand:

- **Trend and location** (4 cards): `trend-judgment-skill` (multi-timeframe charts, progressive highs and lows, breaks of old levels), `support-resistance-stops-skill` (support/resistance review and the stop-loss system), `accumulation-distribution-skill` (accumulation/distribution across volume × range × time), `seven-action-zones` (locating the seven action zones)
- **Selection and timing** (2 cards): `strength-based-selection-skill` (relative strength, the "broke last year's high" list, sell the weak and buy the strong), `entry-exit-timing-skill` (buy 10 points above the low, sell 10 points below the top, the four profit questions, when in doubt stay out)
- **Position, discipline and triage** (3 cards): `twelve-trading-rules-skill` (the twelve trading rules and capital management), `pyramid-scaling` (scale in with decreasing size, 100→50→30→20→10), `failure-mode-triage-skill` (the three fatal errors plus 35 verified failure modes)
- **News, workflow and portfolio care** (3 cards): `news-discounting` (how news is already priced in), `tape-review-workflow` (do not watch the tape, three chart layers, divide volume by shares outstanding), `portfolio-annual-checkup` (annual portfolio checkup)

The full definition of every card (trigger intents, keywords, dependencies, destination) lives in [`bundle/verified.yaml`](./bundle/verified.yaml); the dependency graph and loading order are in [`INDEX.md`](./INDEX.md).

## Two packaging modes: single and pack

The same 12 capability cards are compiled twice, at two granularities. The content is identical; the only difference is how many entries an agent can discover.

| | single (one entry) | pack (compact pack, multiple entries) |
|---|---|---|
| Discoverable entries | **1**: `gann-trend-theory-skill` | **8**: one source router + 7 promoted standalone skills |
| Where the 12 cards live | All inside the entry's `references/capabilities/`, loaded 1–2 at a time by the router table | 7 high-frequency cards become standalone skills; the other 5 stay in the router's `references/` |
| Triggering | Only the entry description participates in matching; routing happens after entry | The 7 high-frequency capabilities are matched directly, one hop fewer |
| Upgrades | Replace 1 directory | Replace 8 directories |

The 7 cards promoted to standalone skills in the pack:

- `trend-judgment-skill` — trend judgment
- `support-resistance-stops-skill` — support/resistance review and stops
- `accumulation-distribution-skill` — accumulation/distribution detection
- `strength-based-selection-skill` — relative strength and stock selection
- `twelve-trading-rules-skill` — the twelve rules and capital management
- `entry-exit-timing-skill` — entry and exit timing
- `failure-mode-triage-skill` — failure-mode triage checklist

The 5 that stay in the router: `seven-action-zones`, `pyramid-scaling`, `news-discounting`, `tape-review-workflow`, `portfolio-annual-checkup`.

### Which one to install

Pick by the way you work, and **install only one**:

| How you work | Recommended | Why |
|---|---|---|
| You use DSH / Codex / Claude Code with a skills directory and want a clean list | single | Takes 1 slot, loses no capabilities |
| Your daily questions concentrate on "which way is this trending / where is my stop / is this accumulation or distribution / which stock do I buy / how much capital to commit / can I buy now / where did I go wrong" | pack | Those are exactly the promoted standalone skills, matched directly |
| You distribute to several agents or teammates who pick what they need | pack | They can install only the standalone skills they want |
| You want to install once and maintain one directory | single | Upgrades replace a single directory |

> Both builds come from the same bundle and carry identical capabilities. **Installing both will double-trigger**, so pick one.

## Worked examples

### Example 1: seven months sideways — accumulation or distribution?

**User question**

"This stock has been stuck between 18 and 22 for seven months. Last week it broke 22 on heavy volume and fell straight back. Accumulation or distribution?"

**How the skill reasons**

- The entry runs its stop conditions first: this asks for a range assessment, not a price prediction, so it proceeds; the question enters `accumulation-distribution-skill`
- Volume must be divided by shares outstanding: the unit of reading is turnover, not absolute share count — the book anchors this on U.S. Steel's 5 million shares and "more than a million shares must change hands before a big move"
- Range counting: a round trip of 5 points or more counts once; 10–20 round trips without breaking the range is accumulation or distribution, and location decides which
- Location decides the label: narrow range and small volume near the lows leans accumulation; heavy volume churning near the highs leans distribution — the `seven-action-zones` card is pulled in through `also_read`
- Two ending signals close the read: a single week of record volume plus great news marks the end of a move; shrinking volume at the low means selling pressure is exhausted

**Example answer**

> Do not settle this from "seven months sideways" alone — split it into the book's three dimensions. First, divide volume by shares outstanding: what percentage of the float traded per week over these seven months, and is that high or low against this stock's own accumulation and distribution periods. Second, count round trips: 18–22 is a 4-point range, and the book's counting rule only credits moves of 5 points or more, so the range itself is narrow — that points to narrow-range accumulation rather than wide-range distribution, but only if volume shrank while the price was low. Third, check location: is this stock nearer its multi-year old high or old low, and which of the seven action zones is it in? That alone decides whether "narrow range, small volume" reads as accumulation or as "stalling at the top" reading as distribution. Finally, the break of 22 that fell back is either a test of overhead supply or a trap; the difference is the volume on the way down — shrinking volume favours the first, expanding volume the second. Note the book's premise that "the tape cannot be faked" does not strictly hold in a modern market with wash trading and algorithmic flow, so what you get here is an evidence-strength assessment, not a verdict. If you are going to act, location and the stop belong to `support-resistance-stops-skill` — do not set the trade here.

### Example 2: bought at 104, old low is 96 — where does the stop go?

**User question**

"I bought at 104. The previous low is 96. Where do I put the stop, and what do I do once I have a profit?"

**How the skill reasons**

- The entry resolves the mixed intent: this is about a level and a stop, so the primary card is `support-resistance-stops-skill`; trend direction is read through `also_read` into `trend-judgment-skill`
- Review old levels before discussing the stop: pull the multi-year chart, mark every historical accumulation and distribution zone and every old top and bottom; repeated touches at the same price are counted, with a tolerance of ±1–2 points
- Where the order goes: on the long side, 3 points below the old bottom (1–2 points for week-long operations; the combined system is 1–3 points); the short side is the mirror, 1–3 points above the old top
- Order type: it must be G.T.C. (good till cancelled), placed together with the entry, not added afterwards
- Two iron rules: never cancel the stop, never widen it — when you want to take a bigger loss, the book's verdict is that you are wrong 99% of the time
- Profit handling: move the stop to break-even first, then trail it in steps; never let a winning position turn into a loser
- Normalization caveat: 3 points is a 1920s price scale and will distort if copied into a modern market; it must be converted by volatility, and that conversion is the compiler's patch, not the book's content

**Example answer**

> Anchor the stop on structure, not on how much you can bear. The old bottom is 96, so the book's long-side rule puts the stop 3 points below it, around 93 — but that 3-point figure is a 1920s dollar scale, and carrying it onto today's price requires normalization. The sturdier approach is to express it as "about one ATR, or a fixed percentage, below the old bottom", so that the 93 area corresponds to a sensible modern width, and to write the convention down before you place the order. The order type matters just as much: place the G.T.C. stop at the same time as the entry, not as a manual sell "if it breaks", because failing to place a stop order is one of the three fatal errors in the book. Once you have a profit, follow rule four: move the stop to cost first (break-even), then trail it in steps as the trend continues. Two things are non-negotiable — do not cancel, do not widen; the moment you want to widen is usually the moment your read is already wrong. One more point: the stop only settles how much you lose if you are wrong. Whether 104 was the right place to buy is a location question — go back to the trend card and the seven action zones and confirm it once more.

## How these skills were generated

This skill pack was produced with the RIA-TV++ pipeline from **[cangjie-skill](https://github.com/kangarooking/cangjie-skill)**, in six stages:

1. **Whole-book understanding (Adler analysis)** — Mortimer Adler's analytical reading method, applied in four steps: structure, interpretation, criticism, application. Output: [`BOOK_OVERVIEW.md`](./BOOK_OVERVIEW.md)
2. **Parallel extraction** — several specialized extractors (frameworks, principles, cases, counter-examples, glossary) run at once to pull candidate methodology units out of the text; this book yielded 381 candidates
3. **Triple verification** — every candidate must pass three tests: at least two independent corroborations inside the book (cross-domain), the ability to answer a new question the book never states (predictive power), and not being common sense (distinctiveness). Of the 381 candidates, 333 passed, 40 were demoted to the reference domain, 9 were flagged for review and 1 was rejected — see [`verified.md`](./verified.md)
4. **RIA++ construction** — structure each unit along six dimensions: R (verbatim quotation), I (restatement in our own words), A1 (case from the book), A2 (future trigger scenario), E (executable steps), B (boundaries and blind spots). The 381 units were merged into 12 capabilities
5. **Zettelkasten linking** — identify dependencies, contrasts and combinations between cards, then generate the capability index and router table, which is the `also_read` field in [`bundle/verified.yaml`](./bundle/verified.yaml)
6. **Trigger and output testing** — design blind trigger tests for every entry (including decoy prompts: trigger when it should, stay silent when it should not) plus output-evaluation scenarios; failing cards go back for rework and are regression-tested afterwards

Two quirks of this book shaped the distillation. First, a version-date mismatch: the cover subtitle points at 1929–1935, while the body's data and cases stop in early 1923, so all quotations follow the body's own frame. Second, the fixed point-based parameters (3-point stops, 5–7 point reactions, 2–3 million share days) are tied to 1920s price levels and must be normalized by volatility before reuse in a modern market — a caveat written into every card's boundary section.

## Testing and verification

This repository ships the test material from the generation process: each skill directory publishes its own trigger cases as `test-prompts.json`, and [`test-results.md`](./test-results.md) records the item-by-item scoring for all 9 entries together with the failures and the fixes, not only the passes.

- **Blind trigger tests**: 65 cases across 9 entries, 64 passed (98.5%); 17 of them were decoys (should_not_trigger) with zero false triggers
- **Method**: 3 clean sub-agent blind tests plus scoring by the main process, with no expected answers supplied to the testers
- **The one failure**: `gann-trend-theory-skill::should_trigger-03` (a combined trend-plus-timing prompt) was routed to `trend-judgment-skill` by the blind test; the fix added that combined scenario to the single entry's description, without touching the expected answer
- **Output tests**: 7 of the 9 entries have a standalone representative-task output test; the entry and the router are covered through routing behaviour
- **Known gaps** (recorded as they are): the standalone output test for `strength-based-selection-skill` was done late (PASS-with-notes, 5 fixes); the train/validation split in `run_trigger_evals.py` was not executed; cross-model re-testing was not done

## Repository structure

```text
gann-trend-theory-skill/
├── README.md              ← Chinese version
├── README.en.md           ← you are reading this
├── LICENSE                ← MIT
├── BOOK_OVERVIEW.md       ← stage 0 output: Adler whole-book analysis
├── INDEX.md               ← stage 3 output: skill map + dependencies
├── verified.md            ← 333 units that passed triple verification
├── TEST_SUMMARY.md        ← stage 4 output: stress-test summary
├── CANGJIE_ADAPTATION.md  ← cangjie adaptation notes
├── GITHUB_REPO.md         ← repository metadata
├── test-results.md        ← test result records
├── candidates/            ← stage 1 output: raw candidate pool
│   ├── frameworks.md      ← framework and method candidates
│   ├── principles.md      ← principle / rule / calculation candidates
│   ├── cases.md           ← case candidates from the book
│   ├── counter-examples.md← counter-example and boundary candidates
│   └── glossary.md        ← terminology candidates
├── rejected/              ← stage 1.5 output: rejected units + reasons
├── bundle/                ← compilation source of truth
│   ├── verified.yaml      ← capability metadata, criteria and destinations
│   ├── cards/             ← capability card sources (six sections)
│   └── book/              ← overview.md + glossary.md
├── single/                ← single-mode build (one entry + all capability cards)
│   └── gann-trend-theory-skill/SKILL.md  ← entry: triggers + routing table + loading rules
└── pack/                  ← pack-mode build (one router + 7 promoted skills)
    └── */SKILL.md         ← 8 skills, each shipping a test-prompts.json
```

## Usage

Clone the repository first:

```bash
git clone https://github.com/raphael-y7/gann-trend-theory-skill.git
```

### Install single (recommended first try)

```bash
# macOS / Linux
cp -r gann-trend-theory-skill/single/gann-trend-theory-skill ~/.agents/skills/
```

```powershell
# Windows
Copy-Item -Recurse .\gann-trend-theory-skill\single\gann-trend-theory-skill "$env:USERPROFILE\.agents\skills\"
```

### Install pack

Copy only the directories that contain a `SKILL.md`; do not copy the two JSON files under `pack/` into your skills directory:

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

> `~/.agents/skills` is the DSH skills directory; with another agent, use its own skills directory (for example `~/.claude/skills` for Claude Code).

### How to verify the install

Ask: "I bought at 104 and the old low is 96 — where does the stop go?" If the agent enters the stop-anchoring and G.T.C. order flow instead of giving generic technical commentary, the install works. With the single build it reads the entry first and then routes to a card; with the pack build the matching capability is hit directly.

## Sources

- *New Stock Trend Detector* by William D. Gann

## Notice

This repository publishes distilled skills, indexes and rule quick references only. It contains no PDF, EPUB, OCR files, screenshots or full-book transcripts of the source book. Quotations that appear in the capability cards serve solely to attribute methodology and keep the material auditable.

All numeric criteria in the book (3-point stops, 5–7 point reactions, 10–20 round trips in a range, 2–3 million share days, etc.) are case- and experience-based rules from 1920s market conditions without statistical backtesting, and they cannot be applied to a modern market as they stand; normalize them by volatility and float, and state the convention you use. Nothing in this repository is investment advice.


## License

[MIT](./LICENSE)
