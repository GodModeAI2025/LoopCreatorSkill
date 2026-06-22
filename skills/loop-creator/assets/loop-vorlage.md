# Loop-Vorlage

Fülle diese Vorlage aus, um einen neuen Loop strukturiert zu entwerfen. Sie ist die
**interne Arbeitsfassung** — geliefert wird am Ende nur ein Satz Erklärung plus ein
kurzer, kopierfertiger Prompt (siehe unten). Lass jedes Feld weg, das die Aufgabe
nicht braucht; erfinde keine Werte, die du nicht aus dem Rahmen kennst.

## Steckbrief

- **Name:** [kurz und sprechend]
- **Ziel (ein Satz):** [das Ergebnis, messbar oder prüfbar formuliert]
- **Kategorie:** Engineering · Evaluation · Operations · Content · Design

## Der Regelkreis

- **Auslöser:** [wenn der Nutzer fragt · nach Zeitplan · nach einem Ereignis]
- **Beobachten:** [welcher frische Zustand, welche Belege werden gelesen]
- **Wählen:** [Kriterien für die wertvollste Aktion im erlaubten Rahmen]
- **Handeln:** [die eine begrenzte, umkehrbare Änderung pro Durchgang]
- **Prüfen:** [der feste Abnahme-Check unter gleichen Bedingungen — wer prüft?
  möglichst eine getrennte Instanz]
- **Festhalten:** [was wird in der Zustandsdatei `tmp/<datei>.md` gespeichert]

## Grenzen und Enden

- **Erfolgs-Gate:** [Schwelle, Benchmark, Rubrik, Prüfer-Entscheidung, Szenario-Set]
- **Stopp:** [vom Nutzer gesetztes Limit — sonst: No-Progress-Stopp]
- **Endzustände:** Erfolg · sauberer Leerlauf · blockiert · Freigabe nötig ·
  Budget erschöpft · kein Fortschritt
- **Freigabepflichtig:** [zerstörend · Produktion · Geld · Datenschutz · extern]
- **Verboten:** [was der Loop nie tun darf]
- **Übergabe:** [Pull Request · Bericht · Artefakt · Handoff an einen Menschen]

## Sicherheits-Check (vor dem Liefern)

- [ ] Eine frische Beobachtung kann die nächste Aktion ändern (sonst Einmal-Aufgabe).
- [ ] Prüfung ist reproduzierbar und — bei Overfitting-Gefahr — vom Auswahl-Signal
      getrennt.
- [ ] Prüfung läuft möglichst über eine getrennte Instanz (Agent / Modell / Session).
- [ ] Endzustände sind benannt; ein Fehler wird nie als Erfolg gemeldet.
- [ ] Folgenreiche Aktionen haben eine Freigabe-Grenze; fremde Arbeit bleibt erhalten.
- [ ] Keine erfundenen Tools, Limits, Metriken, Verantwortlichen, Berechtigungen.

## Lieferformat

```markdown
## [Loop-Name]

[Ein Satz: was der Loop tut und wann er stoppt.]

Prompt:
> [Ein kurzer, in sich geschlossener Absatz — gern unter 80 Wörtern.]
```
