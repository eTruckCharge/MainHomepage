# TODO: Echte Partnerlogos einbauen — Stand & nächste Schritte

Stand: 2026-08-11. Diese Datei dokumentiert, wo die Recherche/Integration der echten
Partnerlogos (statt der generierten Initialen-Platzhalter) gerade steht, damit die Arbeit
später ohne Kontextverlust fortgesetzt werden kann.

## Bereits fertig integriert (in `assets/img/partners/`, HTML zeigt bereits darauf)

- `dischinger.svg` — Fachspedition Karl Dischinger GmbH (offiziell, karldischinger.de)
- `rlp.svg` — Land Rheinland-Pfalz, Ministerium des Innern (offiziell, mdi.rlp.de)
- `vrn.png` — Verband Region Rhein-Neckar / Metropolregion Rhein-Neckar (offiziell, m-r-n.com)
- `rptu.svg` — RPTU (offiziell, allgemeines RPTU-Logo, nicht lehrstuhlspezifisch)
- `fhnw.svg` — FHNW (offiziell, allgemeines FHNW-Logo, nicht IMVS-spezifisch)
- `schmitt.png` — Walter Schmitt GmbH (offiziell heruntergeladen von logistik-schmitt.de,
  auf dunklen Hintergrund-Chip montiert, da Original weiß/transparent ist)

Diese 6 sind fertig und müssten nur noch committed werden (`git status` zeigt sie als
geänderte/neue Dateien).

## Fast fertig — noch 1 Schritt nötig

- **Chargemap**: Offizielles SVG bereits heruntergeladen nach
  `assets/img/partners/chargemap.svg` (von chargemap.com, direkter CDN-Link). Die HTML-Dateien
  (`de/index.html`, `fr/index.html`, `en/index.html`) referenzieren aber noch
  `assets/img/partners/chargemap.png` (den alten Platzhalter). **Nächster Schritt:** wie beim
  vorherigen Batch per `sed` `chargemap.png` → `chargemap.svg` in allen 3 Sprachdateien
  ersetzen, dann `chargemap.png` (Platzhalter) löschen.

## Im Browser gefunden, aber noch NICHT eingebaut

Liegen als Rohschnitt (Screenshot-Crop von der jeweiligen offiziellen Website) unter
`assets/img/partners/_staging/`. Für jede Datei: prüfen ob Qualität ausreicht, ggf. nachschärfen/
neu zuschneiden, dann nach `assets/img/partners/<slug>.png` verschieben (überschreibt den
Platzhalter) — HTML muss dabei NICHT geändert werden, da die Slugs/Dateinamen bereits mit den
bestehenden `<img>`-Referenzen übereinstimmen (nur Extension beachten, falls SVG vs. PNG).

| Staging-Datei | Ziel-Slug | Quelle | Hinweis |
|---|---|---|---|
| `hka_wordmark_crop.png` | `hka.png` | h-ka.de (Header-Logo) | Nur die Wortmarke "Hochschule Karlsruhe / University of Applied Sciences" (rot). Es gibt zusätzlich ein separates rotes "+HKA"-Kreuz-Symbol oben rechts im Header — evtl. beides kombinieren oder nur die Wortmarke nutzen. |
| `basel-landschaft_crop.png` | `basel-landschaft.png` | baselland.ch (Header) | Gut, sauberer Crop, "BASEL LANDSCHAFT" mit Wappen. |
| `basel-stadt_crop.png` | `basel-stadt.png` | bs.ch (Header) | Nur Text-Wortmarke "Kanton Basel-Stadt", kein Bildzeichen/Wappen auf der Seite gefunden. |
| `solothurn_crop.png` | `solothurn.png` | so.ch (Header) | Gut, "KANTON solothurn" mit rotem Schweizer-Kreuz-Symbol. |
| `ch-npr_crop.png` | `ch-npr.png` | admin.ch (Der Bundesrat) | Offizielles Schweizer Wappen + "Schweizerische Eidgenossenschaft" 4-sprachig. Sehr gut. |
| `strasbourg_crop_darkbg.png` | `strasbourg.png` | strasbourg.eu (Header) | Weißes Logo, dunkler Hintergrund ist im Crop bereits mit eingefangen (dadurch auf weißen Karten sichtbar). Ein direkter PNG-Download (strasbourg.eu/o/strasbourg-theme/images/medias/logo.png) ergab ein unsichtbares weiß-auf-weiß-Bild — nicht verwenden. |
| `trk_crop_lowres.png` | `trk.png` | trk.de (Header) | Funktioniert, aber niedrige Auflösung (90×40px), da der Browser-Tab zwischenzeitlich in eine kleine Viewport-Größe "hängen geblieben" ist (siehe Bug-Hinweis unten). Sollte idealerweise neu/größer eingefangen werden. |
| `cesi_crop.png` | `cesi.png` | strasbourg.cesi.fr (Header) | Gut, "CESI ÉCOLE D'INGÉNIEURS". Achtung: Beim ersten Versuch öffnete sich ein Promo-Popup ("Parcoursup"), das erst weggeklickt werden musste. |

