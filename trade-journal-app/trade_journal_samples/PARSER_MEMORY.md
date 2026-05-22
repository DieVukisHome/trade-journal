# Parser Memory

Diese Datei dient als dauerhafte lokale Referenz fuer bestaetigte Screenshot-Strukturen, Parser-Annahmen und Tutorial-Hinweise pro Boerse.

## Allgemeine Regeln

- `open` Screenshots:
  - zeigen typischerweise Einstieg / Order-Fill / Direction / Amount / Filled / Avg oder Fill Price / Time
- `closed` Screenshots:
  - zeigen typischerweise Entry / Exit / Realized PnL / weitere Resultatdaten / Open- und Close-Zeit
- `tutorial` Screenshots:
  - sind nicht primaer fuer OCR
  - dienen fuer boersenspezifisches Onboarding und Hilfe

- Fuer die Store-App gilt aktuell als Arbeitsannahme:
  - `Open` und `Closed` sind die zentrale fachliche Trennung
  - `Realized PnL` ist der Standard-Anzeigewert im Review
  - `Closed PnL` soll trotzdem separat erhalten bleiben, wenn vorhanden

## Produkt- und Parser-Stand allgemein

### Aktueller Produktstand

- Die aktuelle App ist noch ein Web-/Browser-Prototyp.
- OCR laeuft dort aktuell ueber `Tesseract.js`.
- Fuer die spaetere Store-Version ist native OCR vorgesehen:
  - iPhone: Apple `Vision` / `VisionKit`
  - Android: Google `ML Kit`

### Aktuelle Review-Logik

- Im Review zaehlen nur `closed` Trades.
- Der sichtbare Hauptwert ist aktuell:
  - primaer `Realized PnL`
  - Fallback `Closed PnL`
- Beide Werte sollen getrennt erhalten bleiben.

### Daten- und Diagramm-Annahmen

- `1W`, `1M`, `All` sind die gewuenschten Review-Zeitraeume.
- Die Linie startet immer bei `0`.
- Das Diagramm soll sich dynamisch aus vorhandenen `closed` Trades mit `Realized PnL` aufbauen.
- Bei `1M` soll der aktuelle Monat Standard sein, mit Wechsel auf vorherige Monate.
- Bei dichterem Daytrading ist eine feine Linien-/Punktedarstellung wichtig.

## OKX

### Status

OKX ist aktuell die am besten dokumentierte Zusatzboerse nach BingX und reicht fuer einen ersten echten Parser-Entwurf.

Vorhanden:

- `open`:
  - Open Short
  - Open Long
  - mehrere Beispiele mit unterschiedlichen Coins / Zahlen
- `closed`:
  - Closed Loss
  - Closed Win
  - mehrere Beispiele mit positivem und negativem `Realized PnL`
- `tutorial`:
  - mehrere Screens fuer den Weg zur History / Position-History

### Bestaetigte Open-Felder

Aus den bisherigen OKX-`open`-Screens lassen sich stabil erkennen:

- `Coin`
- `Direction`
  - `Buy` entspricht Long
  - `Sell` entspricht Short
- `Isolated`
- `Leverage`
- `Time`
- `Order amount (USDC)`
- `Filled (USDC)`
- `Fill price`

### Bestaetigte Closed-Felder

Aus den bisherigen OKX-`closed`-Screens lassen sich stabil erkennen:

- `Coin`
- `Direction`
- `Closed`
- `Entry price`
- `Exit price`
- `Realized PnL (USDC)`
- `Realized PnL %`
- `Max held (USDC)`
- `Closed (USDC)`
- `Time opened`
- `Closed` Zeit / Close-Zeit

### Parser-Hinweise fuer OKX

