# Einen Loop bauen

Nutze diesen Ablauf, wenn der Nutzer einen neuen Loop entwerfen will. Gehe davon
aus, dass er mit Loops noch nicht vertraut ist.

## Das Design-Interview

Stell **eine kurze Frage nach der anderen** in Alltagssprache. Benutze in den
Fragen keine Fachbegriffe wie Auslöser, Erfolgs-Gate, Endzustand, Leitplanke oder
persistenter Zustand, außer der Nutzer fragt, was sie bedeuten.

Beginne mit:

1. „Was soll der Agent erledigen?"

Frage dann nur, was noch fehlt:

2. „Wann soll er laufen: wenn du fragst, nach einem Zeitplan, oder nachdem etwas
   passiert ist?"
3. „Worauf darf er schauen, was darf er ändern? Ist etwas tabu?"
4. „Woran erkennst du, dass es funktioniert hat?"
5. „Wann soll er stoppen oder dich um Hilfe bitten?"

Leite die kleinste wiederholbare Aktion, was er sich merken soll und die finale
Übergabe **aus den Antworten ab**, statt den Nutzer diese Teile entwerfen zu
lassen. Halte unbekannte Details generisch, statt sie auszufüllen. Hör auf zu
fragen, sobald weitere Details das Design nicht mehr materiell ändern würden.

## Den Feedback-Zyklus entwerfen

Bau den Loop um die sechs Schritte aus `SKILL.md`: Beobachten → Wählen → Handeln →
Prüfen → Festhalten → Wiederholen/Stoppen. Wende dabei diese Regeln an:

- Mach das Erfolgs-Gate **beobachtbar und reproduzierbar**. Ersetze „bis ich
  zufrieden bin" wo möglich durch eine Rubrik, Schwelle, einen Benchmark, eine
  Prüfer-Entscheidung oder eine endliche Szenario-Liste.
- Definiere die relevanten Endzustände: Erfolg, sauberer Leerlauf, blockiert,
  Freigabe nötig, erschöpft, stagniert. Melde einen Fehler oder ein erschöpftes
  Budget nie als Erfolg.
- Nimm ein vom Nutzer gesetztes Limit, wenn es eines gibt. Sonst nutze einen
  **No-Progress-Stopp** statt eine Zeit-, Iterations-, Kosten-, Versuchs- oder
  Umfangsgrenze zu erfinden. Nenne einen Eskalations-Verantwortlichen nur, wenn der
  Nutzer einen geliefert hat oder er aus dem Rahmen bekannt ist.
- Lies den aktuellen Zustand vor folgenreichen Aktionen neu. Liefere keinen
  veralteten Code, keine halben Artefakte, keine Annahmen aus einem früheren Durchgang.
- Bewahre unbeteiligte Arbeit. Verlange Freigabe für zerstörende, unumkehrbare,
  Produktions-, finanzielle, datenschutz-sensible oder externe Aktionen.
- **Trenne Arbeitssignal vom frischen Abnahme-Gate**, wenn du einen Prompt, ein
  Modell, ein Ranking oder ein Artefakt optimierst, das seine eigene Kennzahl
  überlisten könnte.
- Nutze **unabhängige Verifikation durch eine getrennte Instanz**, wenn derselbe
  Akteur nicht zugleich erzeugen und abnehmen sollte: zweiter Agent, andere
  Modellfamilie, eigene Session oder zumindest ein frischer Kontext. Beispiele aus
  dem Katalog sind der Builder/Reviewer-Loop, der Clodex-Review und die Multi-LLM-
  Konvergenz. Ohne getrennte Instanz: mechanischer Gegencheck (Fix zurücknehmen →
  wird der Test wieder rot?).
- Empfiehl einen **Einmal-Workflow** statt einen Loop zu fabrizieren, wenn keine
  neue Rückmeldung die nächste Aktion ändern kann.

## Die Prompt-Vorlage

Schreib den Loop in gewöhnlicher Sprache. Benenne den Auslöser, die frischen
Eingaben, die erlaubte Änderung, den Pflicht-Check und die Stopp-Bedingungen.
Diese Vorlage lässt sich kopieren und anpassen:

> Wenn [Auslöser], sieh dir [frische Eingaben] an. Wähle nach [Kriterien] eine
> Aktion im erlaubten Rahmen und führe die Änderung durch.
>
> Lass [Abnahme-Check] unter gleichen Bedingungen laufen. Halte fest, was sich
> geändert hat, den Beleg und den nächsten Schritt in [Zustandsdatei].
>
> Wiederhole nur, solange Fortschritt messbar ist und [Budget] bleibt. Stoppe,
> wenn [Erfolgs-Gate] erfüllt ist. Stoppe ohne Änderung, wenn [Leerlauf-Bedingung]
> zutrifft.
>
> Bitte um Freigabe oder melde einen Blocker, wenn [Eskalations-Bedingung]
> eintritt. Tu niemals [verbotene Aktion]. Schließe mit [Pull Request, Bericht,
> Artefakt oder Übergabe] ab.

Halte deinen Zustand für die Übergabe in `tmp/<datei>.md` fest: Ziel, erledigte
Schritte, Belege, Blocker, nächste Aktion. Speichere dort nie Geheimnisse.

## Wo der Loop läuft

Derselbe Loop-Prompt funktioniert über Werkzeuge hinweg; nur Speicherort und
Zeitplanung unterscheiden sich. Übersteigt die Taktung die Lebensdauer einer
Sitzung (z. B. wöchentlich oder nächtlich), nenn das passende Laufmodell — einen
geplanten Lauf (Routine, Cron, GitHub Action) statt eines Session-Loops — und
liefere den kopierfertigen Prompt trotzdem sofort. Laufmodell und Prompt sind zwei
unabhängige Entscheidungen; verzögere die Lieferung nicht wegen der Planung.

- **Claude Code** — In der Sitzung mit `/loop 5m <aufgabe>` pollen; stabile
  Projektregeln in `CLAUDE.md` (`/init`). Für Arbeit, die einen geschlossenen
  Terminal überdauert: Routine, Desktop-Task oder GitHub Action.
- **Cursor** — Im Agent den Loop-Prompt einfügen; wiederkehrende Hinweise in
  `.cursor/rules` oder `AGENTS.md`; geplante Läufe über Automations.
- **Codex** — Worktree-Thread für isolierte Code-Änderungen; Projektregeln in
  `AGENTS.md`; Prompt zuerst manuell testen, dann als Automation.

Lauf den Loop in jedem Fall **einmal von Hand**, bevor du ihn einplanst. Aktiviere
keinen Zeitplan und keine Produktionsänderung, ohne dass der Nutzer es will.

## Liefern und Preflight

Geh vor der Lieferung den Preflight aus `SKILL.md` durch und liefere im knappen
Standardformat (ein Satz + kopierfertiger Prompt). Zeig die innere Mechanik nur,
wenn der Nutzer das Detail will.
