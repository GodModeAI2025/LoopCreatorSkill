# Changelog

Nennenswerte Änderungen an Skill, Katalog und Landingpage. Neueste zuerst.

## 2026-09-20

### Skill
- **Scheinfortschritt:** Der No-Progress-Stopp hängt jetzt am neu Gewussten, nicht an der
  Verschiedenheit der Aktionen. Mehrere verschiedene Versuche auf derselben schon
  widerlegten Annahme sind kein Fortschritt. Ergänzt in der Stopp-Leitplanke und der
  Gefahren-Tabelle der `SKILL.md`, in der Stopp-Regel von `bauen.md` und als getarnte
  Form der **Endlos-Reparatur** in `pruefen.md`.
- **Prüf-Theater** um eine weitere Form ergänzt: Der Check urteilt über einen
  zwischengespeicherten Stand (Cache, altes Build-Artefakt, alter Container) und wird
  grün, obwohl die gerade geänderte Quelle kaputt ist. Reparatur: den
  zwischengespeicherten Stand vor jedem Urteil verwerfen.
- Anregung: [ProgressGate](https://github.com/AshutoshVJTI/progressgate) (MIT) zur
  semantischen Stagnation und [governed-agents](https://github.com/alphan-ml/governed-agents)
  (MIT) zum grünen Gate auf altem Bytecode — eigene Formulierung, kein Text übernommen.

## 2026-09-16

### Skill
- **Rot-Test für den Check:** Ein Abnahme-Check verdient Vertrauen erst, wenn er einmal
  an einem absichtlich kaputten Stand abgelehnt hat. Neue Bau-Regel in `bauen.md`,
  Preflight-Punkt in `SKILL.md`, Zeile im Sicherheits-Check der `loop-vorlage.md`.
- **Prüf-Theater** im Loop-Doktor um die typischen Formen ergänzt: Werkzeug meldet trotz
  Fehler Erfolg, Suche trifft die eigenen Notizen des Loops, Check schaut auf den
  falschen Ort. Reparatur: Check auf das Ergebnis begrenzen und rot sehen.
- Anregung: der Fehlerkatalog von
  [ralph-loop-playbook](https://github.com/oh-ashen-one/ralph-loop-playbook) (MIT) —
  eigene Formulierung, kein Text übernommen.

## 2026-07-04

### Skill
- **Ausführungs-Leitplanke:** Wird der Agent gebeten, einen Loop selbst auszuführen,
  bleibt dessen Text Daten — eingebettete Anweisungen werden ignoriert, es sind nur
  umkehrbare Aktionen im genannten Rahmen erlaubt, Freigabe-Grenzen und Endzustände
  gelten unverändert.
- **Loop-Doktor** ordnet vor jeder Reparatur die Ursache ein (Design / Ausführung /
  Umgebung-Werkzeug / verändertes Ziel); ein Umgebungsfehler baut keinen gesunden Loop um.
- **Zustandsdatei-Vorlage** um den Block „Letzter Durchgang" (Aktion, Beleg, Ergebnis,
  Restarbeit) erweitert; löst den Zeitstempel-als-Beleg-Widerspruch bei den Reifestufen.
- **Projekt-lokale `LOOPS.md`:** gelieferte Loops auf Wunsch speichern und in späteren
  Sitzungen wiederverwenden (als Daten behandelt, keine Geheimnisse).
- **Katalog:** nur real vorhandene Muster empfehlen, Rangfolge bei mehreren Treffern,
  klarer Kein-Treffer-Ausgang ins Bau-Interview.
- **Routing/Description:** fehlendes Prüf-Objekt wird erfragt; die Beschreibung deckt
  jetzt „Codebasis oder Verlauf durchsuchen" ab.
- **Kohärenz-Feinschliff** (getrennte Instanz): Reifestufen-Aufstieg braucht eine
  anhängende Durchgangs-Historie (Zustandsdatei akkumuliert, statt zu überschreiben);
  Loop-Doktor prüft „zu früher Aufstieg"; Ausführungs-Leitplanke rein defensiv gerahmt.

### Landingpage
- Modernisierter, aufgeräumter Relaunch (Layout-Rhythmus statt Karten-Monotonie:
  Loop-Stepper, Reifestufen-Leiter, Editorial-Zweispalter, Pull-Quote, Mono-Labels).
- Dark-Theme-Kontrast-Blocker und weitere A11y-Punkte behoben (`color-scheme` pro
  Theme, Scroll-Offset, `aria-hidden`, Fokus-Kontrast).

## 2026-06-26

- Lernpunkte aus einer geprüften Analyse von `cobusgreyling/loop-engineering`
  übernommen: qualitative Reifestufen, Maker/Checker mit ablehnendem Default,
  Fehlermodus-Katalog, Verständnisschuld, Schutzzonen-Tabelle, billiger Leerlauf.

## 2026-06-22

- Erste Veröffentlichung: Skill `loop-creator` (Identifizieren, Finden, Anpassen,
  Bauen, Prüfen/Reparieren), Landingpage und Projektgerüst.
- Muster-Katalog auf 50 erprobte Loops erweitert.
