# PflegeBox (Bestellschein-pflegebox) | Silo-Governance (Genesis 2026-10-03)

> Genesis-Eintrag (2026-10-03) — Repo war bereits auf GitHub vorhanden
> (`Renekrieg1401/Bestellschein-pflegebox`), aber lokal nicht geklont und
> nirgends registriert. Geklont nach einem Header-Bugreport (Safe-Area-
> Inset fehlte, Header rutschte unter die iOS-Statusleiste).

## Was ist PflegeBox
Monatlicher Bestellschein für Pflegehilfsmittel zum Verbrauch (§ 40 SGB XI
„Pflegebox") — Handschuhe (S/M/L), Waschhandschuhe, Unterlagen,
Desinfektionsmittel (Hände/Flächen), Wipes (Hände/Flächen), Inkontinenz-
material je Person. Reine clientseitige PWA, kein Backend, kein CDN,
offlinefähig, Export als Vektor-PDF oder JPG.

## Quelle & Eigentum
- GitHub: `Renekrieg1401/Bestellschein-pflegebox` (persönlicher Account)
- Lokal: `/Users/kriegrene/Development/IRIS-DIGITAL/Projekte/Bestellschein-pflegebox/`
- Deployment: GitHub Pages direkt aus dem Repo-Wurzelverzeichnis (laut README)
- **Zugehörigkeit zur IRIS-Digital-Produkthierarchie UNGEKLÄRT** — anders
  als AERIS/ZEUS/FORMA trägt das Repo keine IRIS-Digital-Markenbezüge
  (eigene Lila/Cyan-Palette, App-Titel „PflegeBox", keine Erwähnung von
  IRIS Digital im Code). Nicht eigenmächtig als „zehntes Produkt" in die
  Produkt-Hierarchie der Root-CLAUDE.md aufgenommen — nur als technisches
  Silo registriert, damit Silo-Isolation greift. Einordnung bei Bedarf mit
  René klären.

## Architektur (laut README, nicht eigenständig verifiziert)
- Datenschicht/Migration/Update-Mechanik an AERIS-Doku-Logik angelehnt
  (`js/store.js`, `js/model.js`, `js/update.js`, `sw.js`).
- Eigener PDF-1.4-Writer (kein html2canvas/jsPDF), Vektordruck.
- **Keine Verschlüsselung/kein PIN-Schutz:** laut README liegen Namen/
  Bestellungen (Art. 9 DSGVO-Gesundheitsdaten) unverschlüsselt im
  Browser-Speicher — anders als AERIS Doku/Buch. Das ist eine bewusste
  README-eigene Feststellung, keine von mir neu entdeckte Lücke.

## Status — Erstkontakt, nicht vollständig geprüft
- Fix 2026-10-03 (`app.css:85-89`): `env(safe-area-inset-top)` im
  Header-Padding ergänzt — Header rutschte bei `viewport-fit=cover` unter
  die iOS-Statusleiste/Dynamic Island. Commit `5e55bc1`, gepusht.
- Verifikation: `npm run typecheck` (0 Fehler), `npm test` (16/16 PASS).
  `npm run e2e`: 3 von 5 Schritten PASS, PDF-Download-Schritt bricht mit
  Timeout ab — **vorbestehend, nicht durch den Fix verursacht** (gegen den
  unveränderten Stand gegengetestet, identischer Fehler). Vermutlich ein
  Sandbox-/Headless-Chromium-Limit bei dieser speziellen PDF-Blob-
  Download-Route, nicht weiter untersucht (außerhalb des Auftragsumfangs).
- Kein `handoff.md` bisher vorhanden — angelegt, s. `handoff.md` in diesem
  Ordner.
- Kein Vier-Augen-Gegenprüfer-Lauf (testing-qa) — Komplexitäts-Gate:
  Einzeiliger CSS-Fix, Score <6, direkt durch Claude erledigt.
