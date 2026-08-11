# eTruckCharge Projekt-Website — Design

## Kontext

eTruckCharge ist ein von der EU über Interreg Oberrhein 2021-2027 kofinanziertes
Projekt (Ref. 22614, Laufzeit 2026-07-02 bis 2029-06-30, Projektträger Hochschule
Karlsruhe, 16 Partner aus Deutschland, Frankreich und der Schweiz). Es soll eine
dreisprachige (DE/FR/EN) One-Pager-Projektwebsite entstehen, gehostet über GitHub
Pages im Repo `eTruckCharge/MainHomepage`.

Quellen für die Inhalte:
- `Antrag_v4_interreg2026_without_finances__RHS_22614-4_applicationform_22329_1783004558.pdf`
  (deutsche Antragsfassung, Version 4, final eingereicht) — primäre Quelle für DE-Texte
- `eTruck-Application-Form-FR.pdf` (französische Antragsfassung, Version 2) — Quelle/Abgleich
  für FR-Texte und offizielle französische Terminologie
- Offizielle Projektseite https://www.interreg-oberrhein.eu/projet/etruckcharge/ (DE/FR) —
  Faktencheck für öffentliche Kennzahlen (Budget, Laufzeit, Partneranzahl)
- https://www.interreg-oberrhein.eu/kommunikation-rund-um-ihr-projekt/ — Pflichten zu
  Kommunikation/Sichtbarkeit
- `Logos_Interreg-Rhin-Sup_Oberrhein.zip` — offizielle Interreg-Logos (DE-FR, FR-DE, EN)
- `Beispiel co-branding eTruckCharge.png` — Referenz für korrekte Logo-Platzierung
- `logo_etruckcharge.png` / `eTruckCharge_logo_transparent.svg` — eTruckCharge-Logo
- `eTruckCharge2.png` — Illustrationsbild einer Ladestation (Hero-Bild)

## Technischer Ansatz

Statische, buildfreie Website. Für jede Sprache ein eigenes HTML-Dokument, gemeinsame
Assets:

```
/index.html              # minimaler Redirect: Accept-Language -> /de|/fr|/en/, Fallback /de/
/de/index.html
/fr/index.html
/en/index.html
/assets/css/style.css
/assets/js/lang-switch.js   # kleines Skript für Sprachumschalter, kein Framework
/assets/img/...              # Logos, Hero-Bild, Interreg/EU-Logos (aus dem Zip entpackt)
```

Alle Asset- und internen Links sind relative Pfade (nicht root-absolut), damit die Seite
sowohl unter `https://etruckcharge.github.io/MainHomepage/` als auch später unter einer
eigenen Domain (CNAME) funktioniert.

Kein Build-Tool, kein Framework, kein npm. GitHub Pages Source wird vom Nutzer selbst auf
"Deploy from branch: main / (root)" gestellt.

## Seitenstruktur (identisch in allen 3 Sprachen)

