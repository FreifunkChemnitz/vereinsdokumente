# Vereinsdokumente Freifunk Chemnitz e.V.

Satzung, Beitragsordnung und Mitgliedsantrag des Freifunk Chemnitz e.V. als LaTeX-Quellen samt fertig gebauter PDFs.

| Dokument | Quelle | PDF |
| --- | --- | --- |
| Vereinssatzung | [Freifunk-Satzung.tex](Freifunk-Satzung.tex) | [Freifunk-Satzung.pdf](Freifunk-Satzung.pdf) |
| Beitragsordnung | [Freifunk-Beitragsordnung.tex](Freifunk-Beitragsordnung.tex) | [Freifunk-Beitragsordnung.pdf](Freifunk-Beitragsordnung.pdf) |
| Mitgliedsantrag | [Mitgliedsantrag.tex](Mitgliedsantrag.tex) | [Mitgliedsantrag.pdf](Mitgliedsantrag.pdf) |

## Bauen

Es wird nur Docker benötigt; TeX Live und Inkscape laufen als Services aus der [docker-compose.yml](docker-compose.yml).

Zuerst das Logo aus der SVG erzeugen (`ffc.png` ist nicht eingecheckt):

```bash
docker compose run --rm inkscape --export-dpi=300 --export-filename=ffc.png ffc.svg
```

Dann die Dokumente bauen:

```bash
docker compose run --rm tex lualatex Freifunk-Satzung.tex
docker compose run --rm tex lualatex Freifunk-Beitragsordnung.tex
docker compose run --rm tex lualatex Mitgliedsantrag.tex
```

Die PDFs liegen im Repo. Nach einer Änderung an einer `.tex`-Datei das zugehörige PDF neu bauen und mit einchecken.

## CI

Die [.gitlab-ci.yml](.gitlab-ci.yml) baut alle Dokumente mit lualatex, pdflatex und xelatex und veröffentlicht die PDFs über GitLab Pages.

## Lizenz

Gemeinfrei (Unlicense), siehe [LICENSE](LICENSE).
