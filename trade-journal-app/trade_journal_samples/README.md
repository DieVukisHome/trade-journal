# Trade Journal Screenshot Checklist

Lege deine Screenshots bitte in diesen Ordnern ab:

- `binance/open`
- `binance/closed`
- `binance/tutorial`
- `okx/open`
- `okx/closed`
- `okx/tutorial`
- `bitget/open`
- `bitget/closed`
- `bitget/tutorial`
- `bingx/open`
- `bingx/closed`
- `bingx/tutorial`
- `bitunix/open`
- `bitunix/closed`
- `bitunix/tutorial`

## Was ich pro Boerse brauche

Bitte pro Boerse idealerweise:

- `5-10` Open-Screenshots
- `5-10` Closed-Screenshots

Je mehr Varianz, desto besser. Besonders hilfreich:

- `Long`
- `Short`
- `Win`
- `Loss`
- verschiedene Coins
- verschiedene Uhrzeiten / Sessions
- kleine und grosse PnL-Werte

## Wichtige Regeln

- Bitte echte Screenshots direkt vom iPhone verwenden
- Bitte moeglichst alles in derselben Sprache halten, idealerweise Englisch
- Bitte moeglichst denselben App-Look verwenden, idealerweise Dark Mode
- Bitte keine persoenlichen Daten extra markieren oder umbenennen
- Bitte keine Screenshots zuschneiden, wenn es nicht noetig ist

## Was ist Open / Closed

`open`:
- Screenshot eines noch offenen Trades oder Order-Fills
- typischerweise mit Einstieg, Direction, Amount, Filled, Avg Price, Time

`closed`:
- Screenshot eines bereits geschlossenen Trades
- typischerweise mit Realized PnL, Closed PnL, Open Time, Close Time, Entry Price, Avg Close Price

`tutorial`:
- Screenshot, der zeigt, wie man in der jeweiligen Boerse zur Trade-History oder Position-History kommt
- diese Screens sind nicht primaer fuer den OCR-Parser
- sie sind primaer fuer Onboarding, Hilfe und boersenspezifische Erklaerungen in der App

## Dateibenennung

Bitte wenn moeglich so benennen:

- `open_long_win_01.jpg`
- `open_short_02.jpg`
- `closed_long_loss_01.jpg`
- `closed_short_win_02.jpg`

Wenn du das nicht sauber benennen willst oder kannst, ist das auch ok. Die Ordnerstruktur ist wichtiger als die Dateinamen.

Fuer `tutorial` kannst du zum Beispiel so benennen:

- `tutorial_trade_history_01.png`
- `tutorial_position_history_01.png`
- `tutorial_where_to_tap_01.png`

## Prioritaet

Falls du nicht alles auf einmal liefern willst, bitte in dieser Reihenfolge:

1. `bingx`
2. `binance`
3. `okx`
4. `bitget`
5. `bitunix`

## Ziel

Mit diesen Beispielen kann ich:

- Open- und Closed-Layouts pro Boerse vergleichen
- gemeinsame Felder identifizieren
- OCR-Normalisierung verbessern
- parser-spezifische Unterschiede dokumentieren
- boersenspezifische Tutorial-Hinweise fuer die App vorbereiten
