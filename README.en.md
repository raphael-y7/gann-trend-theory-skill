<h1 align="center">Gann Trend Theory Skill</h1>

<p align="center"><a href="README.md">中文</a> | English</p>

An AI skill pack for immediate use — it distills the trend-reading and trade-operating system of *Gann Trend Theory* into 12 capability cards that can be triggered individually or combined.

It is not a book summary, nor a reading response — it breaks the reusable methodology in the book into skill modules that can be triggered, executed and tested.

## What these skills solve

- Monthly says up, weekly says down, daily just jumped — you cannot tell which timeframe to trust, nor how to actually line up "higher tops and higher bottoms" on a chart
- A stock has been range-bound for months and you cannot tell accumulation from distribution; you look at absolute volume without dividing by shares outstanding and mistake a dead tape for abandonment
- Your stop is placed by feel, not anchored to a structural level; you do not know whether to trail it after a profit, or what condition allows re-entry after being stopped out
- A fresh new high: chase it or not, and is it a false breakout? A long narrow range suddenly breaks out on volume and you cannot judge whether a major move is starting
- Position size has no fixed risk budget, so you average down when wrong; when in profit you want to add but do not know how a pyramid should taper or when adding is forbidden
- Good news arrives and the stock falls, a dividend is raised, shares are issued — you cannot read any of it; after a loss you can only say "my mindset was bad" and never reach a named failure mode

## What was distilled

12 capability cards (each slug maps to `references/capabilities/<slug>-skill.md`), organized in the order "judge direction first, fix location second, manage money and discipline last":

- **Trend and range character**: `trend-judgment` (multi-timeframe charts, progressive highs/lows, breaking into a new range), `seven-action-zones` (locating price across the seven action zones), `accumulation-distribution` (accumulation vs distribution across volume × range × time)
- **Key levels and risk control**: `support-resistance-stops` (reviewing support/resistance and the stop system)
- **Selection**: `strength-based-selection` (relative strength and stock selection)
- **Position sizing and adding**: `twelve-trading-rules` (the twelve trading rules and capital management), `pyramid-scaling` (pyramid scaling)
- **Timing and news**: `entry-exit-timing` (entry/exit levels and timing), `news-discounting` (discounting news)
- **Review, triage and checkup**: `tape-review-workflow` (daily record and weekly review workflow), `failure-mode-triage` (failure-mode triage checklist), `portfolio-annual-checkup` (annual portfolio checkup)

Every card is structured in six sections — R / I / A1 / A2 / E / B: quotations, restatement, in-book cases, future trigger scenarios, executable steps, boundaries and blind spots.

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
- `support-resistance-stops-skill` — support/resistance review and the stop system
- `accumulation-distribution-skill` — accumulation vs distribution
- `strength-based-selection-skill` — relative strength and selection
- `twelve-trading-rules-skill` — the twelve rules and capital management
- `entry-exit-timing-skill` — entry/exit levels and timing
- `failure-mode-triage-skill` — failure-mode triage checklist

### Which one to install

Pick by the way you work, and **install only one**:

| How you work | Recommended | Why |
|---|---|---|
| You use DSH / Codex / Claude Code with a skills directory and want a clean list | single | Takes 1 slot, loses no capabilities |
| Your daily questions concentrate on "which way is the trend / where is my stop / accumulation or distribution / which stock is strongest / how much to buy / should I chase / where did I go wrong" | pack | Those are exactly the promoted standalone skills, matched directly |
| You distribute to several agents or teammates who pick what they need | pack | They can install only the standalone skills they want |
| You want to install once and maintain one directory | single | Upgrades replace a single directory |

> Both builds come from the same bundle and carry identical capabilities. **Installing both will double-trigger**, so pick one.

## Examples

### Example 1: four months sideways — accumulation or distribution?

**User question**

"This stock has been stuck between 18 and 21 for four months. Volume spikes sometimes, and they raised the dividend in the middle. Is smart money accumulating or dumping?"

**How the skill reasons**

