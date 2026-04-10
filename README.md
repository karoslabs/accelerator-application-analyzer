# Accelerator Application Analyzer

**A Claude skill that scores your accelerator application against what each program actually wants.**

Built for founders applying to Y Combinator, Techstars, a16z Speedrun, 500 Global, and The Pitch by Deel.

---

## What it does

You give it your profile (CV, deck or blurb, traction numbers, target program). It gives you back:

- A **1-10 score** across 6 dimensions tailored to your target program's actual rubric
- An **estimated acceptance probability** (base rate x founder multiplier, math shown)
- **The case for you** and **the case against you**, with zero softening
- **What the program specifically wants that you're missing**
- **Top 5 concrete improvements** ranked by impact, most doable in under 2 weeks
- **Line-by-line application craft notes** on your deck or written blurb

Every score cites your own inputs. No generic startup advice. No hand-waving.

## Why this exists

Most founders apply to accelerators blind. They don't know what YC actually weighs (team is 35%, not traction). They don't know Techstars will reject you for seeming uncoachable. They don't know Speedrun wants a strategy memo, not a pitch.

This skill has the rubric for each program, compiled from public sources: official websites, published partner interviews, founder post-mortems, and program announcements. It scores you against what each program has publicly said they look for.

## Covered programs

| Program | Base rate | What they weight most |
|---|---|---|
| Y Combinator | ~1% | Team (35%), product/insight (25%) |
| Techstars | ~1% | Team + coachability (45%), program fit (15%) |
| a16z Speedrun | ~0.4% | Team + founder-market fit (30%), velocity (25%) |
| 500 Global | ~1-1.5% | Team + co-founder dynamics (25%), traction (25%) |
| The Pitch by Deel | ~0.5% regional | Product + clarity (25%), traction (20%) |

## How to install

### Option 1: Drop the .skill file into Claude
1. Download \`accelerator-application-analyzer.skill\` from [Releases](../../releases)
2. Drop it into Claude Desktop or Claude Code
3. Done. Say "analyze my YC application" to trigger it.

### Option 2: Manual install
1. Clone this repo
2. Copy the \`SKILL.md\` and \`references/\` folder into your Claude skills directory
3. The skill auto-triggers when you mention applying to any of the 5 programs

## How to use it

Just tell Claude which program you're targeting and share your profile:

> "I'm applying to YC next batch. Here's my LinkedIn, my co-founder's LinkedIn, and our deck. What are our odds?"

The skill runs a structured intake, loads the program-specific rubric, scores you, estimates your probability, and delivers a verdict with specific improvements.

## What's inside

\`\`\`
SKILL.md                          <- the skill itself
references/
  yc.md                           <- Y Combinator rubric + scoring weights
  techstars.md                    <- Techstars rubric + scoring weights
  speedrun.md                     <- a16z Speedrun rubric + scoring weights
  500global.md                    <- 500 Global rubric + scoring weights
  pitch-by-deel.md                <- The Pitch by Deel rubric + scoring weights
accelerator-application-analyzer.skill  <- one-click installable
\`\`\`

## Source disclaimer

All program information is compiled from **public sources**: official accelerator websites, published partner interviews, TechCrunch / Fortune / founder blog posts, and Deel's own public announcements. No confidential data, no insider info, no leaked rubrics. The acceptance rates, scoring weights, and multipliers are directional heuristics, not insider access.

## License

MIT. Use it, fork it, improve it.

---

*Built by Albert Kattan. If this helped you, drop a star and share it with a founder who's applying.*
