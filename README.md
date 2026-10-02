# Redezeit-Timer

Mobiler Redezeit-Timer im Toastmasters-Stil: Der ganze Bildschirm wird grün, gelb und rot, wenn die eingestellten Zeiten erreicht sind.

**Live:** https://mvonulmerbach-ship-it.github.io/redezeit-timer/

## Bedienung

- **Start / Pause / Weiter** und **Reset** unten; Tippen aufs Bild startet oder pausiert ebenfalls.
- Zahnrad ⚙ oben rechts: Zeiten für Grün, Gelb und Rot (Minuten : Sekunden, je 0–59) mit − und + oder per Tastatur einstellen. Vorlagen: Stegreif 1–2 Min, Kurzrede 4–6 Min, Rede 5–7 Min, Rede 7–9 Min. Standard ist 5–7 Min.
- Bei jedem Farbwechsel vibriert das Handy kurz. Der Bildschirm bleibt an, solange der Timer läuft (Wake Lock).
- Die Zeit wird aus der Uhrzeit berechnet (`Date.now()`), sie driftet also nicht. Die eingestellten Zeiten werden im Browser gespeichert (`localStorage`, Schlüssel `redetimer`).

## Bewusste Abweichungen vom Mini-App-Muster

- **Nur dunkel, kein Hell/Dunkel-Schalter:** Der Timer läuft vor Publikum oder auf dem Pult. Ein dunkler Grund blendet nicht, und die Phasenfarben Grün, Gelb und Rot füllen ohnehin den ganzen Bildschirm.
- **`orientation: any`:** Der Timer soll auch quer auf dem Tisch oder am Tablet stehen können.

Die Schrift- und Knopffarben sind je Phase so gewählt, dass sie lesbar bleiben: Grün und Rot mit weißer Schrift, Gelb mit dunkler Schrift und dunklen Knöpfen.

## Dateien

| Datei | Zweck |
|---|---|
| `index.html` | die ganze App (HTML, CSS, JavaScript) |
| `manifest.webmanifest`, `icon-192.png`, `icon-512.png`, `icon-maskable-512.png`, `apple-touch-icon.png` | Installation als App |
| `sw.js` | Service Worker für den Offline-Betrieb |

## Auf dem Handy installieren

Seite in Chrome öffnen → Menü ⋮ → „Zum Startbildschirm hinzufügen“ (Safari: Teilen → „Zum Home-Bildschirm“).

## Offline

Nach dem ersten Öffnen läuft der Timer ohne Netz (Service Worker, network first mit Cache als Rückfall) – auch in Sitzungsräumen ohne Empfang.
