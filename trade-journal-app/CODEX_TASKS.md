# PerpLog — Codex Aufgabenliste (Marketing-/Strategie-Konformität)

> Stand-Review: 2026-05-22 · Datei: `index.html` (2910 Zeilen, Single-File-PWA) + `manifest.webmanifest`
> Grundlage: PerpLog Positionierung, Onboarding/Growth- und Pricing-Strategie.
> Reihenfolge ist Priorität. **P0 zuerst** — der Funnel ist die Monetarisierung, nicht das Feature.
> Zeilennummern beziehen sich auf den Stand vom 2026-05-22 und können nach Edits verrutschen — bei Bedarf per Label/Text suchen.

---

## P0 — Identität & Monetarisierung (Blocker für Launch)

### A) Rebranding „Trade Journal" → „ClipLog" (Name FINAL, 2026-05-22)
**Der Name steht fest: ClipLog.** Aktuell liegt „Trade Journal" verstreut an 8 Stellen → konsistent durch „ClipLog" ersetzen (Name = Wiedererkennung + ASO-Keyword). Den Namen einmalig als Konstante/Variable zentralisieren, damit künftige Änderungen ein One-Liner sind.
> Vor Hard-Launch von Wookie zu bestätigen: cliplog.com/.app + Marke + Handles.

- [ ] Namen an **einer** Stelle zentralisieren (z. B. JS-Konstante + per Script ins Markup), statt 8× hartkodiert.
- [ ] `index.html:6` — `<title>Trade Journal</title>` → `ClipLog — Screenshot Trade Journal`
- [ ] `index.html:9` — `<meta name="apple-mobile-web-app-title" content="Trade Journal">` → `ClipLog`
- [ ] `index.html:837` — Hero `<h1>Trade Journal</h1>` → `ClipLog` (Copy siehe Punkt D)
- [ ] `index.html:1288` — Onboarding `<h2>Welcome to Trade Journal</h2>` → `ClipLog` (wird ohnehin durch Funnel ersetzt, Punkt B)
- [ ] `index.html:1322` — Paywall `<h2>Trade Journal Pro</h2>` → `ClipLog Pro`
- [ ] `index.html:2304` — Statusmeldung „valid Trade Journal backup" → „valid ClipLog backup"
- [ ] `manifest.webmanifest:2-3` — `name` und `short_name` → `ClipLog`
- [ ] `manifest.webmanifest` `description` → USP-Satz statt „Trade journal PWA for BingX screenshot OCR…" (siehe Punkt D)

### B) Onboarding zum Sales-Funnel umbauen (größter Hebel)
**Ist:** `index.html:1283–1315` — statisches 4-Schritt-Info-Modal, einmalig (`ONBOARDING_KEY`, `index.html:1357 / 1554`). Reine Feature-Erklärung.
**Soll:** 3-Säulen-Sales-Funnel (10–15 Min), jeder Screen ein Verkaufsargument. Tag 0 entscheidet — ~89 % der Trial-Starts und ~50 % der Paid-Conversions passieren am Download-Tag.
> 📋 **Fertige englische Screen-Copy S1–S14: `CLIPLOG_COPY_EN.md` → Abschnitt 2.** Nur einbauen, nicht neu texten.

- [ ] Statisches Modal durch mehrstufigen Screen-Flow ersetzen (Fortschrittsanzeige, Weiter-Button pro Screen).
- [ ] **Säule 1 – Introduction:** (1) Problem rahmen „Du tradest täglich — merkst du Fortschritt?", (2) Aha-Rechnung „Wenn du 2 Revenge Trades/Monat vermeidest, sparst du X USDT/Jahr", (3) **Exchange wählen** (Binance / OKX / Bitget / BingX), (4) größtes Problem wählen (FOMO / Revenge Trading / Plan nicht eingehalten / keine Übersicht), (5) Antworten spiegeln, (6) Commitment-Frage „Wie ernst ist dir deine Verbesserung?".
- [ ] **Säule 2 – Climax:** (7) Live-OCR-Demo „Screenshot rein → Trade erkannt", (8) ausgefüllten Trade + Zeitvorteil „15 Sekunden statt 3 Minuten", (9) Tag-1-Streak-Animation + Review-Request auf emotionalem Hoch.
- [ ] **Säule 3 – Conclusion:** (10) persönlicher Plan mit 30-Tage-Ziel, (11) Preisvergleich **gegen einen schlechten Trade** (nicht gegen Kaffee), (12) Plan-Loader + Social Proof, (13) **Paywall** (Punkt C), (14) Post-Paywall-Welcome-Offer nur für Non-Converter (24 h, 40 % auf Jahresplan).
- [ ] Exchange-Auswahl aus Screen 3 persistent speichern (personalisiert App + bereitet die exchange-spezifischen Parser vor).
- [ ] Onboarding endet **in** der Paywall (Hard Paywall), nicht im leeren Journal.

### C) Paywall + Pricing scharf machen
**Ist:** `index.html:1317–1350` — 2 Tiers (Monthly/Yearly), **keine Preise**, kein Weekly, kein Lifetime, keine Trial-Struktur, keine Free-vs-Pro-Tabelle. Button „Continue with trial" (`:1345`) ohne hinterlegte Trial-Logik (`:1518–1520` ist reiner Placeholder).
**Soll:** Hard Paywall mit 7-Tage-Trial und voller Preis-Hierarchie.

