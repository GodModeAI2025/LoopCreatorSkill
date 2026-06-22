# Validierungs-Ergebnisse

Der Skill wurde nach der skill-creator-Methode geprüft — die Prüfung lief in
**getrennten Instanzen**: Skill-Läufe und Blind-Judges auf unterschiedlichen
Modellfamilien, damit niemand seine eigene Arbeit abnimmt.

## Eval-Läufe (mit Skill vs. ohne Skill)

Jeder der drei Prompts aus `evals.json` wurde einmal **mit** dem Skill und einmal
**ohne** (Baseline) beantwortet; ein Blind-Judge verglich beide Antworten, ohne zu
wissen, welche welche war.

| Eval | Thema | Gewinner |
|---|---|---|
| 1 | Lohnt sich ein Loop fürs Repo-Aufräumen? (Identifizieren) | **mit Skill** |
| 2 | Loop, der die Doku aktuell hält (Bauen) | **mit Skill** |
| 3 | Endlos laufender, selbst-benotender Optimierer (Prüfen) | **mit Skill** |

Die Skill-Antworten folgten dem knappen Lieferformat (ein Satz + kopierfertiger
Prompt), benannten Endzustände, verlangten Freigabe vor irreversiblen Aktionen und
erfanden keine Tools/Limits. Die Baselines scheiterten genau dort: kein
kopierfertiger Prompt, erfundene Schwellenwerte/Dateinamen, teils Selbst-Aktivierung
des Loops ohne Freigabe.

## Triggering (Auslöse-Qualität der Beschreibung)

14 realistische Anfragen (8 sollten auslösen, 6 knappe Near-Misses sollten *nicht*),
je dreimal gegen die `description` getestet.

- **Genauigkeit: 100 %** — alle 8 Soll-Treffer lösten aus, alle 6 Near-Misses
  (Python-`for`-Schleife, Cronjob fürs Backup, RL-Wissensfrage, PR-Review, Vercel-
  Deploy, KPI-Dashboard) blieben korrekt stumm. Keine Fehlauslösung.

## Eingearbeitete Härtungen

Aus den Judge-Hinweisen übernommen (generalisierbar, nicht auf die Beispiele
überangepasst):

- Freigabe für irreversible Aktionen muss als eigene Zeile **im Prompt** stehen,
  nicht nur im Erklärsatz (`SKILL.md`).
- Übersteigt die Taktung die Sitzungsdauer, das Laufmodell (geplanter Lauf statt
  Session-Loop) benennen — aber den Prompt trotzdem sofort liefern (`bauen.md`).
- Loop-Doktor: keine erfundenen Schwellen/Limits/Pseudocode im reparierten Prompt;
  getrennte Prüf-Instanz ausdrücklich in den Prompt; knappes Format (`pruefen.md`).
