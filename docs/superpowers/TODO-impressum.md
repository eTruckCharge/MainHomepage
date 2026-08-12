# TODO: Impressum-Angaben im Kontakt-Bereich ergänzen

Stand: 2026-08-12. Der Footer-Link "Impressum" / "Legal notice" / "Mentions légales" verweist
inzwischen in allen drei Sprachen auf den bestehenden Kontakt-Bereich (`#kontakt` in `de/`,
`#contact` in `fr/` und `en/`) statt auf `#`. Der separate "Datenschutz"/"Privacy policy"/
"Confidentialité"-Link wurde entfernt, da die Website keine Nutzerdaten erhebt (kein Tracking,
keine Formulare, keine Cookies).

Der Kontakt-Bereich (`.contact-box` in `de/index.html`, `fr/index.html`, `en/index.html`)
enthält aktuell nur Name, Adresse und Website-Link der Hochschule Karlsruhe – das reicht
rechtlich nicht als vollständiges Impressum. Fehlende Pflichtangaben (§5 DDG, ehem. TMG, und
§18 Abs. 2 Medienstaatsvertrag):

1. **Vertretungsberechtigte Person** – z. B. "gesetzlich vertreten durch den Rektor/die
   Rektorin, Prof. Dr. [Name]" (oder die eTruckCharge-Projektleitung, falls passender).
2. **Direkter Kontakt** – Telefonnummer und/oder E-Mail-Adresse (aktuell nur der Website-Link
   vorhanden).
3. **Aufsichtsbehörde** – vermutlich Ministerium für Wissenschaft, Forschung und Kunst
   Baden-Württemberg, aber noch nicht bestätigt.
4. **Umsatzsteuer-ID** – falls vorhanden/zutreffend, sonst weglassen.
5. **Inhaltlich verantwortliche Person** (§18 Abs. 2 MStV) – Name + Anschrift einer
   natürlichen Person.

Diese Angaben wurden bewusst nicht erfunden/geraten, da falsche Angaben in einem Impressum
rechtlich riskant sind. Ein E-Mail-Entwurf an das Interreg-Oberrhein-Office mit genau diesen
Rückfragen (inkl. der Frage, ob eine gesonderte Datenschutzerklärung trotz fehlender
Datenerhebung nötig ist, und ob es Interreg-spezifische Impressum-Vorgaben gibt) wurde im Chat
am 2026-08-12 erstellt, aber noch nicht verschickt (keine verifizierte Empfängeradresse
verfügbar).

## Nächste Schritte

1. Antwort des Interreg-Office abwarten bzw. E-Mail-Entwurf verschicken (Empfängeradresse aus
   der offiziellen Kontaktseite https://www.interreg-oberrhein.eu holen).
2. Sobald die 5 obigen Punkte als gesicherte Fakten vorliegen: `.contact-box` in allen drei
   Sprachversionen um diese Angaben ergänzen (auf Übersetzungskonsistenz achten, siehe
   Drei-Sprachen-Regel in `CLAUDE.md`).
3. Prüfen, ob nach Ergänzung ein eigener "Impressum"-Abschnitt/-Kicker im Kontakt-Bereich
   sinnvoller ist als die reine Weiterleitung per Anchor-Link.
