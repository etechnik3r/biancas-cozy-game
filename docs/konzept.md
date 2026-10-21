# Konzept: Biancas Leseecke (v1)

**Stand:** 21.10.2026

**Idee in einem Satz:** Bianca sortiert Bücher, Pflanzen und Teekannen in ruhigen Regal-Puzzles und richtet sich mit den Belohnungen eine kleine, gemütliche Leseecke ein.

**Zielgruppe:** Bianca, Bekannte von Bastian. Sie dekoriert gern und puzzelt wahrscheinlich auch gern. Das Spiel dient zur Entspannung.

**Rahmen:** Browserspiel fürs Handy, erste Version an einem Abend umsetzbar.

## Spielablauf
1. Start in der **Leseecke** mit dem Knopf „Weiterlesen“.
2. **Puzzle:** Gegenstände sortieren, bis jedes Brett nur eine Art enthält.
3. **Belohnung:** kurze Animation, Nachricht „Schön sortiert, Bianca!“. Etwa alle 2–3 Level wird ein Deko-Gegenstand freigeschaltet.
4. Zurück in die Leseecke: dekorieren oder weiterspielen.

## Puzzle-Regeln
- Regalbretter liegen **untereinander** (Hochformat). Gegenstände stehen nebeneinander, bewegt wird immer der **rechte äußere**.
- **Bedienung:** Brett antippen → Gegenstand hebt sich. Zielbrett antippen → Gegenstand wandert hinüber.
- Erlaubt, wenn das Zielbrett **leer** ist oder der rechte Gegenstand dort **dieselbe Art** hat und Platz frei ist.
- Jedes Brett fasst **4 Gegenstände**. Liegen mehrere gleiche Gegenstände rechts nebeneinander, wandern so viele mit, wie hinüberpassen.
- **Keine Uhr, kein Zuglimit.** Knöpfe „Rückgängig“ (unbegrenzt) und „Neu starten“.

## Gegenstandsarten
| Art | Ab Level |
|---|---|
| Buch rot | 1 |
| Topfpflanze | 1 |
| Teekanne | 1 |
| Buch grün | 4 |
| Kaktus | 11 |
| Buch blau | 21 |
| Teetasse | ggf. später |

Die genaue Reihenfolge der Freischaltung ist offen (siehe `offene-punkte.md`). Schon die ersten Level mischen Bücher, Pflanzen und Teekannen.

## Schwierigkeit
| Level | Arten | Bretter |
|---|---|---|
| 1–3 | 3 | 5 |
| 4–10 | 4 | 6 |
| 11–20 | 5 | 7 |
| ab 21 | 6 | 8 |

Immer 2 leere Bretter mehr als Arten. Level werden zufällig erzeugt und vor der Anzeige von einem Löser auf Lösbarkeit geprüft. Das Spiel ist damit endlos.

## Belohnung pro fertigem Brett
- **Pflanzen** bekommen kleine Blüten.
- **Teekannen** dampfen.
- **Bücher** rücken zusammen und leuchten kurz auf.

## Leseecke
- **5 feste Plätze:** Fensterbank (Pflanze), Tisch (Teekanne/Tasse), Sessel, Lampe, Regal-Deko.
- Jeder Platz hat **3–4 Varianten**, freigeschaltete Varianten wechseln per **Antippen**. Kein Drag & Drop.
- Insgesamt ca. 15–20 Freischaltungen, Motivation für ca. 40–50 Level.

## Grafik
- **Parametrisch erzeugte Inline-SVGs**, eine Generator-Funktion pro Art. Keine Emojis.
- Stil: flache Formen, feste warme Palette (Pastell, Holzbraun, Creme), eine Schattenkante und ein Glanzlicht pro Objekt.
- **Buch:** Rücken mit abgerundeten Ecken, Zierbänder. Parameter: Farbe, Höhe, Breite, Bandposition, Titelstreifen.
- **Topfpflanze:** Terrakotta-Topf, Blätter als gedrehte Bézier-Formen. Parameter: Blattanzahl, Winkel, Grünton.
- **Kaktus:** ovaler Körper, Arme, Stachel-Striche. Parameter: Armanzahl, Höhe, optionale Blüte.
- **Teekanne:** Körper, Tülle, Henkel, Deckelknauf. Parameter: Farbe, Muster (Punkte, Streifen, Blümchen).
- **Teetasse:** Tasse mit Untertasse, Parameter wie Teekanne.
- Arten unterscheiden sich vor allem über die **Silhouette**. Buchfarben zusätzlich über unterschiedliche Bandmuster (Farbschwäche).
- Dieselben Generatoren werden in der Leseecke und für die Animationen genutzt.

## Sound
- Synthetisiert mit der Web Audio API, keine Dateien.
- Weiches Holz-Klicken beim Bewegen, heller Glockenton bei fertigem Brett, kleiner Akkord bei gelöstem Level.
- Stummschalter.
- Bekannte Einschränkungen (nicht abschließend geprüft): Auf iOS startet Ton erst nach der ersten Berührung. Der Stummschalter am iPhone kann je nach iOS-Version auch Web Audio stumm schalten. Muss getestet werden.

## Technik
- Eine Datei `index.html`, Vanilla JS/CSS, keine Bibliotheken.
- Hochformat, Tippflächen ≥ 44 px.
- `localStorage` für Level, Freischaltungen und gewählte Deko.
- Offline lauffähig.

## Bewusst nicht in v1
Freies Platzieren von Deko, Gäste und Geschichten, gezeichnete Grafiken, Bestenlisten.

## Umsetzung in Häppchen
1. **Grafik-Musterblatt:** alle Gegenstände in mehreren Varianten, Stil mit Bastian abstimmen.
2. **Spielbares Puzzle** mit diesen Grafiken (Logik, Generator, Löser, Bedienung).
3. **Leseecke, Sound, Speichern, Feinschliff.**

## Aufwandsschätzung (grob, nicht belastbar)
| Schritt | Dauer |
|---|---|
| Puzzle-Logik, Generator, Löser | ca. 1 h |
| SVG-Generatoren | ca. 1–1,5 h |
| Bedienung und Layout | ca. 45 min |
| Leseecke, Sound, Speichern, Test | ca. 1–1,5 h |

Gesamt ca. 4–5 h. Größter Unsicherheitsfaktor ist die Abstimmung des Grafikstils.
