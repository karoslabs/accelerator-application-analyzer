---
name: accelerator-application-analyzer
description: Analyze a founder's readiness for top accelerators and startup competitions (Y Combinator, Techstars, a16z Speedrun, 500 Global, The Pitch by Deel). Use whenever someone asks for feedback on their YC application, wants to know their odds at Techstars, is preparing a Speedrun deck, is unsure whether to apply to a specific accelerator, asks "do I stand a chance at X", wants a realistic acceptance probability, or asks how to improve an application. Also trigger when the user mentions applying to any of these programs and wants tactical advice tailored to their specific profile. Do not rely on generic startup advice — this skill runs a structured intake on the founder and their company, compares the profile against the specific criteria of the target program, and returns a probability estimate plus concrete improvements.
---

# Accelerator Application Analyzer

Turn a founder's raw profile (CV, co-founder CV, deck or blurb) into a tailored verdict on a specific accelerator or competition: what they'd improve, what the program actually wants, and an estimated acceptance probability.

## When to use

Trigger this skill whenever a founder wants tailored feedback on applying to a top accelerator or pitch competition. Covered programs:

1. Y Combinator
2. Techstars
3. a16z Speedrun
4. 500 Global (Flagship)
5. The Pitch by Deel

Not a legal or investment opinion. The probability estimate is a directional signal, not a prediction.

## Workflow

Run these steps in order. Do not skip intake.

### Step 1 — Intake

Ask the founder for whatever is missing from the conversation. Be concise — group requests into one message, not a drip of questions.

Minimum inputs:
- **Founder CV / LinkedIn** (text paste or file)
- **Co-founder CV / LinkedIn** if any, plus equity split
- **Deck** (PDF or link) OR a 5-sentence blurb describing: problem, solution, who it's for, traction so far, why this team
- **Target program** (pick from the 6 above)
- **Stage + traction numbers** (MRR / users / pilots / LOIs / funding raised to date)
- **Geography** and whether they can relocate

If the deck is a file, read it. If the founder only has a blurb, that is fine — note the reduced confidence in the final verdict.

### Step 2 — Load the program profile

Read the matching reference file in `references/`:

- `references/yc.md`
- `references/techstars.md`
- `references/speedrun.md`
- `references/500global.md`
- `references/pitch-by-deel.md`

Each file contains the program's base rate, stage fit, what partners actually look for, common reasons to get rejected, and the founder archetype that wins. Use it as the rubric for the analysis.

### Step 3 — Score the founder across the program's rubric

For the target program, score the founder 1-10 on each of these dimensions (adapt to what the program weights most — this is specified in each reference file):

- **Team strength** (track record, domain fit, co-founder balance, technical depth)
- **Product / insight** (clarity of what's being built, non-obvious insight, differentiation)
- **Traction** (evidence of pull — users, revenue, retention, LOIs)
- **Market** (size and why now)
- **Founder-program fit** (do they match what this specific program backs)
- **Application craft** (clarity, specificity, candor — how well the story comes across)

Cite the specific evidence from the founder's inputs for each score. No hand-waving.

### Step 4 — Estimate acceptance probability

Use this formula:

```
estimated_probability = base_rate x founder_multiplier
```

- **base_rate**: from the reference file (e.g. YC ~ 1%, Speedrun ~ 0.4%, Techstars ~ 1%, 500 ~ 1.5%, Pitch by Deel ~ 0.5%)
- **founder_multiplier**: a judgment call based on the scoring above.

Multiplier bands:

| Profile | Multiplier | What it looks like |
|---|---|---|
| Below bar | 0.1-0.3x | Solo non-technical, no MVP, no insight, no traction |
| Average applicant | 0.5-1x | Real product, some progress, but nothing that pops |
| Strong applicant | 2-5x | Clear insight, meaningful traction, balanced team, sharp story |
| Exceptional | 10-25x | Repeat founder / prior exit, rare insight, hard traction, obvious founder-market fit |
| Clear-in | 30-50x | Would be a shock if they got rejected. Name-recognition founders, 6-7 figure ARR at pre-seed, etc. |

Report the probability as a range (e.g. "roughly 4-8%"), never a single false-precision number. Always state the base rate and multiplier separately so the founder can see the math.

### Step 5 — Deliver the verdict

Structure the output exactly like this:

```
## Verdict: [Program name]

**Estimated probability:** ~X-Y%
(Base rate: Z% / Founder multiplier: Nx)

### The case for you
3 bullets. What's actually strong.

### The case against you
3 bullets. Honest. No softening.

### What [Program] specifically wants that you're missing
Pull from the reference file. Be specific to the program, not generic.

### Top 5 concrete improvements before you apply
Ranked by impact. Each one should be doable in under 2 weeks where possible.

### Application craft notes
If there's a deck or written blurb, call out specific lines that are hurting the application and how to rewrite them.

### Bottom line
One paragraph. Would you apply in the current cycle or wait one cycle and strengthen?
```

## Source disclaimer

**All program information in this skill's reference files is compiled from public sources**: official accelerator websites, published partner interviews, TechCrunch / Fortune / founder blog posts, and Deel's own public announcements. No confidential data, no insider info, no leaked rubrics. The acceptance rates, scoring weights, and red flag / green flag multipliers are directional heuristics built from what programs publicly say they look for. Treat them as a well-researched framework, not insider access.

When delivering the verdict to a founder, include a one-line version of this disclaimer at the end of the output, phrased as: *"Program data is based on public sources. Probability is a directional signal, not a forecast."*

## Critical rules

- **Be honest, not nice.** A founder asking for this analysis wants real feedback. Soft-pedaling wastes their time.
- **Tailor to the program, never generic.** YC advice does not apply to Speedrun. 500 Global is not Techstars. Use the reference files.
- **Cite the founder's own inputs.** Every score must point to something they actually said or submitted.
- **Never invent traction.** If the founder didn't share numbers, say so and score the traction dimension as "unknown, likely weak."
- **Never promise acceptance.** The probability is a signal, not a forecast.
- **Reapplication is normal.** If the verdict is "not yet," frame it as "apply next cycle with these changes" rather than "don't apply."
- **No em dashes in any output.** Use commas, periods, or " / " instead.
- **If the founder wants to compare multiple programs**, run Step 2 through Step 5 for each, then add a final "best fit" summary ranking the programs by probability x strategic fit.
