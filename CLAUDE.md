# eTruckCharge Projekt-Website

Statische, dreisprachige One-Pager-Website (Deutsch, Französisch, Englisch) für das
Interreg-Oberrhein-Projekt eTruckCharge (Ref. 22614). Kein Build-Prozess, gehostet über
GitHub Pages.

## Struktur

```
/de/index.html   /fr/index.html   /en/index.html   – je eine vollständige Sprachversion
/assets/css, /assets/js, /assets/img               – gemeinsam genutzte Assets
/index.html                                        – Redirect auf Browsersprache (Fallback DE)
```

## Wichtige Regel: Alle drei Sprachen synchron halten

**Jede inhaltliche oder strukturelle Änderung an der Website muss in allen drei
Sprachversionen (`de/`, `fr/`, `en/`) nachgezogen werden**, nicht nur in einer. Das gilt für:

- Textänderungen (neue Absätze, geänderte Zahlen/Fakten, neue Partner, etc.)
- Neue oder entfernte Sektionen
- Strukturelle/HTML-Änderungen (neue Elemente, geänderte Klassen, neue Links)
- Änderungen an den Fakten-Badges im Hero (Laufzeit, Budget, Partneranzahl)

Rein sprachneutrale Änderungen (CSS in `assets/css/style.css`, gemeinsame Bilder/Logos)
betreffen alle drei Seiten automatisch und müssen nicht dupliziert werden.

Beim Übersetzen: nicht nur wörtlich übersetzen, sondern nach Möglichkeit mit den offiziellen
deutschen und französischen Antragsformulierungen abgleichen (siehe Quellen unten). Englisch
ist im Interreg-Programm nicht offiziell erforderlich, wird hier aber als zusätzlicher Service
gepflegt und muss trotzdem synchron bleiben.

## Quellen für Inhalte

- Deutsche Antragsfassung (final, Version 4) und französische Antragsfassung (Version 2)
- Offizielle Projektseite: https://www.interreg-oberrhein.eu/projet/etruckcharge/
- Kommunikationsvorgaben: https://www.interreg-oberrhein.eu/kommunikation-rund-um-ihr-projekt/

## Interreg-Konformität

- Footer: Pflicht-Co-Branding (eTruckCharge-Logo, Interreg-Logo, EU-Förderhinweis) muss auf
  jeder Seite vorhanden und in der jeweiligen Sprache korrekt beschriftet sein. Die englische
  Interreg-Logovariante ist laut Asset-Paket "Permission requested" – bis zur Freigabe wird
  auf der EN-Seite die offizielle DE/FR-Lockup-Grafik weiterverwendet und der Förderhinweis
  nur als Text auf Englisch ergänzt.
- Header: Das EU-Emblem (`assets/img/interreg/eu-emblem-de.png` bzw. `-fr.png`, aus dem
  offiziellen Lockup zugeschnitten) steht oben rechts und muss sichtbar größer dargestellt
  werden als das eTruckCharge-Logo oben links (`.site-header .brand img` vs.
  `.header-top .eu-emblem img` in `assets/css/style.css`) – das ist eine EU-Förder­vorgabe zur
  Logogröße, nicht nur Geschmackssache. Bei Layoutänderungen im Header diese Größenrelation
  beibehalten.

## Partnerlogos

- Liegen in `assets/img/partners/<slug>.png` bzw. `.svg`, referenziert in der Partnerliste
  (Hover/Fokus zeigt das Logo über dem Partnernamen, siehe `.partner-logo-preview` in
  `assets/css/style.css`) sowie im Kontakt-Bereich (`.hka-logos`).
- **Echte Logos eingebaut** für alle Partner außer IDSS: die meisten offiziell von den
  jeweiligen Institutions-/Firmenwebsites heruntergeladen bzw. als Screenshot-Crop übernommen.
  Sobald bessere/offizielle Dateien vorliegen (z. B. `trk.png`, das aktuell niedrig aufgelöst
  ist), einfach unter demselben Dateinamen/Slug ersetzen – keine HTML-Änderung nötig.
- **Nur `idss.png` ist noch ein Platzhalter** (generiertes Initialen-Badge): kein
  eigenständiges Logo auffindbar, siehe nächster Punkt.
- Hochschule Karlsruhe (HKA) ist **Konsortialleiter** (nicht "Projektträger"/"Lead partner" –
  das war eine falsche Übersetzung aus dem Antragsformular) und im Projekt vertreten durch das
  **Institut für Datenzentrierte Softwaresysteme (IDSS)** / *Institut des systèmes logiciels
  centrés sur les données* / *Institute of Data-centric Software Systems*. Recherche (Stand
  2026-08-12) fand dazu nur eine "Forschungsgruppe Datenzentrierte Softwaresysteme" (Leitung:
  Prof. Dr. Christian Zirpins) ohne eigenständiges Logo – die Bezeichnung "IDSS" bleibt auf der
  Website trotzdem bestehen (bestätigte Nutzer-Vorgabe). Beide Logos (HKA + IDSS) gehören
  zusammen dargestellt; `hka.png` ist das echte Logo, `idss.png` bleibt vorerst Platzhalter.

Siehe auch die Design-Spec: `docs/superpowers/specs/2026-08-11-etruckcharge-website-design.md`
