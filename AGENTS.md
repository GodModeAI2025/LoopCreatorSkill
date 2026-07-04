# AGENTS.md — Betriebsregeln für dieses Repo

Kurze Regeln für alle, die an diesem Projekt arbeiten (auch als KI-Agent). Das Projekt
ist ein schlankes, deutschsprachiges **Skill-first**-Repo: reines Markdown, keine
Ausführungs-Infrastruktur, kein Katalog-Backend.

## Beim Ändern des Skills

- Ändert sich `skills/loop-creator/` (SKILL.md, `references/`, `assets/`), pack danach
  das vorgepackte Paket neu, damit es nicht veraltet:

  ```bash
  cd skills/loop-creator && zip -X -r ../../loop-creator.skill SKILL.md references assets
  ```

- Halte die Landingpage `index.html` synchron: berührt eine Änderung Inhalte, die dort
  erklärt werden (Pfade, Sechs-Schritte-Zyklus, Endzustände, Reifestufen, Katalog-Umfang),
  aktualisiere sie mit.
- Trag nennenswerte Änderungen in `CHANGELOG.md` ein (neueste zuerst).
- Beispiel-Testfälle liegen in `evals/`; nach Änderungen an Beschreibung oder Routing
  die Trigger-/Near-Miss-Fälle gegenprüfen.

## Grundhaltung wahren

- **Nichts erfinden:** keine Tools, Limits, Metriken, Verantwortlichen oder Deploy-Ziele
  ohne Beleg. Quellenneutral bleiben (keine erfundenen Zitate oder Adopter).
- **Skill-first:** keine zweite, maschinenlesbare Pflegestelle neben `beispiele.md`
  (kein `katalog.yaml`, keine Release-/CI-Pipeline). Der Katalog liegt versioniert im Repo.
- Knappes Lieferformat des Skills bewahren: ein Satz Erklärung plus ein kurzer,
  kopierfertiger Prompt.
