# Handoff — PflegeBox (Bestellschein-pflegebox), 2026-10-03

## Stand
Repo neu geklont (vorher nur auf GitHub, nirgends lokal/governance-seitig
registriert). Ein Bug behoben: Header-Safe-Area-Inset oben fehlte,
Titel/Monatsnavigation lagen unter der iOS-Statusleiste. Fix committet und
gepusht (`5e55bc1`).

## Verifikation
- `npm run typecheck` — 0 Fehler.
- `npm test` — 16/16 PASS.
- `npm run e2e` — 3/5 PASS, PDF-Download-Schritt timeout (vorbestehend,
  auch ohne meinen Fix reproduziert — keine Regression).

## Offen
- Produkt-Hierarchie-Zugehörigkeit zu IRIS Digital ungeklärt — s.
  `CLAUDE.md` in diesem Ordner.
- PDF-Download-E2E-Schritt in dieser Sandbox nicht lauffähig (Ursache nicht
  tiefer untersucht, außerhalb des Auftragsumfangs).
- Keine Verschlüsselung/kein PIN-Schutz für die erfassten Gesundheitsdaten
  (laut README bewusst so, nicht von mir neu gefunden) — ggf. mit René
  klären, ob das geändert werden soll.
- Kein Vier-Augen-Gegenprüfer-Lauf (testing-qa) für diesen Fix.
