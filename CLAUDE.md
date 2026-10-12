# Vereinsdokumente Freifunk Chemnitz e.V.

LaTeX-Quellen und gebaute PDFs für Satzung, Beitragsordnung und Mitgliedsantrag. Dokumentsprache ist Deutsch.

## Bauen

Nur über Docker, nichts lokal installieren:

```bash
docker compose run --rm inkscape --export-dpi=300 --export-filename=ffc.png ffc.svg
docker compose run --rm tex lualatex <Dokument>.tex
```

- `ffc.png` wird aus `ffc.svg` erzeugt und ist per `.gitignore` ausgeschlossen. Ohne die Datei schlägt jeder Build fehl.
- Das Logo mit 300 dpi exportieren; höhere Auflösung bläht nur die PDFs auf.
- Die PDFs sind eingecheckt. Nach jeder Änderung an einer `.tex`-Datei das PDF neu bauen und mit committen.
- Das Datum auf dem Titelblatt von Satzung und Beitragsordnung kommt aus `\datum` (Beschlussdatum, aktuell 26.09.2026), nicht aus `\today`.
- Das Logo in der Kopfzeile steht in `\smash`, damit es nach oben in den Rand ragt und nicht über den Text rutscht.
- Die GitLab-CI baut mit lualatex, pdflatex und xelatex. Neue Dokumente müssen mit allen drei Engines kompilieren.

## Inhaltliche Regeln

- Satzung und Beitragsordnung sind von der Mitgliederversammlung beschlossene Texte. Wortlaut nur auf ausdrückliche Anweisung ändern, keine stilistischen Korrekturen.
- Vorstand und Bankverbindung stehen in der Fußzeile von `Mitgliedsantrag.tex`. Kontoinhaber ist Steffen Förster, nicht der Verein.
- Der Mitgliedsantrag muss auf eine Seite passen. Nach Änderungen das PDF rendern und ansehen.

## Git

- Commit-Nachrichten auf Deutsch, im Conventional-Commits-Format (Typ und Scope bleiben englisch).
- Änderungen über Branch und Pull Request auf GitHub (`FreifunkChemnitz/vereinsdokumente`).
