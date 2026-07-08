# is-this-a-good-idea

A domain-routed idea evaluation skill. It runs your idea through hard gates, a weighted scorecard, and a cross-domain decision layer, then issues one of four verdicts: **GO**, **TEST FIRST**, **NO-GO**, or **PIVOT**.

It covers three domains with separate gates and scoring weights:

- **Entrepreneurship / business ideas**
- **Real estate investment deals**
- **App and product builds** (market-facing products and internal workflow tools are scored differently)

Every verdict comes with evidence tags on every claim, counterarguments for every weakness, the falsifiable conditions that would change the verdict, and next actions where the first one is doable today.

## What Makes It Different

- **Gates before scores.** A fatally flawed idea fails a hard gate and never reaches the scorecard, so a polished-looking score can't launder a broken idea.
- **No flattery.** The skill is instructed to assess, never compliment. Strengths are findings with evidence.
- **Evidence protocol.** When a claim is load-bearing (the verdict flips if it's wrong) and unverified, the skill stops and asks whether to search for evidence or proceed from reasoning. Nothing load-bearing gets silently assumed.
- **Built on established frameworks only.** Kagan (Velocity to $1), Fitzpatrick (The Mom Test), Blank-era validation discipline replaced by Amazon's Working Backwards press-release test, RICE (Intercom), standard real estate underwriting screens (cap rate, cash-on-cash, DSCR), Munger's inversion, Klein's pre-mortem, and expected-value tie-breaking. Nothing invented.

## Install

### Claude.ai (Chat)

Upload `SKILL.md` to a conversation or attach it to a Project. Invoke with:

```
Use the is-this-a-good-idea skill: [your idea]
```

### Claude Code

```bash
mkdir -p ~/.claude/skills/is-this-a-good-idea
cp SKILL.md ~/.claude/skills/is-this-a-good-idea/
mkdir -p ~/.claude/commands
cp claude-code/is-this-a-good-idea.md ~/.claude/commands/
```

Invoke with:

```
/is-this-a-good-idea a SaaS that auto-generates lease abstracts for landlords
```

### Codex CLI

```bash
mkdir -p ~/.codex/skills/is-this-a-good-idea
cp SKILL.md ~/.codex/skills/is-this-a-good-idea/
```

Then reference the skill by name in your session.

### ChatGPT

Open `chatgpt/instructions.md`, copy everything below the divider line, and paste it into the Instructions field of a Custom GPT (or a project's custom instructions). This is a flattened single-document version of the same logic, compressed to fit ChatGPT's instruction character limit.

## Usage Examples

```
/is-this-a-good-idea duplex in a B-class neighborhood, $310k, rents $2,600 combined, 25% down at current rates

Use the is-this-a-good-idea skill: an AI tool that drafts contractor scope-of-work docs from voice notes

/is-this-a-good-idea internal automation that pulls rent rolls from email attachments into a spreadsheet every Monday
```

## The Verdict Tiers

| Verdict | Meaning |
|---|---|
| **GO** | Gates passed, weighted score 4.0 or higher, no caps triggered. Proceed. |
| **TEST FIRST** | Viable but carries an untested fatal assumption. The report names the assumption and the cheapest test that could falsify it. |
| **PIVOT** | The idea as framed fails, but a salvageable core exists. The report names the core and the new angle. |
| **NO-GO** | Weak across the board with nothing worth saving. The report states the kill reason in one line. |

## File Structure

```
is-this-a-good-idea/
├── SKILL.md                          # Main skill (Claude.ai, Claude Code, Codex)
├── claude-code/
│   └── is-this-a-good-idea.md        # Claude Code slash command
├── chatgpt/
│   └── instructions.md               # Flattened Custom GPT version
├── README.md
├── CHANGELOG.md
└── LICENSE
```

## Design Notes

- The skill is fully standalone. No cross-references to other skills, no external files, no persistent state. Same idea in, same rigor out, on any platform.
- Scoring uses 1 to 5 with plain-language anchors instead of 1 to 10, because nobody can defend why something is a 7 and not a 6.
- The 1% rule appears in the real estate dimension as a fast screen only, never a verdict input. It was built for a different rate and price environment.
- The Cheapest-Test Gate for apps explicitly allows building as validation when a build is genuinely the cheapest learning path (a weekend build passes). It fails only long builds with no learning checkpoint, which is the actual Engineering Disease.

## License

MIT. Copyright (c) 2026 Almora Technology / Bhaskar Pandey.