- [ ] Drei Pläne anlegen statt zwei: **Wöchentlich, Monatlich (Empfehlung markiert), Jährlich** + Launch-**Lifetime**.
- [ ] Preise einsetzen — Global (USD): Wöchentlich **$2.99**, Monatlich **$9.99**, Jährlich **$39.99** („Spare 67 %"), Lifetime **$79** (Founding Member). EU (EUR): **€2.90 / €8.99 / €34.99 / €69.99**. (Echte Preise später aus RevenueCat ziehen.)
- [ ] **Preis-Hierarchie pro Monat muss stimmen:** $2.99/Wo (=$12.94) > $9.99/Mo > $3.33 (Jahr). Wer weniger Commitment will, zahlt mehr.
- [ ] Trial-Info sichtbar: „7 Tage kostenlos, dann …", „Jederzeit kündbar".
- [ ] Free-vs-Pro-Vergleichstabelle ergänzen (Strategie-Screen S13).
- [ ] Lifetime nur als zeitlich begrenzter „Founding Member"-Deal labeln (30 Tage nach Launch).
- [ ] `subscribeNowBtn` (`:1345`) + `restorePurchasesBtn` an RevenueCat-Hooks vorbereiten (`@revenuecat/purchases-capacitor`); Placeholder-Texte `:1520 / :1523` für Store-Build ersetzen.

---

## P1 — Positionierung & Copy

### D) Hero & Kern-Copy auf emotionalen Kern + USP umstellen
> **Primärsprache Englisch** — die englische Copy ist die Hauptfassung, Deutsch ist die spätere Übersetzung (Punkt E).
> 📋 **Fertige englische Copy (Hero, Paywall, Store-Listing, Microcopy): `CLIPLOG_COPY_EN.md` → Abschnitte 1, 3, 4, 5.**
**Ist:** `index.html:838` — „Capture your trade the moment it happens, review OCR suggestions, and keep everything on-device without handing over exchange API access." → rein funktional, verkauft das „Warum" nicht.
**Soll:** Emotionaler Kern = Selbstverbesserung. Schärfster Satz der Strategie (EN): **„You know what you should do. How often have you done it anyway?"** (DE später: „Du weißt was du tun solltest. Wie oft hast du es trotzdem nicht getan?")

- [ ] Hero-Subline emotional + USP (EN, primär): z. B. „The trading journal for futures day-traders on Binance, OKX, Bitget & BingX. Screenshot in, trade logged — no API key, no cloud."
- [ ] USP-Satz mindestens einmal prominent platzieren (Hero oder Onboarding S1): „The only journal with native on-device OCR for OKX, Bitget and BingX."
- [ ] Wettbewerbs-Differenzierung sichtbar machen (vs. Trade Snap = Cloud-AI): „Your screenshots stay on your device — not on someone's server." Aktuell nur als Settings-Bullet (`:1218–1222`) versteckt.
- [ ] `manifest.webmanifest` `description` analog umschreiben (kein „BingX"-only mehr — es sind 4 Exchanges).

### E) Sprache / Lokalisierung (Englisch primär, Deutsch sekundär)
**Ist:** App ist zu 100 % Englisch (`<html lang="en">`, alle UI-Texte).
**Soll:** **Englisch ist die Primärsprache** und Basis aller Copy (englischsprachiger Markt zuerst). Deutsch ist die **sekundäre** Lokalisierung, die später dazukommt (DACH als zweiter Markt; Lokalisierung hat generell die höchste LTV-Win-Rate, 62,3 % — daher als früher Folgeschritt einplanen, aber nicht vor dem englischen Launch).

- [ ] Englische UI als sauberen, finalen Stand behandeln (Primärfassung) — `<html lang="en">` bleibt Default.
- [ ] i18n-Struktur so anlegen, dass eine zweite Sprache (DE) ohne Markup-Umbau ergänzt werden kann (Texte aus Markup in ein Strings-Objekt ziehen).
- [ ] Deutsche Übersetzung als **Folge-Task nach dem englischen Launch**, nicht davor.
- [ ] Währung an Store-Region koppeln (USD global / EUR DACH) — vorbereitet für RevenueCat-Regional-Pricing.

> Hinweis: Sample-Screenshots bewusst auf Englisch/Dark-Mode halten (siehe `trade_journal_samples/README.md`) — das betrifft nur den OCR-Input, nicht die App-Sprache.

---

## P2 — Technik-Hinweise (für Store-Version, kein reines Text-Thema)

### F) Bekannte Strategie-Abhängigkeiten (nur tracken, nicht jetzt)
- [ ] OCR: `Tesseract.js` (`index.html:1352`) ist nur Prototyp → Store-Version native (Apple VisionKit / Google ML Kit).
- [ ] Parser ist aktuell **ein** generischer BingX/USDT-Parser (`parseOpenTradeText :1681`, `parseClosedTradeText :1713`, Labels `Amount(USDT)`, `Realized PnL(USDT)` etc.). Strategie = 4 Exchanges → bis zu **4× Open/Closed-Parser**, die bei UI-Änderungen der Exchanges gewartet werden müssen.
- [ ] „Demo membership" / „placeholder"-Texte (`:1206–1207`, `:1262`) vor Store-Release entfernen.

---

## Was bereits on-brand ist (beibehalten)
- Local-only / On-Device-Privacy-Messaging (`:838`, `:1217–1222`, `:1299`) — deckt sich mit USP & DSGVO-Argument.
- „Screenshot-first" Open/Closed-Flow (`:867–919`) — Kernmechanik korrekt.
- About-Zeile „review fast enough that you actually keep the habit" (`:1256`) — trifft den emotionalen Kern, darf aber prominenter werden.
