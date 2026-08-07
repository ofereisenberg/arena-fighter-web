# Arena Fighter — Web-Export

Statischer Godot-4.7-Web-Export (Compatibility-Renderer) des Spiels `arena-fighter`
(`C:\Users\ofere\OneDrive\Documents\arena-fighter`). Wird per GitHub Pages gehostet:

**https://ofereisenberg.github.io/arena-fighter-web/**

Eingebettet auf [Noams Website](https://github.com/ofereisenberg/website-noam) per iframe
(siehe dort `web/src/lib/gameConfig.ts`).

## Warum ein eigenes Repo statt Teil der Website?

Der `.wasm`-Build ist ~36 MB groß - größer als das 25-MB-Limit für Cloudflare Workers
Static Assets (die Website läuft auf Workers). Cloudflare R2 hätte das gelöst, braucht aber
eine hinterlegte Zahlungsmethode; GitHub Pages ist komplett kostenlos und reicht für die
paar MB völlig aus.

## Aktualisieren nach Godot-Änderungen

1. In Godot: **Project → Export... → Export Project** (Web-Preset, überschreibt den
   `export/web/`-Ordner im Godot-Projekt).
2. Alle Dateien außer den `.import`-Dateien (die brauchen nur den Editor) hier reinkopieren
   und committen/pushen:
   ```
   git add -A
   git commit -m "Update Web-Export"
   git push
   ```
3. GitHub Pages baut automatisch neu (dauert ~30-60 Sekunden), keine weiteren Schritte
   nötig - kein erneutes `wrangler deploy` auf der Website-Seite, da dort nur eine URL
   referenziert wird.