- Enter `accumulation-distribution`: the first step is not absolute volume but the range's cumulative volume divided by shares outstanding, giving turnover counts — the book's own benchmark is that volume must be read against shares issued; U.S. Steel's 5 million shares "needed more than a million shares to change hands" before any major move
- Count round trips: the book counts swings of 5 points or more; 10–20 round trips inside one range, or 15–20 turnovers of the float in that range, is what makes the signal strong
- Check events: the book lists "heavy volume with rapid repeated rallies and breaks, plus higher dividends, extra dividends and extra rights" as the most reliable distribution signals — the dividend raise here is **bait evidence**, not a bullish reason
- Fix location: leaders distribute within 5–10 points below the top, laggards 20–30 points below the high; the same dead quiet means buying power exhausted near a top, and accumulation only near a bottom
- Stop rule: when top deadness and bottom deadness cannot be told apart, output "location undetermined" and never default to safe

**Sample answer**

> Do not call it accumulation yet. Three dimensions each need a number: turnover — cumulative range volume divided by shares outstanding, so you know how many times the float changed hands; round trips — how many 5-point-equivalent swings you counted; and time — whether four months is long or short relative to this stock's own history. The book's strong-signal thresholds are 15–20 turnovers of the float or 10–20 swings of 5 points or more inside the range. If you are far below both, this is "no signal" — neither accumulation nor distribution.
>
> Record the dividend raise separately: the book puts "higher dividends, extra dividends, extra rights" directly on its list of the most reliable distribution signals. It is bait, not a reason to be bullish.
>
> One conversion is mandatory: the "5 points" and "15–20 times" are 1920s fixed-point parameters. Applying them directly to an 18–21 range produces nonsense. Rebuild the swing threshold from this stock's ATR or percentage range, and state the conversion basis in your conclusion — that conversion is the compiler's patch, not the book's content.
>
> Finally, even if all three dimensions qualify, the conclusion can only be written as an "evidence-strength assessment", never as "smart money is dumping". The book's premise that volume and price cannot be faked does not strictly hold under today's algorithmic slicing and high-frequency market making. If location cannot be determined, stop there and wait for the breakout to define the range's character.

### Example 2: a fresh new high — should I chase, and where does the stop go?

**User question**

"The stock broke out of a two-year box and made a new high. I chased it. Where should my stop be — and was chasing a new high too risky?"

**How the skill reasons**

- `trend-judgment`: first ask which new high this is — the book states that buying "when a stock makes a new high a second time is always safer than buying at its first new high"; then check whether the range before the breakout was accumulation or distribution (an upside break from an accumulation range is more credible), and note that the longer the gap between two entries into a new range, the greater the force
- The false-breakout branch of `trend-judgment`: if price falls back below the old high within a few days, mark it "suspected false breakout / distribution unfinished" — this step is never skipped
- `support-resistance-stops`: anchor the stop to structure — for longs, 3 points below the old bottom/support; for shorts, 1–3 points above the old top. The stop order is G.T.C. and goes in together with the entry
- The normalization band in `support-resistance-stops`: the book's cases land between 2.6% and 10% in percentage terms; the compiler's default band is 3%–6% calibrated to ATR, and the conversion basis must be stated
- Time confirmation: a key level must hold "for several weeks" to count as valid; before that, direction is only "preliminary" and confidence caps at "medium"

**Sample answer**

> On "was chasing a new high too risky": the book takes the opposite view — a second new high is safer than the first, because the first tends to meet heavy selling while by the second the supply has been absorbed. So the question is not whether to chase a new high, but which new high this is.
>
> Stop placement: anchor it to structure, not to a round percentage. For a long, it sits below the support or old bottom; the book's raw parameter is 3 points. Converted to your stock, the book's cases land between 2.6% and 10%, and the compiler's suggested default band is 3%–6% calibrated to ATR. Neither number is a modern parameter from the book — write down which one you use.
>
> Two iron rules carry over verbatim: the stop order goes in at the same time as the entry (G.T.C., good till cancelled), and once filled it is never cancelled or widened — the book says that when you want to risk more than planned, "99% of the time you are wrong".
>
> Keep one branch open: if price falls back below the old high within a few days, that is not a pullback but a "suspected false breakout / distribution unfinished" signal, and the correct action is to check the distribution evidence, not to average down. Also, a breakout only counts once it has held for several weeks; the day of the break is preliminary confirmation at best.
>
> One boundary to close with: every case in the book is a retrospective reading of a completed move, with no failure-rate statistics and no out-of-sample test. This workflow gives you a checkable evidence chain and explicit stop rules — not a win-rate promise.

