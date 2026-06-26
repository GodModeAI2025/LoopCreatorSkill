# LoopCreatorSkill

[![Lizenz: MIT](https://img.shields.io/badge/Lizenz-MIT-informational.svg)](LICENSE)

**Loop Engineering für KI-Agenten — erkennen, bauen, prüfen.**

`loop-creator` ist ein Skill, der hilft, aus einer Aufgabe einen **begrenzten,
prüfbaren Agenten-Loop** zu machen: einen Regelkreis aus Handeln, Messen, Behalten
oder Verwerfen — mit festem Prüfschritt und klarem Stopp. Die Stärke eines Loops
liegt nicht in maximaler Autonomie, sondern darin, dass er weiß, wann er fertig ist
oder einen Menschen fragen muss.

➡️ **Landingpage:** <https://godmodeai2025.github.io/LoopCreatorSkill/>

## Was der Skill kann

- **Identifizieren** — erkennen, ob sich aus wiederkehrender Arbeit überhaupt ein
  Loop lohnt (oder ob eine Einmal-Aufgabe besser passt).
- **Finden & Anpassen** — aus 50 erprobten Mustern das passende wählen und auf die
  eigenen Werkzeuge, Schwellen und Verantwortlichen umstellen.
- **Bauen** — über ein paar Fragen in Alltagssprache einen neuen, kopierfertigen
  Loop entwerfen.
- **Prüfen & Reparieren** — bestehende Loops als „Loop-Doktor" diagnostizieren:
  fehlende Bremse, Reward Hacking, Selbstabnahme, veralteter Zustand.

Ein Kernprinzip: Der **Prüfschritt gehört möglichst in eine getrennte Instanz** —
einen zweiten Agenten, eine andere Modellfamilie oder eine eigene Session. Wer baut,
sollte nicht zugleich abnehmen.

## Aufbau

```
skills/loop-creator/
├── SKILL.md                  # Kern: Routing, Feedback-Zyklus, Endzustände, Sicherheit
├── references/
│   ├── identifizieren.md     # Wann lohnt sich ein Loop? Discovery aus Code/Verlauf
│   ├── bauen.md              # Design-Interview, Prompt-Vorlage, wo der Loop läuft
│   ├── pruefen.md            # Loop-Doktor: Audit & Reparatur
│   └── beispiele.md          # 50 Loops als anpassbare Muster nach Kategorie
└── assets/
    ├── loop-vorlage.md       # Ausfüll-Vorlage für einen neuen Loop
    └── pruef-instanz.md      # Kopierfertiger Prüf-Prompt für eine getrennte Instanz
index.html                    # Landingpage (Loop Engineering erklärt)
evals/evals.json              # Beispiel-Testfälle für die Skill-Qualität
```

## Installation als Skill

Den Ordner `skills/loop-creator/` in das Skills-Verzeichnis des jeweiligen Agenten
legen (z. B. `~/.claude/skills/loop-creator/` für Claude Code). Der Skill wird über
seine Beschreibung automatisch ausgelöst, sobald es um das Bauen, Prüfen oder
Erkennen von Loops geht. In Claude Code lässt er sich auch mit `/loop-creator`
aufrufen.

Alternativ liegt das vorgepackte Paket [`loop-creator.skill`](loop-creator.skill)
(ZIP mit `SKILL.md` im Wurzelverzeichnis) zum Installieren bereit.

## Validierung

Der Skill wurde in getrennten Instanzen geprüft (Skill-Läufe und Blind-Judges auf
verschiedenen Modellfamilien): In allen drei Eval-Szenarien (Identifizieren, Bauen,
Prüfen) gewann die Skill-Variante gegen die Baseline, und das Auslösen der
Beschreibung lag bei 100 % (8/8 Treffer, 6/6 Near-Misses korrekt stumm). Details in
[`evals/ergebnisse.md`](evals/ergebnisse.md).

## Loop Engineering in einem Satz

> Erledige die begrenzte Aufgabe. Nach jeder Änderung führe den verfügbaren Check
> aus und behalte nur Verbesserungen. Stoppe bei Ziel, Limit oder ausbleibendem
> Fortschritt. Frag vor jeder freigabepflichtigen Aktion.

## Lizenz

MIT — siehe [LICENSE](LICENSE). © 2026 Mark Zimmermann.