- `Realized PnL` ist auf OKX klar sichtbar und sollte primaer gelesen werden.
- Gewinn und Verlust sind strukturell gleich aufgebaut.
- Die Farbe aendert sich, aber der Parser soll sich nicht auf Farben verlassen.
- Stattdessen auf Labels, Positionsmuster und Zahlenformate setzen.
- `Entry price` / `Exit price` sind klar benannt und gut fuer Closed-Screens nutzbar.
- `Buy` / `Sell` als Direction-Mapping verwenden.
- `My trades` ist als Seitentitel vorhanden, aber kein notwendiges Kernmerkmal fuer Feldextraktion.

### Tutorial-Hinweise fuer OKX

Die vorhandenen `tutorial`-Screens sind geeignet, um spaeter in der App zu zeigen:

- wie man im `Futures`-Bereich landet
- wo `Positions & assets` sichtbar ist
- wie man weiter zur `Order history` oder `Position history` navigiert

### Noch hilfreich, aber nicht kritisch

Optional spaeter sammeln:

- weiterer Open Long mit anderem Coin
- weiterer Closed Win oder Loss mit anderem Umbruch
- Beispiel mit engerem oder dichterem Zahlenlayout

## BingX

### Status

BingX war die urspruengliche Referenzboerse fuer den ersten Web-Prototyp und ist die bisher wichtigste Parser-Basis.

### Bestaetigte Open-Felder

Aus den bisherigen BingX-Open-Screens lassen sich in der aktuellen Parser-Logik erkennen:

- `Coin`
- `Direction`
  - `Open Long`
  - `Open Short`
- `Amount(USDT)` oder `Amount`
- `Filled(USDT)` oder `Filled`
- `Avg. Price`
- `Time` / `Open Time`

### Bestaetigte Closed-Felder

Aus den bisherigen BingX-Closed-Screens lassen sich in der aktuellen Parser-Logik erkennen:

- `Coin`
- `Direction`
- `Realized PnL(USDT)` / `Realized PnL`
- `Closed PnL(USDT)` / `Closed PnL`
- `Entry Price`
- `Avg. Close Price`
- `Open Time`
- `Close Time`

### Parser-Hinweise fuer BingX

- Open- und Closed-Screens wurden bereits fuer den bisherigen OCR-Flow verwendet.
- BingX-spezifische Felder und Erkennung sind bereits die Grundlage des aktuellen Browser-Prototyps.
- `Realized PnL` wird aktuell als primaerer Wert gelesen.
- `Closed PnL` bleibt als Fallback in der Logik.
- OCR-Normalisierungen, die im aktuellen Prototyp bereits verwendet werden:
  - `USOT -> USDT`
  - `CIosed -> Closed`
  - `ReaIized -> Realized`
  - `Ciose -> Close`
  - `0pen -> Open`
- Parser setzt aktuell stark auf:
  - Header-/Symbolerkennung
  - Labels fuer Zeit- und Preisfelder
  - `Long` / `Short` bzw. `Open Long` / `Open Short`

### Besonderheiten

- BingX-Screens waren die Grundlage fuer:
  - Coin-Erkennung
  - Direction-Erkennung
  - Open-vs.-Closed-Flow
  - manuelle PnL-/Win-Loss-Normalisierung im Journal

### Noch offen

- die bisher genutzten BingX-Screens sollten spaeter wie OKX noch explizit im Sample-Ordner mit `open`, `closed`, `tutorial` gesammelt werden
- Tutorial-Material fuer BingX ist noch nicht separat dokumentiert

## Binance

### Status

- noch keine bestaetigten Screens dokumentiert

### Ziel

- spaeter dieselbe Struktur aufbauen wie bei OKX:
  - `open`
  - `closed`
  - `tutorial`

## Bitget

### Status

- noch keine bestaetigten Screens dokumentiert

### Ziel

- spaeter dieselbe Struktur aufbauen wie bei OKX:
  - `open`
  - `closed`
  - `tutorial`

## Bitunix

### Status

- noch keine bestaetigten Screens dokumentiert

### Ziel

- spaeter dieselbe Struktur aufbauen wie bei OKX:
  - `open`
  - `closed`
  - `tutorial`