## Noch offen / nicht gefunden

- **CCI Alsace Eurométropole** (`cci-alsace.png`): direkter Downloadlink
  `https://www.alsace-eurometropole.cci.fr/sites/g/files/mwbcuj986/files/LOGO-CCI-alsace-eurometropole-2026-L-250px.png`
  gefunden, aber `curl`-Download schlägt mit HTTP 403 fehl (Hotlink-Schutz). Muss per
  Browser-Tool (claude-in-chrome, Screenshot-Crop wie bei den anderen) geholt werden — noch
  nicht versucht. **Wichtig:** Die aktuell im Repo liegende `cci-alsace.png` wurde
  zwischenzeitlich versehentlich mit der HTTP-403-Fehlerseite überschrieben und dann per
  `git checkout` wieder auf den Platzhalter zurückgesetzt — Stand jetzt ist wieder der
  saubere Platzhalter.
- **IDSS** (Institut für Datenzentrierte Softwaresysteme): Recherche auf h-ka.de zeigt, dass
  es sich um die **"Forschungsgruppe Datenzentrierte Softwaresysteme"** (Leiter: Prof. Dr.
  Christian Zirpins, Professor für Verteilte Systeme) handelt, vermutlich Teil eines größeren
  Instituts (URL-Pfad deutet auf "ISRG"). Kein eigenständiges Logo gefunden — vermutlich nutzt
  die Gruppe HKA-Branding. **Offene Entscheidung für den Nutzer:** Soll die Website-Bezeichnung
  "Institut für Datenzentrierte Softwaresysteme (IDSS)" so bleiben (laut Nutzer-Vorgabe vom
  2026-08-11), oder auf "Forschungsgruppe Datenzentrierte Softwaresysteme" korrigiert werden?
  Der aktuell verwendete Platzhalter-Badge (`idss.png`) bleibt in jedem Fall vorerst bestehen,
  da kein echtes Logo auffindbar war.

## Bug-Hinweis für die Browser-Recherche

Während der Recherche ist der claude-in-chrome-Browser-Tab mehrfach in einen sehr kleinen
Viewport (z.B. 268×103px oder 355×59px) "hängen geblieben", unabhängig von `resize_window`-
Aufrufen. Abhilfe, die funktioniert hat: Tab schließen (`tabs_close_mcp`) und neuen Tab
öffnen (`tabs_context_mcp` mit `createIfEmpty: true` bzw. `tabs_create_mcp`) — danach war der
Viewport wieder normal groß. Beim Fortsetzen der Recherche (z.B. TRK in besserer Auflösung,
oder CCI Alsace) auf diesen Bug vorbereitet sein.

## Sobald alle Logos eingebaut sind

1. Alle Platzhalter-Referenzen geprüft (`grep -rn "partners/" de/ fr/ en/`), Extensions
   (`.png` vs `.svg`) müssen mit den tatsächlichen Dateien übereinstimmen.
2. `assets/img/partners/_staging/` wieder löschen (nur Zwischenablage, nicht Teil der Site).
3. Kurzer Sichtcheck aller drei Sprachseiten im Browser (Partner-Hover + Kontakt-Sektion).
4. Commit mit aussagekräftiger Message; `CLAUDE.md`-Abschnitt "Partnerlogos" aktualisieren
   (aktuell sagt er noch "nur Platzhalter" — das stimmt dann nicht mehr für alle Partner).
