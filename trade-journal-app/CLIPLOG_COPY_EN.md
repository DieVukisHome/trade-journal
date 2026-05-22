# ClipLog — Copy Package (English, primary language)

> Stand: 2026-05-22 · Primärsprache **Englisch** (Deutsch = spätere Lokalisierung, Punkt E).
> Diese Datei liefert paste-fertige Copy für **Codex-Liste Punkt B (Onboarding-Funnel)** und **Punkt D (Hero/Positionierung)**.
> `{{ ... }}` = dynamischer Platzhalter, von Codex zu befüllen.

## Voice & rules (verbindlich)
- **Pain first, solution second.** Never promise profit or returns.
- Say **"understand why you lose"**, not "become profitable". Say **"see your pattern"**, not "learn from your trades".
- **"OCR suggests — you decide."** Never imply OCR is infallible.
- No "best / #1 / top" claims (App Store flags unverifiable claims).
- Tone: direct, second person, honest, trader-native (perps, setup, R, PnL, liquidation). No hype, no emojis.
- Recurring sharpest line (use sparingly, high impact): **"You know what you should do. How often have you done it anyway?"**

---

## 1. Hero (in-app landing / website)
- **H1:** ClipLog
- **Subline:** The futures journal you'll actually keep. Screenshot in, trade logged — no API key, no cloud.
- **Secondary line:** For day-traders on Binance, OKX, Bitget & BingX.
- **Primary CTA:** Start free trial
- **Trust line (small):** 100% on-device · Your screenshots never leave your phone.

---

## 2. Onboarding funnel — 14 screens (Hard Paywall, 7-day trial)

> Goal: 10–15 min, every screen is a sales argument. Ends **inside** the paywall (S13), not in an empty journal.

### Pillar 1 — Introduction

**S1 · Problem frame**
- Headline: You trade almost every day. Are you actually getting better?
- Body: Most traders can't answer that — because they never write it down. Two minutes here changes that.
- CTA: Show me

**S2 · Aha calculation** *(personalized)*
- Step A (input): What does one bad trade usually cost you? `{{avg_loss}}` USDT
- Step B (result): Headline: One revenge trade can erase a good week.
- Body: Avoid just 2 a month and you keep about **{{avg_loss × 24}} USDT a year**. ClipLog helps you see them coming.
- Fallback (no input): A single revenge trade can cost more than a month of disciplined gains.
- CTA: Makes sense

**S3 · Choose your exchange**
- Headline: Where do you trade?
- Body: We'll tune ClipLog to read your screenshots.
- Options (multi-select, "pick all that apply"): Binance · OKX · Bitget · BingX
- CTA: Continue
- Note: persist this — personalizes the app and pre-selects the right OCR parser.

**S4 · Your biggest leak**
- Headline: What costs you the most?
- Options (single-select): FOMO — entering too early · Revenge trading after a loss · Not sticking to my plan · No clear overview of my trades
- CTA: Continue

**S5 · Reflect** *(dynamic — mirrors S4)*
- Headline: `{{problem}}`. That's exactly what ClipLog is built to surface.
- Body: You don't need another strategy. You need to see the pattern — so you can finally break it.
- CTA: Continue
- Example (problem = Revenge trading): "Revenge trading. That's exactly what ClipLog is built to surface."

**S6 · Commitment**
- Headline: How serious are you about getting better?
- Body: Honest answer — it shapes the plan we build for you.
- Options: Extremely · Very · Somewhat
- CTA: (auto-advances on tap)

### Pillar 2 — Climax

**S7 · Live OCR demo**
- Headline: Watch. Drop in a trade screenshot.
- Body: ClipLog reads the coin, direction, entry, exit and PnL — right here, on your device. No typing.
- CTA: Try it
- Note: live demo with a sample screenshot; fields visibly fill in.

**S8 · The time advantage**
- Headline: That took 15 seconds. By hand it's 3 minutes.
- Body: Fast enough that you'll actually do it after every trade — which is the entire point.
- CTA: Continue

**S9 · Day-1 streak + review request**
- Headline: Day 1. Your first logged trade.
- Body: Most traders quit journaling by day 3. You won't — because this is fast.
- Action: trigger the native review request here (emotional high).
- CTA: Continue

### Pillar 3 — Conclusion

**S10 · Your personal plan**
- Headline: Your 30-day plan is ready.
- Body: Log every trade for 30 days. By the end you'll see your pattern — when you lose, and why.
- CTA: Continue