1. **Header** — eTruckCharge-Logo links, Sprachumschalter (DE | FR | EN) rechts, sticky.
2. **Hero** — `eTruckCharge2.png` als Hintergrund/Seitenbild, Projekttitel + Claim
   ("E-Mobilität grenzenlos — Föderierter Ladepark für nachhaltigen Güterverkehr am
   Oberrhein" / FR- und EN-Entsprechung aus den Anträgen), kurzer Teaser-Satz, 4
   Fakten-Badges: Laufzeit 07/2026–06/2029 · EU-Förderung 1.311.414,60 € · Gesamtbudget
   2.866.829,21 € · 16 Partner (D/F/CH).
3. **Über das Projekt** — Hintergrund/Kontext, Text basierend auf IV.1 Hintergrundinformationen
   (DE) / IV.1 Contexte (FR).
4. **Ziele** — Projektziele, Text basierend auf IV.2 Projektziele (DE) / IV.2 Objectifs (FR).
5. **Erwartete Ergebnisse** — Text basierend auf IV.3 (DE) / IV.3 (FR): föderiertes
   Softwaresystem, KI-Modelle, digitaler Zwilling, Ladealgorithmen, Cybersicherheit.
6. **Zielgruppen & Nutzen** — Text basierend auf IV.4 (DE) / IV.4 (FR).
7. **Partner** — alle 16 Partner als Karten/Liste, gruppiert nach Land (DE/FR/CH),
   Projektträger (Hochschule Karlsruhe) hervorgehoben. Liste aus dem finalen DE-Antrag
   (Version 4, Kapitel II.2):
   - **Deutschland:** Hochschule Karlsruhe (Projektträger), TechnologieRegion Karlsruhe GmbH,
     Verband Region Rhein-Neckar, Walter Schmitt GmbH, Fachspedition Karl Dischinger GmbH,
     RPTU – Lehrstuhl für Mechatronik in Maschinenbau und Fahrzeugtechnik, Land
     Rheinland-Pfalz (Ministerium des Innern, für Integration und Verkehr)
   - **Frankreich:** CESI – Campus de Strasbourg, CHARGEMAP SAS, Chambre de Commerce et
     d'Industrie Alsace Eurométropole, Eurométropole de Strasbourg
   - **Schweiz:** Fachhochschule Nordwestschweiz – Institut für Mobile und Verteilte Systeme
     (IMVS), Schweizerische Eidgenossenschaft (NPR), Kanton Basel-Landschaft (Interreg),
     Kanton Basel-Stadt (Interreg), Kanton Solothurn (Interreg)
8. **Kontakt** — Platzhalter-Sektion mit Hinweis "Kontaktdaten der Hochschule Karlsruhe
   ergänzen" (keine Kontaktdaten in den Quelldokumenten vorhanden).
9. **Footer** — Pflicht-Co-Branding gemäß `Beispiel co-branding eTruckCharge.png`:
   eTruckCharge-Logo | Interreg-Rhin-Supérieur/Oberrhein-Logo | EU-Flagge +
   "Kofinanziert von der Europäischen Union" (DE) / "Cofinancé par l'Union Européenne" (FR) /
   "Co-financed by the European Union" (EN). Link zur offiziellen Projektseite
   https://www.interreg-oberrhein.eu/projet/etruckcharge/. Platzhalter-Links für
   Impressum/Datenschutz (rechtliche Pflichtangaben der Hochschule Karlsruhe müssen
   nachträglich ergänzt werden — nicht Teil dieser Spec, da keine echten Daten vorliegen).

## Interreg-Konformität

- Verwendung der offiziellen Logo-Dateien aus dem Zip: DE-FR-Variante (RGB, transparent,
  Farbe) für die DE- und FR-Seite; EN-Variante ("Permission_requested") für die EN-Seite,
  mit Hinweis im Footer-Kommentar (HTML-Kommentar, nicht sichtbar), dass die Nutzung der
  EN-Logovariante laut Ordnerstruktur eine Genehmigung erfordert und vor Go-Live geprüft
  werden sollte.
- Klarer, in allen drei Sprachen korrekter EU-Förderhinweis im Footer auf jeder Seite.
- Verlinkung zur offiziellen Interreg-Projektseite als "mehr erfahren"-Link im Footer.
- Kein Social-Media-Posting- oder Poster-Bestandteil (außerhalb des Scopes "Website").

## Design/Look

Farbpalette abgeleitet vom eTruckCharge-Logo (Grün- zu Dunkelblau-Verlauf) kombiniert mit
Interreg-Blau als Akzent für Förder-/Partnerbereiche. Moderne, seriöse Optik passend zu
Hochschul-/EU-Förderprojekt. Responsive (Mobile-first), da Zielgruppen auch über Social
Media / Messen auf die Seite zugreifen.

## Texte

- DE: Basis ist der finale deutsche Antrag (Version 4).
- FR: Nicht nur übersetzt, sondern mit dem französischen Antrag (Version 2, offizielle
  Formulierungen) abgeglichen, wo inhaltlich identische Passagen vorhanden sind. Bei
  Abweichungen zwischen v2 (FR) und v4 (DE, z.B. Partnerliste) gilt die DE v4-Liste als
  aktuell (bestätigt durch die offizielle Projektseite: "16 Partner").
- EN: Eigene Übersetzung, da im Programm nicht offiziell zweisprachig — dient als
  zusätzlicher Service, kein Interreg-Pflichtbestandteil.

## Out of Scope

- Impressum/Datenschutz-Inhalte (nur Platzhalter mit TODO-Hinweis)
- Kontaktformular oder Backend jeglicher Art
- CMS oder Mehrseiten-Navigation über die vereinbarte One-Pager-Struktur hinaus
- Automatisches GitHub Pages Setup in den Repo-Settings (muss der Nutzer selbst aktivieren)