## How these skills were generated

These skills were produced with the **[cangjie-skill](https://github.com/kangarooking/cangjie-skill)** RIA-TV++ pipeline, in six stages:

1. **Whole-book comprehension (Adler analysis)** — apply Mortimer Adler's analytical reading method to the book: structure, interpretation, criticism, application
2. **Parallel extraction** — several specialized extractors (frameworks, principles, cases, counter-examples, terminology) mine candidate methodology units from the source text
3. **Triple verification** — every candidate must pass three checks: at least two independent in-book supports (cross-domain), the ability to answer questions the book never explicitly addresses (predictive power), and not being common sense (distinctiveness)
4. **RIA++ construction** — structure each unit along R (quotation) / I (restatement in own words) / A1 (in-book case) / A2 (future trigger scenario) / E (executable steps) / B (boundaries and blind spots)
5. **Zettelkasten linking** — map dependencies, contrasts and combinations between cards, producing the capability index and routing table
6. **Trigger and output testing** — write trigger blind tests (including decoy questions: fire when they should, stay silent when they should not) and output evaluation scenarios for every card; failing cards go back for rework and are re-verified afterwards

## Repository layout

```text
gann-trend-theory-skill/
├── README.md                      ← Chinese version
├── README.en.md                   ← you are reading this
├── LICENSE                        ← MIT
├── BOOK_OVERVIEW.md               ← whole-book comprehension (Adler four-step, stage 0 output)
├── verified.md                    ← triple-verification conclusions for the 12 capability units
├── single/                        ← single-entry build
│   └── gann-trend-theory-skill/
│       ├── SKILL.md               ← entry: triggers + routing table + loading rules
│       ├── BUILD_MANIFEST.json    ← build manifest and file hashes
│       └── references/
│           ├── overview.md        ← whole-book overview
│           ├── capability-index.md  ← full intent and keyword index
│           ├── cheatsheet.md      ← decision-rule quick reference
│           ├── glossary.md        ← glossary
│           └── capabilities/      ← 12 capability cards
├── pack/                          ← multi-entry build (compact pack)
│   ├── BUILD_MANIFEST.json
│   ├── capability-destinations.json
│   ├── gann-trend-theory-skill-router/
│   │   ├── SKILL.md               ← source router entry
│   │   └── references/            ← 12 cards + indexes, called by the router
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

Ask: "This stock has been sideways for four months — is it accumulation or distribution?" If the agent asks for shares outstanding and starts computing turnover counts and range round trips instead of jumping to a verdict, the install works. With the single build it reads the entry first and then routes to a card; with the pack build the matching capability is hit directly.

## Sources

- *Gann Trend Theory* by William D. Gann
- Distilled from the whole book, producing 12 capability cards

## Notice

This repository publishes distilled skills, indexes and rule quick references only. It contains no PDF, EPUB, OCR files, screenshots or full-book transcripts of the source book. Quotations that appear in the capability cards serve solely to attribute methodology and keep the material auditable.

All numeric criteria in the book (3-point stops, 5-point swings, 15–20 turnovers, 2–3 million share climax days, the 100→50→30→20→10 scaling sequence, etc.) are bound to 1920s price levels and share counts, without statistical backtesting. They must be normalized by volatility and float before use in modern markets, and the conversion basis must be stated in the output; the conversion itself is the compiler's patch, not the book's content. The book's time-cycle algorithm was explicitly left unpublished by the author, and this repository invents no cycle numbers. Nothing in this repository is investment advice.

## License

[MIT](./LICENSE)