**S11 · Price vs. a bad trade**
- Headline: ClipLog Pro costs less than one bad trade.
- Body: One revenge trade can cost you {{avg_loss}} USDT. ClipLog Pro is $39.99 a year. The math isn't close.
- CTA: Continue

**S12 · Plan loader + social proof**
- Loader headline: Building your trading plan…
- Sequential lines: Setting your 30-day goal… · Tuning OCR for {{exchange}}… · Preparing your review dashboard…
- Social proof (honest, no invented numbers): Join the traders who finally kept the habit.
- Note to Codex: do NOT fabricate user counts/ratings. Replace with real figures only once verifiable.

**S13 · Paywall** *(the hard paywall — onboarding ends here)*
- Headline: Start your 7-day free trial.
- Subhead: Then keep the habit that actually makes you better.
- Plans:
  - Yearly — **$39.99/year** · Save 67% — *(BEST VALUE, preselected)*
  - Monthly — **$9.99/month** · Most flexible
  - Weekly — **$2.99/week**
  - Lifetime — **$79 one-time** · Founding Member *(launch only, limited)*
- Trial line: 7 days free, then {{selected_plan_price}}. Cancel anytime.
- Primary CTA: Start free trial
- Comparison table — **"By hand vs. ClipLog Pro"** (NOT a free-tier table — there is no free tier):

  | By hand / spreadsheet | ClipLog Pro |
  |---|---|
  | Type every field manually | Screenshot → trade in 15 seconds |
  | Scattered, rarely updated | Every trade, logged automatically |
  | No pattern visible | See your FOMO, revenge trades & plan breaks |
  | Your keys on a server (other apps) | 100% on-device · no API key |

- Sub-CTA line: Cancel anytime · No API key · Nothing leaves your device.

**S14 · Post-paywall welcome offer** *(only for users who declined S13)*
- Headline: Wait — here's 40% off your first year.
- Body: The first 30 days are when journaling actually sticks. This offer expires in 24 hours.
- CTA: Claim 40% off
- Secondary: No thanks
- Note: 24h countdown, 40% off the yearly plan, non-converters only.

---

## 3. Persistent paywall (Settings / when tapping a Pro feature)
- Headline: Become the trader you could be.
- Body: You've got the setups. You know the technical analysis. What's missing is the mirror — an honest look at your own behavior. ClipLog Pro gives you unlimited trades, full OCR, all exchanges, and the insights that make your pattern visible.
- Plans + trial + CTA: same as S13.
- Sub-CTA: Cancel anytime · No API key · Nothing leaves your device.

---

## 4. App Store listing (English)
- **App name (≤30):** ClipLog: Futures Journal
- **Subtitle (≤30):** Screenshot in. Trade logged.
- **First 3 lines (no "more" tap needed):**
  1. You know the mistakes you make. You just don't write them down.
  2. ClipLog is the futures journal traders actually use — a screenshot becomes a logged trade in 15 seconds.
  3. Binance, OKX, Bitget, BingX. No API key. No cloud. Everything on your device.
- **Promotional text (≤170):** Screenshot in, trade logged — 100% on-device, no API key, no cloud. For futures day-traders on Binance, OKX, Bitget & BingX.
- **Keywords (≤100, comma-sep):** trading journal,futures,crypto,binance,okx,bitget,bingx,perpetual,day trading,screenshot,trade tracker
- **Description — features (after the opener):**
  - Screenshot OCR — open & closed trade screenshots read automatically, on your device. Binance, OKX, Bitget, BingX.
  - The fields that matter — emotions, notes, "did you follow your rules?" This is where the pattern shows up.
  - See your pattern — when do you lose? Which session? After which event?
  - 100% local — no account, no cloud, no API key. Your data stays on your device.
  - Close: A journal can't make you a better trader. But it can show you what's holding you back. The rest is on you.

---

## 5. Key microcopy fixes (current code → new)
- `index.html` Paywall button "Continue with trial" → **"Start 7-day free trial"**
- Subscription badge "Demo membership" → remove for store build; show real trial/subscription state.
- Hero `<p>` (line ~838) → use the Hero subline above.
- Onboarding modal heading "Welcome to Trade Journal" → replaced by S1 of the funnel.
- Manifest `description` → "Screenshot in, trade logged. On-device futures journal for Binance, OKX, Bitget & BingX — no API key, no cloud."

---

## 6. German localization (later — Punkt E)
Do NOT translate yet. The German finished copy already exists in `ClipLog_Kommunikation.docx` (App Store text, onboarding slides, paywall) and serves as the starting point for the DE localization after the English launch.
