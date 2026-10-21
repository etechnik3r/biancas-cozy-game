# Arbeitsanweisungen für Claude – Bianca Game

Dieses Repo enthält „Biancas Leseecke“, ein Cozy-Browserspiel für Biancas Handy. Bastian entwickelt es zusammen mit Claude. Diese Datei gilt für jede Sitzung, egal ob in claude.ai, Claude Code oder VS Code.

## Zu Beginn jeder Sitzung
1. `git log --oneline -20` und `CHANGELOG.md` lesen, um den aktuellen Stand zu kennen.
2. `docs/offene-punkte.md` lesen.
3. Bei inhaltlichen Fragen zum Spiel `docs/konzept.md` lesen. Das Konzept ist die verbindliche Grundlage.

## Während der Arbeit
- **Bei Unklarheiten nachfragen statt Annahmen treffen.** Das gilt besonders für Spielregeln, Grafikstil und Texte.
- **Mehrere Aufgaben in kleine Häppchen aufteilen** und nacheinander abarbeiten. Jedes Häppchen wird einzeln getestet und committet.
- **Harte Fakten** (Browser-Verhalten, iOS-Eigenheiten, API-Details) nur mit Quelle oder offen ausgesprochener Unsicherheit nennen.
- Lieferungen sind **vollständig und lauffähig**, keine halben Code-Schnipsel.
- Kommunikation auf Deutsch, Bastian wird geduzt.

## Nach jeder inhaltlichen Änderung
1. `CHANGELOG.md` aktualisieren (Abschnitt „Unveröffentlicht“, neueste Einträge oben).
2. `docs/offene-punkte.md` pflegen: Erledigtes entfernen, Neues eintragen.
3. Weicht die Umsetzung vom Konzept ab, `docs/konzept.md` mit anpassen.
4. Committen mit aussagekräftiger Nachricht auf Deutsch.

## Am Ende jeder Sitzung
- `git push`.
- Kurz zusammenfassen, was erledigt ist und was als Nächstes ansteht.

## Versionierung
- Versionsnummern nach dem Schema `MAJOR.MINOR.PATCH` (z. B. `0.1.0`).
- Ein Release entsteht, wenn Bastian eine Version an Bianca weitergibt. Dann wandert „Unveröffentlicht“ im Changelog unter die neue Versionsnummer mit Datum, und es gibt einen Git-Tag `vX.Y.Z`.

## Technische Leitplanken
- **Eine einzelne Datei `index.html`** mit Vanilla JS und CSS. Keine Bibliotheken, kein Build-Schritt.
- **Grafik ausschließlich als parametrisch erzeugtes Inline-SVG.** Keine Emojis, keine Bilddateien, keine KI-generierten Bilder.
- **Sound nur per Web Audio API synthetisiert**, keine Audiodateien. Immer mit Stummschalter.
- Hochformat, Handy zuerst. Tippflächen mindestens 44 px.
- Spielstand in `localStorage`, jeder Zugriff in `try/catch`. Das Spiel muss auch ohne Speicher laufen.
- Offline lauffähig, keine externen Abhängigkeiten zur Laufzeit.
- Aufwand im Blick behalten: Ziel ist eine erste Version an einem Abend. Neue Ideen erst in `docs/offene-punkte.md` unter „Später“ notieren, nicht direkt einbauen.

## Grafik-Generatoren
- Der Block `GRAFIK-GENERATOREN` steht identisch in `index.html` und `musterblatt.html`. Änderungen immer in beiden Dateien vornehmen (oder von `index.html` ins Musterblatt kopieren).

## Testen
- Jede Änderung im Browser in Handygröße prüfen (ca. 375 × 667 px).
- Puzzle-Logik: Jedes erzeugte Level muss vom Löser als lösbar bestätigt sein.
