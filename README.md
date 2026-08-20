# Investor Type Quiz

A single-file, no-backend HTML quiz that sorts respondents into one of 8 investing archetypes based on their investment philosophy and their actual risk tolerance, time horizon, and involvement level.

**[Live demo](index.html)** — open `index.html` directly in any browser, no build step or server required.

## How it works

**Stage 1 — Investing philosophy (8 questions)**
Multiple-choice questions score the respondent across 8 archetypes:

- Buffett Compounder
- Growth Chaser
- Income Builder
- Passive Optimizer
- GARP Hybrid
- Contrarian/Deep Value
- Momentum Trader
- Barbell Allocator

If the top two scores land within 1 point of each other, the quiz flags a tie and holds off declaring a winner until Stage 2 resolves it.

**Stage 2 — Behavioral profile (12 questions)**
Twelve more questions measure three dimensions — Risk Tolerance, Time Horizon, and Involvement Level — each scored 1–5.

**Scoring & overrides**
A weighted mismatch score compares the respondent's Stage 2 profile against their Stage 1 archetype's "ideal" profile:

```
mismatch = 2×|Risk − ideal Risk| + 1×|Horizon − ideal Horizon| + 2×|Involvement − ideal Involvement|
```

- **0–4 (confirmed):** the archetype stands as-is.
- **5–9 (caveat):** the archetype stands, with a plain-language note on where behavior diverges from the label.
- **10+ (rerouted):** the quiz recalculates mismatch against all 8 archetypes and reassigns the respondent to whichever fits best.

**Results screen**
- Archetype name, tier badge, and description
- "Why You Landed Here" — plain-language reasoning from the respondent's top Stage 1 answers
- A dimension comparison table (respondent vs. archetype ideal)
- A collapsible full scoring breakdown (mismatch score for all 8 archetypes, for QA/verification)
- An email-gated preview (blurred teaser until an email is submitted) with a "Retake Quiz" option that's never gated

## Tech

Vanilla HTML/CSS/JS. No frameworks, no build tools, no dependencies beyond Google Fonts (Space Grotesk + Inter). Fully responsive/mobile-friendly. No data is persisted anywhere except an optional webhook POST (email + resulting archetype) fired on unlock.

## Disclaimer

This quiz is for entertainment and self-reflection purposes only. It is not investment, financial, tax, or legal advice.
