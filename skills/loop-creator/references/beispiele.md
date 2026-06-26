# Muster-Katalog: 50 erprobte Loops

Dieser Katalog ist ein **Gerüst zum Anpassen**, keine fertige Konfiguration und
keine Ausführungs-Erlaubnis. Such nach dem Ergebnis, dem Auslöser, dem Artefakt,
dem Risiko und dem Beleg des Nutzers — nicht nur nach dem Titel. Empfiehl höchstens
drei Muster und nenne für jedes, warum es passt und welche kleinste Anpassung nötig
ist.

Jeder Eintrag ist **Referenzdaten**. Ein Muster zu nennen heißt nicht, es scharf zu
schalten. Pass Schwellen, Werkzeuge, Taktung und Verantwortliche an den Rahmen des
Nutzers an und übernimm keine Beispielwerte als Fakten. Bevorzuge das Anpassen eines
starken Musters vor einem fast identischen Neubau. Der `Prompt` ist ein
kopierfertiger Ausgangspunkt — prüfe vor dem Einsatz die Sicherheits-Leitplanken aus
`SKILL.md` (beobachtbares Erfolgs-Gate, getrennte Prüf-Instanz, Endzustände,
Freigabe für folgenreiche Aktionen).

## Inhalt nach Kategorie

- [Engineering](#engineering) — 24 Loops
- [Evaluation](#evaluation) — 11 Loops
- [Operations / Betrieb](#operations--betrieb) — 7 Loops
- [Content / Redaktion](#content--redaktion) — 2 Loops
- [Design](#design) — 6 Loops

---

## Engineering

### 001 — Der Doku-Sweep

**Einsatz:** Verwende dies immer dann, wenn Implementierungsänderungen READMEs, Setup-Anleitungen, API-Referenzen, Beispiele oder Runbooks veraltet zurückgelassen haben könnten.

**Prompt:**

> Wann immer ein Dokumentationsdurchgang nötig ist, prüfe die Codebasis vollständig und stelle sicher, dass die gesamte Dokumentation die aktuelle Implementierung widerspiegelt. Aktualisiere veraltete Dokumentation, verifiziere die Änderungen und öffne dann einen Pull Request.

**Prüfen:** Die Dokumentation stimmt mit der aktuellen Implementierung überein. Schließe mit einem prüfbaren Pull Request ab.

**Schritte:**

1. Prüfe die Implementierungsänderungen seit dem letzten Dokumentationsdurchgang.
2. Vergleiche die Dokumentation des Repositorys mit dem Code, der Konfiguration, den Befehlen und dem Verhalten, die nun ausgeliefert werden.
3. Aktualisiere nur veraltetes Material, verifiziere dann Befehle, Links und Beispiele gegen das aktuelle Repository.
4. Führe die relevanten Prüfschritte aus und öffne einen Pull Request, der die Dokumentations-Drift und die Korrekturen erklärt.

**Warum:** Der Loop bindet die Dokumentation an die Implementierung, statt sich auf das Gedächtnis zu verlassen. Die Forderung nach einem Pull Request schafft ein sichtbares Diff, einen Prüfpunkt und einen dauerhaften Beleg dessen, was sich geändert hat.

### 002 — Der Architektur-Zufriedenheits-Loop

**Einsatz:** Verwende dies für ein bewusstes Architektur-Refactoring, bei dem sich das Ziel in konkreten Begriffen benennen lässt und das aktuelle System nach jeder bedeutsamen Änderung getestet werden kann.

**Prompt:**

> Refaktoriere, bis du mit der Architektur zufrieden bist. Teste nach jedem bedeutsamen Schritt das System live, führe Autoreview aus und committe. Verfolge den Fortschritt in `tmp/refactor-{projectname}.md`.

**Prüfen:** Die Architektur ist zufriedenstellend und die Prüfschritte bestehen. Live-Test, Autoreview und Commit bei jedem bedeutsamen Schritt.

**Schritte:**

1. Halte das Architekturziel, die Randbedingungen und die aktuellen Risiken fest, bevor du Code änderst.
2. Mache jeweils eine bedeutsame, prüfbare Änderung.
3. Teste das betroffene Verhalten live und führe nach jedem bedeutsamen Schritt eine unabhängige Prüfung durch.
4. Committe jeden verifizierten Checkpoint und aktualisiere die temporäre Fortschrittsdatei mit Entscheidungen, Blockern und der nächsten Aktion.

**Warum:** Kleine verifizierte Checkpoints senken das Refactoring-Risiko und bewahren Rollback-Punkte. Die Fortschrittsdatei hält Ziel und Entscheidungen über lange Sitzungen oder Übergaben hinweg verfügbar.

### 003 — Der Sub-50-ms-Seitenlade-Loop

**Einsatz:** Verwende dies, wenn ein Produkt eine definierte Menge an Routen, ein stabiles Performance-Harness und ein 50-ms-Ziel hat, das einer konkreten Metrik und Umgebung zugeordnet ist.

**Prompt:**

> Optimiere den Code weiter auf Geschwindigkeit. Miss nach jeder bedeutsamen Änderung die Seitenladeleistung über jede Seite unter denselben wiederholbaren Testbedingungen. Fahre fort, bis jede Seite in unter 50 ms lädt.

**Prüfen:** Jede Seite lädt in unter 50 ms. Verwende denselben Benchmark und bestätige, dass es keine Regressionen gibt.

**Schritte:**

1. Definiere die genaue Metrik, die Routen, die Testumgebung, das Aufwärmverhalten und die Anzahl der Benchmark-Durchläufe.
2. Erfasse eine Baseline für jede Zielseite, bevor du Änderungen vornimmst.
3. Nimm eine bedeutsame Optimierung vor, führe denselben Benchmark erneut aus und prüfe Regressionen über alle Routen.
4. Fahre fort, bis jede Seite den Schwellenwert unter den ursprünglichen Testbedingungen erreicht.

**Warum:** Das fixierte Harness verhindert, dass Performance-Arbeit zu anekdotischem Feintuning wird. Das Messen jeder Route nach jeder Änderung erkennt lokale Gewinne, die still und leise eine andere Seite verlangsamen.

### 004 — Der Produktionsfehler-Sweep

**Einsatz:** Verwende dies als geplanten Zuverlässigkeitsdurchgang, wenn ein Agent Produktionstelemetrie lesen, Fehler ins Repository zurückverfolgen, die relevanten Tests ausführen und eine prüfbare Korrektur vorbereiten kann.

**Prompt:**

> Prüfe unsere Produktionslogs auf Fehler. Wenn du ein behebbares Problem findest, verfolge es zu seiner Grundursache zurück, behebe es, verifiziere die Korrektur und öffne einen Pull Request. Wenn keine behebbaren Fehler vorhanden sind, stoppe, ohne Änderungen vorzunehmen.

**Prüfen:** Behebbare Produktionsfehler sind korrigiert und verifiziert. Schließe mit einem Pull Request ab oder stoppe, wenn keine behebbaren Fehler vorhanden sind.

**Schritte:**

1. Prüfe das vereinbarte Produktionslog-Zeitfenster und gruppiere wiederkehrende Symptome zu wahrscheinlichen Vorfällen.
2. Trenne behebbare Produktfehler von erwartbarem Rauschen, vorübergehenden Upstream-Ausfällen und bereits bekannten Problemen.
3. Verfolge jeden behebbaren Fehler zu einer Grundursache zurück, setze die kleinste angemessene Korrektur um und verifiziere sie mit gezielten Prüfschritten.
4. Öffne für jede verifizierte Korrektur einen Pull Request. Wenn die Logs sauber sind, stoppe, ohne Änderungen vorzunehmen.

**Warum:** Der Loop wandelt passive Log-Durchsicht in einen geschlossenen Zuverlässigkeits-Workflow um. Er fordert eine Grundursache, eine verifizierte Änderung und einen Prüf-Beleg, statt bei einer Liste von Fehlern stehenzubleiben.

### 005 — Der 100%-Testabdeckungs-Loop

**Einsatz:** Verwende dies, wenn 100% Abdeckung eine explizite Projektanforderung ist und das Repository einen vertrauenswürdigen Abdeckungsbefehl, klare Ausnahmen und eine wiederholt ausführbare Testsuite hat.

**Prompt:**

> Füge Tests hinzu, bis wir 100% Testabdeckung haben.

**Prüfen:** Die vollständige Testsuite besteht bei 100% Abdeckung. Verwende den Abdeckungsbericht des Projekts als maßgebliche Quelle.

**Schritte:**

1. Führe die vollständige Testsuite mit Abdeckung aus und sichere den Baseline-Bericht.
2. Priorisiere unabgedeckte Branches und Verhalten nach Risiko statt nach Dateireihenfolge.
3. Füge Tests hinzu, die aussagekräftige Ergebnisse, Fehlerpfade und Randbedingungen prüfen.
4. Wiederhole, bis die vollständige Suite besteht und der konfigurierte Abdeckungsbericht 100% erreicht.

**Warum:** Ein konkretes Abdeckungsziel gibt dem Agenten eine messbare Stoppbedingung und macht übersprungenen Code sichtbar. Die risikobasierte Reihenfolge hält die Arbeit auf das Verhalten fokussiert, das zählt.

### 007 — Der Logging-Coverage-Loop

**Einsatz:** Verwende dies, wenn wichtige Nutzerflüsse, Servicegrenzen, Hintergrundjobs oder Fehlerpfade schwer nachzuvollziehen sind, weil das Logging des Systems unvollständig oder inkonsistent ist.

**Prompt:**

> Überprüfe das Logging des Systems und ergänze fehlende Abdeckung, bis jeder wichtige Pfad nützliche, getestete Logs erzeugt.

**Prüfen:** Jeder wichtige Pfad gibt nützliche, getestete Logs aus. Repräsentative Erfolgs- und Fehlertests belegen die Abdeckung, ohne sensible Daten preiszugeben.

**Schritte:**

1. Inventarisiere die wichtigen Pfade und definiere das Ereignis, das Ergebnis, den Schweregrad, den Korrelationskontext und die Felder, die jeder ausgeben sollte.
2. Ergänze strukturierte Logs auf nicht abgedeckten Pfaden, ohne Ereignisse zu duplizieren oder geringwertiges Rauschen hinzuzufügen.
3. Füge Tests für erfolgreiche und fehlgeschlagene Ergebnisse hinzu und prüfe dann repräsentative ausgegebene Logs auf nützlichen Kontext.
4. Prüfe die Redaktion und wiederhole, bis jeder wichtige Pfad eine getestete Abdeckung oder einen dokumentierten Grund hat, nicht zu loggen.

**Warum:** Logging als testbare Abdeckung zu behandeln, verwandelt Observability von verstreuten Anweisungen in eine prüfbare Systemanforderung. Das Prüfen der ausgegebenen Ereignisse fängt Lücken ab, die eine reine Quellcode-Prüfung übersieht.

### 008 — Der nächtliche Changelog-Loop

**Einsatz:** Verwende dies, wenn sich ein Projekt häufig genug ändert, sodass nutzerseitige Release Notes von zusammengeführten Pull Requests, Commits, Deployments und Produktänderungen abweichen können.

**Prompt:**

> Überprüfe jede Nacht die Änderungen des Vortags und aktualisiere das Changelog um alles, was Nutzer wissen sollten.

**Prüfen:** Jede nutzerrelevante Änderung des Vortags ist berücksichtigt. Das Changelog ist aktualisiert und validiert, oder das Ergebnis ohne Änderung ist festgehalten.

**Schritte:**

1. Sammle die zusammengeführten Pull Requests, Commits, Deployments und sonstigen Änderungen des Vortags im Geltungsbereich.
2. Ermittle, welche Änderungen Nutzer betreffen, und vergleiche sie mit dem aktuellen Changelog.
3. Füge knappe, datierte Einträge mit nützlichen Verweisen hinzu, wobei vorhandene Inhalte erhalten und Duplikate vermieden werden.
4. Führe die relevanten Prüfschritte aus und halte entweder die validierte Aktualisierung fest oder die Tatsache, dass kein nutzerseitiger Eintrag nötig war.

**Warum:** Ein täglicher Abgleich macht Auslassungen sichtbar, solange der Kontext noch frisch ist. Die Beschränkung der Einträge auf das, was Nutzer wissen sollten, hält das Changelog nützlich, statt es in einen rohen Commit-Feed zu verwandeln.

### 011 — Der Testsuite-Tempo-Loop

**Einsatz:** Verwende dies, wenn langsame Tests die lokale Rückmeldung oder die Continuous Integration verzögern und das Projekt über stabile Befehle zur Messung von Laufzeit und Abdeckung verfügt.

**Prompt:**

> Optimiere die Testsuite so, dass sie so schnell wie möglich läuft, ohne die Abdeckung zu verringern oder das Verhalten zu verändern.

**Prüfen:** Die Suite ist schneller, ohne Regression bei Abdeckung oder Verhalten. Wiederholbare Zeitmessung, die vollständig bestandene Suite und der ursprüngliche Abdeckungsbericht belegen das Ergebnis.

**Schritte:**

1. Erfasse die Laufzeit der Gesamtsuite, die Abdeckung, die Umgebung, die Worker-Einstellungen und eine wiederholbare Methode zur Zeitmessung.
2. Profiliere die Suite, um teures Setup, redundante Arbeit, schlechte Isolation, unnötige Integrationspfade oder sichere Parallelisierungsmöglichkeiten zu finden.
3. Nimm jeweils eine Optimierung vor, lasse dann die gesamte Suite erneut laufen und vergleiche Zeitmessung, Abdeckung und Verhalten.
4. Stoppe beim vereinbarten Laufzeitziel oder bei der Regel sinkender Erträge, während alle ursprünglichen Prüfschritte weiterhin bestehen.

**Warum:** Eine feste Ausgangsbasis verhindert, dass Tempo-Arbeit unbemerkt Abdeckung oder Korrektheit eintauscht. Das Profiling lenkt den Aufwand auf gemessene Engpässe statt auf spekulative Neuschreibungen.

### 012 — Der Repository-Aufräum-Loop

**Einsatz:** Verwende dies, wenn aufgegebene Branches, alte Worktrees, unklare Pull Requests oder nicht gemergte Commits es erschweren zu erkennen, welcher Repository-Zustand noch von Bedeutung ist.

**Prompt:**

> Untersuche lokale und entfernte Branches, Pull Requests, Commits und Worktrees. Rette wertvolle Arbeit und räume alles Veraltete auf, bis das Repository aktuell und geordnet ist.

**Prüfen:** Wertvolle Arbeit ist gerettet und der verbleibende Repository-Zustand ist gewollt. Branches, Pull Requests, Commits und Worktrees sind aktuell, haben einen Eigentümer oder sind mit Beleg sicher entfernt.

**Schritte:**

1. Erfasse lokale und entfernte Branches, offene und kürzlich geschlossene Pull Requests, nicht gemergte Commits und registrierte Worktrees.
2. Klassifiziere jedes Element als aktuell, wertvoll aber unfertig, abgelöst, gemergt, aufgegeben oder unsicher und halte Beleg und Eigentümerschaft fest.
3. Rette wertvolle Änderungen in einen passenden aktuellen Branch, bevor du eine veraltete Referenz entfernst.
4. Räume nur nachweislich veralteten Zustand auf, führe Fetch und Prune sicher durch und wiederhole die Bestandsaufnahme, bis jedes verbleibende Element gewollt ist.

**Warum:** Bestandsaufnahme und Klassifizierung trennen rettbare Arbeit vom Ballast, bevor das Aufräumen beginnt. Das Wiederholen der Bestandsaufnahme belegt, dass das Repository geordnet und nicht bloß kleiner ist.

### 016 — Der Ticket-zu-PR-reif-Loop

**Einsatz:** Verwende dies, wenn ein echtes, aber lose formuliertes Ticket, ein Bugreport oder eine Kundenbeschwerde in eine abgegrenzte Engineering-Änderung mit genug Beleg für ein schnelles Review verwandelt werden soll.

**Prompt:**

> Nimm ein Ticket, einen Bugreport, ein fehlerhaftes Verhalten oder eine Kundenbeschwerde und verwandle es in einen reviewreifen Patch. Reproduziere den Fehler in der kleinsten repräsentativen Umgebung, weise die Grundursache nach, mache die kleinste glaubwürdige Korrektur und führe die ursprüngliche Reproduktion sowie relevante Regressionstests erneut aus. Wenn sich das Problem nach zwei ernsthaften Versuchen nicht reproduzieren lässt, sage das. Bündle keine unzusammenhängenden Refactorings in den Patch. Schließe ab mit der Ursache, den geänderten Dateien, dem Vorher-Nachher-Beleg, den Risiken und der Pull-Request-Zusammenfassung.

**Prüfen:** Der Fehler ist behoben, verifiziert und bereit zum Review. Das Problem reproduziert sich vor der Korrektur, reproduziert sich danach nicht mehr, und die relevanten Regressionsprüfungen bestehen.

**Schritte:**

1. Beschreibe das erwartete und das tatsächliche Verhalten und reproduziere dann den Fehler in der kleinsten repräsentativen Umgebung.
2. Verfolge das Verhalten bis zu einer Grundursache und bestätige den kausalen Zusammenhang mit Beleg.
3. Setze die kleinste glaubwürdige Korrektur um und vermeide unzusammenhängende Aufräumarbeiten oder versteckte Refactorings.
4. Wiederhole die ursprüngliche Reproduktion, führe relevante Regressionsprüfungen aus und bündle das Ergebnis für das Review.

**Warum:** Der Loop schließt die Lücke zwischen "etwas ist falsch" und dem Punkt, an dem ein Prüfer dem Patch vertrauen kann. Reproduktion, Beleg, abgegrenzter Umfang und eine strukturierte Übergabe nehmen dem Review die Detektivarbeit ab.

### 019 — Der Clodex-Adversarial-Review-Loop

**Einsatz:** Verwende Clodex, wenn Claude eine bedeutsame Codeänderung baut und Codex jede Korrekturrunde unabhängig prüfen soll.

**Prompt:**

> Führe /clodex [task] think hard --max-iter 5 --threshold medium aus. Claude plant die Aufgabe, setzt sie um, öffnet einen Pull Request, bittet Codex um ein Adversarial Review, behebt Befunde oberhalb der akzeptierten Schwere und wiederholt. Halte Branch, PR, Befunde, Verdikt und Iterationsstand fortsetzbar. Stoppe, wenn Codex freigibt, nur akzeptierte Befunde verbleiben, der Fortschritt stockt oder die Iterationsobergrenze erreicht ist. Beschreibe niemals einen mit Fehler abgebrochenen oder erschöpften Lauf als freigegeben. Schließe ab mit dem PR, den Prüfungen, dem Verdikt und den verbleibenden Befunden.

**Prüfen:** Der Pull Request erreicht die konfigurierte Prüfschwelle. Codex gibt ihn frei oder nur explizit akzeptierte Befunde verbleiben; Fehler, Stockungen und erschöpfte Grenzen werden als solche gemeldet.

**Schritte:**

1. Wähle die Aufgabe, das Denkniveau, die maximalen Iterationen und die höchste akzeptable Befundschwere.
2. Lass Claude über Clodex planen, umsetzen, verifizieren und den Pull Request öffnen.
3. Führe das Codex-Adversarial-Review aus, behebe blockierende Befunde, pushe und prüfe erneut.
4. Halte den Zustand über die Runden hinweg fest und schließe ab mit dem Verdikt, den verbleibenden Befunden, den Prüfungen und dem Pull-Request-Link.

**Warum:** Clodex trennt den Claude-Builder vom Codex-Prüfer und verwandelt das Review-Feedback in einen abgegrenzten Korrektur-Loop. Der festgehaltene Zustand hält die Arbeit fortsetzbar, ohne eine Unterbrechung als Freigabe zu behandeln.

### 020 — Der Loop-Harness-Verifikations-Loop

**Einsatz:** Verwende dies, wenn eine wiederkehrende Repository-Aufgabe unbeaufsichtigt laufen soll, eine Instanz aber dieselbe Ausgabe nicht erzeugen und freigeben darf.

**Prompt:**

> Nutze Loop Harness für geplante Repository-Arbeit wie CI-Triage, Issue-Pflege, Dependency-Updates oder Doku-Sync. Setze [Retry-Limit], starte dann einen isolierten Git-Worktree. Lass eine Claude-Session einen Patch oder eine Outbox-Nachricht vorbereiten (stagen) und eine zweite Claude-Session ihn gegen explizite Kriterien verifizieren. Liefere nur nach einem Bestehen aus; andernfalls sichere die Befunde und versuche nur innerhalb des Limits erneut. Schließe ab mit der Quell-Revision, der gestageten Ausgabe, dem Verifizierer-Ergebnis, dem Auslieferungsstatus und dem nächsten Lauf.

**Prüfen:** Nur unabhängig verifizierte Ausgabe wird ausgeliefert. Ein Bestehen durch eine zweite Instanz gibt die konfigurierte Ausgabe frei; eine fehlgeschlagene Verifikation sichert den Beleg und erzeugt keine externe Änderung.

**Schritte:**

1. Setze das Retry-Limit, wecke die fällige Loop-Harness-Aufgabe und erstelle einen isolierten Worktree aus der freigegebenen Quell-Revision.
2. Lass die primäre Claude-Session ein abgegrenztes Ergebnis stagen, ohne es zu veröffentlichen.
3. Lass eine zweite Claude-Session die gestagete Arbeit gegen explizite Abnahmekriterien prüfen.
4. Liefere bei einem Bestehen aus; andernfalls sichere die Befunde, veröffentliche nichts und versuche nur bis zum voreingestellten Limit erneut.

**Warum:** Die Workspace-Isolation begrenzt Interferenz, und das Zweit-Instanz-Gate trennt Erzeugung von Freigabe. Das Ergebnis kann wiederholt laufen, ohne sich auf das Vertrauen einer einzigen Session zu verlassen.

### 025 — Der Fresh-Clone-Loop

**Einsatz:** Nutze dies, um zu prüfen, ob die Onboarding-Anweisungen eines Repositorys in einer sauberen Umgebung ohne undokumentierte Hilfe funktionieren.

**Prompt:**

> Klone [Repository] in eine wegwerfbare Umgebung und folge nur dessen README bis zum dokumentierten Bereitschaftszustand, etwa dem Starten der App oder dem Bauen des Pakets. Wenn ein Schritt fehlschlägt oder fehlendes Wissen voraussetzt, halte die Lücke fest, behebe das Setup- oder Dokumentationsproblem, verwirf die Umgebung und beginne erneut. Übertrage keine Abhängigkeiten, Konfiguration, Anmeldedaten oder Reparaturen zwischen den Versuchen. Stoppe, wenn ein ununterbrochener Fresh Clone diesen Zustand erreicht, der Fortschritt stockt oder [Budget] endet. Gib die exakten Befehle, die geschlossenen Lücken und die verbleibenden Blocker zurück.

**Prüfen:** Eine saubere Umgebung erreicht den dokumentierten Bereitschaftszustand allein mit dem README. Der finale Lauf nutzt nur die Onboarding-Anleitung und benötigt keine ungenannte Abhängigkeit, Konfiguration oder manuelle Reparatur.

**Schritte:**

1. Erstelle eine wegwerfbare Umgebung ohne aus einem anderen Checkout übernommene Projekt-Abhängigkeiten oder Konfiguration.
2. Klone das Repository frisch und folge nur dem README, wobei du jeden fehlenden Schritt, jede versteckte Annahme und jeden Fehlschlag festhältst.
3. Behebe die kleinste Setup- oder Dokumentationslücke, verwirf die Umgebung vollständig und beginne erneut.
4. Wiederhole, bis ein sauberer Lauf den dokumentierten Bereitschaftszustand ohne Eingriff erreicht, und berichte dann die exakten Befehle und geschlossenen Lücken.

**Warum:** Die Umgebung nach jeder Reparatur zu zerstören, verhindert, dass lokaler Zustand das nächste Problem verbirgt. Der finale ununterbrochene Lauf ist ein direkter Beleg dafür, dass das README, nicht das Gedächtnis des Bedieners, ausreicht.

### 027 — Der Autonomy-Loop Builder-Reviewer-Loop

**Einsatz:** Verwende autonomy-loop, wenn ein Repository deterministische Test-, Build- und Lint-Prüfschritte hat und eine Aufgabe vorliegt, die sich für wiederholte Builder-Reviewer-Übergaben eignet.

**Prompt:**

> Verwende autonomy-loop für [Repository-Aufgabe], nachdem die Test-, Build- und Lint-Prüfschritte bestanden sind. Führe /autonomy-loop:autonomy-init aus, starte dann Builder und Reviewer in getrennten Worktrees. Der Builder liest LOOP-STATE.md, nimmt eine begrenzte Änderung vor und ergänzt einen Test, der vorher rot und nachher grün ist. Der Reviewer führt die Prüfschritte erneut aus und belegt den Test, indem er die Korrektur rückgängig macht oder mutiert. Akzeptiere nur, wenn beide bestehen; parke geschützte oder wiederholt fehlschlagende Arbeit für einen Menschen. Schließe ab mit dem Commit, den Prüfschritt-Belegen, dem Testbeleg, der Vertrauensstufe und den Risiken.

**Prüfen:** Jede akzeptierte Welle besteht den Proof-of-Test-Prüfschritt von autonomy-loop. Der neue Test schlägt ohne die Änderung fehl, besteht mit ihr, jeder konfigurierte Prüfschritt besteht, und geschützte Produktionsänderungen bleiben menschlich freigegeben.

**Schritte:**

1. Initialisiere autonomy-loop, konfiguriere deterministische Prüfschritte und geschützte Pfade und erstelle getrennte Builder- und Reviewer-Worktrees.
2. Lass den Builder LOOP-STATE.md lesen, eine begrenzte Änderung umsetzen, einen Test ergänzen, der vorher rot und nachher grün ist, und übergeben.
3. Lass den Reviewer jeden Prüfschritt erneut ausführen und mit Rückgängigmachen oder Mutieren belegen, dass der Test die Änderung erfasst.
4. Akzeptiere nur, wenn beide bestehen; andernfalls gib Befunde zurück oder parke die Welle für einen Menschen, wenn ein Schutzschalter auslöst.

**Warum:** Getrennte Worktrees und ein git-gestützter LOOP-STATE.md-Staffelstab halten die Rollen unabhängig und wiederaufnehmbar. Die Rückgängig-oder-Mutiere-Prüfung erfasst Tests, die Code ausführen, ohne die Korrektur zu belegen.

### 028 — Der Codex-Completion-Contract-Loop

**Einsatz:** Verwende dies für langlaufende Codex-Arbeit, Pull Requests, Laufzeitprüfungen oder nutzersichtbare Artefakte, bei denen ein plausibles Teilergebnis mit Fertigstellung verwechselt werden könnte.

**Prompt:**

> Führe $goal-planner-codex [Aufgabe] für langlaufende Codex-Arbeit aus, bei der Teilarbeit mit Fertigstellung verwechselt werden könnte. Einen PR zu landen und die Produktion zu verifizieren ist ein Beispiel. Definiere vor dem Handeln jedes erforderliche Ergebnis und seinen Beleg. Markiere nach jeder begrenzten Aktion die Anforderungen als belegt, schwach, fehlend oder widersprochen. Schließe das Goal nur ab, wenn alle belegt sind; andernfalls stoppe als blockiert, festgefahren oder erschöpft. Frage nach, bevor du Goal-State anlegst. Schließe ab mit der Anforderung-zu-Beleg-Tabelle, dem Status, dem Verantwortlichen und der nächsten Aktion.

**Prüfen:** Jede Codex-Goal-Anforderung hat einen aktuellen, ausreichenden Beleg. Das finale Audit enthält keinen schwachen, fehlenden oder widersprochenen erforderlichen Punkt; andernfalls bleibt die Arbeit offen, blockiert oder erschöpft.

**Schritte:**

1. Stelle für jede mehrdeutige Anforderung eine messbare Definition von Fertig wieder her.
2. Erfasse die Anforderungen, den Umfang, die Nicht-Ziele, den Belegplan und den aktuellen Status, ohne die angefragte Arbeit auszuweiten.
3. Führe eine begrenzte Aktion nach der anderen aus und hänge jeder betroffenen Anforderung einen aktuellen Beleg an.
4. Prüfe vor dem Abschluss jede Anforderung und bewahre ehrliche Zustände blockiert, erschöpft, festgefahren oder widersprochen.

**Warum:** Ein dauerhafter Completion Contract hält die Definition von Fertig über lange Sessions hinweg sichtbar. Jede Anforderung einem Beleg zuzuordnen macht falsche Fertigstellung leicht erkennbar.

### 030 — Der Fünf-Minuten-Repository-Maintainer-Loop

**Einsatz:** Verwende dies, wenn Codex Wartung über mehrere aktive Repositories koordinieren darf und parallele Arbeit steuerbar bleiben soll, ohne Threads zu duplizieren oder zu mikromanagen.

**Prompt:**

> Solange die Repository-Wartung aktiv ist, wache alle fünf Minuten auf. Triagiere [Repositories] und lies den jeweils neuesten Stand jedes Repository-Threads. Verwende einen Thread pro Repository wieder; weise dessen wertvollste begrenzte Aufgabe nur innerhalb der erteilten Berechtigungen zu und unterbrich keine zusammenhängende aktive Arbeit. Verlange Tests, Live-Beleg, Autoreview und grünes CI, bevor Arbeit landen kann. Eskaliere Produkt-, Zugriffs-, Sicherheits- oder unumkehrbare Entscheidungen. Erfasse bedeutsame Änderungen und stoppe, wenn jeder Punkt gelandet, entscheidungsreif, blockiert ist oder keine Arbeit hat.

**Prüfen:** Jeder Repository-Punkt erreicht eine belegte Übergabe oder einen Endzustand. Autorisierte autonome Arbeit landet mit Beleg; andere Punkte sind entscheidungsreif, mit einer exakten Anfrage blockiert oder als sauberer No-Op erfasst.

**Schritte:**

1. Definiere den Repository-Umfang, die Ausschlüsse und getrennte Berechtigungen für Triage, Delegation, Umsetzung, Push, CI-Reparatur, Merge und Release.
2. Aktualisiere alle fünf Minuten jede Repository-Warteschlange und lies den neuesten Stand des bestehenden Threads, bevor du den wertvollsten geeigneten Punkt wählst.
3. Verwende einen Thread pro Repository wieder, weise eine begrenzte Aufgabe zu und lass zusammenhängende aktive Arbeit weiterlaufen, sofern sie nicht blockiert, festgefahren, unsicher oder vom Kurs abgekommen ist.
4. Verlange Tests, Live-Beleg, Autoreview und grünes CI; erfasse den Beleg, leite dann den nächsten Punkt weiter oder lege dem Verantwortlichen eine exakte Entscheidung vor.

**Warum:** Ein Fünf-Minuten-Herzschlag hält die Steuerungsebene aktuell, ohne Polling in Mikromanagement zu verwandeln. Ein Thread pro Repository bewahrt den Kontext, während Beleg- und Autorisierungs-Prüfschritte autonomes Landen prüfbar machen.

### 031 — Der Sweep des jüngsten Feedbacks

**Einsatz:** Verwende dies nach mehreren Tagen Projekt-Feedback, wenn wiederkehrende Fehler auf ähnliche Probleme an anderer Stelle hindeuten könnten und der Agent sowohl den Konversationsverlauf als auch das vollständige aktuelle Projekt inspizieren kann.

**Prompt:**

> Sichte alle verfügbaren Threads aus [Rückblickfenster], in denen ich etwas an [Projekt] als fehlerhaft gemeldet und um eine Behebung gebeten habe. Erstelle eine deduplizierte Issue-Liste, gruppiere sie in Fehlermuster und prüfe den aktuellen Zustand. Auditiere das gesamte Projekt auf jedes Muster, behebe jede bestätigte Instanz und ergänze, wo praktikabel, Regressionsabdeckung. Wiederhole das vollständige Audit, bis es keine verbleibende Instanz mehr findet oder [Iterationsbudget] endet. Stoppe bei blockierter oder freigabepflichtiger Arbeit. Gib die Issues, Behebungen, Belege und Blocker zurück.

**Prüfen:** Das Issue-Inventar ist geschlossen und ein frisches Muster-Audit ist sauber. Jedes gemeldete Issue und jeder neu gefundene Treffer hat einen aktuellen Beleg der Behebung; blockierte, freigabepflichtige oder budgeterschöpfte Punkte bleiben ausdrücklich offen.

**Schritte:**

1. Lege das Rückblickfenster und die vollständige Projektoberfläche fest und sammle dann jeden zugänglichen Thread, in dem der Nutzer ein Problem gemeldet und eine Behebung verlangt hat.
2. Dedupliziere die gemeldeten Issues, prüfe ihren aktuellen Status und überführe die konkreten Beispiele in explizite Fehlermuster und Prüfschritte.
3. Auditiere jede projektinterne Oberfläche im Geltungsbereich auf jedes Muster, behebe eine bestätigte Instanz nach der anderen und ergänze, wo praktikabel, Regressionsabdeckung.
4. Führe nach jeder Behebung gezielte Prüfschritte durch und wiederhole dann das vollständige Muster-Audit sowie die relevanten vollständigen Prüfschritte, bevor du den Sweep für sauber erklärst.

**Warum:** Jüngste Korrekturen sind konkrete Beispiele für den Qualitätsmaßstab, den das Projekt verfehlt hat. Sie in Fehlermuster zu gruppieren verwandelt einmaliges Feedback in eine wiederverwendbare Audit-Rubrik, während ein frischer Komplett-Sweep verwandte Defekte aufdeckt und den aktuellen Projektzustand verifiziert, statt altem Thread-Zustand zu vertrauen.

### 033 — Der Propagations-Konsistenz-Loop

**Einsatz:** Verwende dies, nachdem du etwas geändert hast, das in mehreren Dateien vorkommt – etwa eine Versionsnummer, einen Feature-Namen, eine Anzahl, eine Regel, eine Einstellung oder einen Bezeichner – und jede Kopie konsistent bleiben muss.

**Prompt:**

> Nachdem du eine Version, Anzahl, Regel, einen Namen oder eine Konfiguration geändert hast, liste auf, wohin der neue Wert gehört, und aktualisiere ihn. Durchsuche das Projekt nach dem alten Wert und verwandten Formen. Sieh dir jeden Treffer an: behebe echte veraltete Werte, aber bewahre bewusste Historie, Beispiele, Migrationen oder Kompatibilitätsregeln. Wiederhole, bis null veraltete Werte verbleiben. Wenn einer über zwei Runden zurückkehrt, stoppe und identifiziere, was ihn möglicherweise neu erzeugt. Gib die Änderungen, die bewussten Treffer und die Suchausgabe zurück.

**Prüfen:** Keine unbeabsichtigte Kopie des alten Werts verbleibt. Die abschließenden Suchen finden nur Referenzen, die bewusst historisch sind oder für Beispiele, Migrationen oder Kompatibilität erforderlich sind, jeweils mit einer erfassten Begründung.

**Schritte:**

1. Liste die Dateien, Dokumentation, Einstellungen, generierten Ausgaben oder Betriebsnotizen auf, die voraussichtlich den geänderten Wert kopieren.
2. Aktualisiere die bekannten Kopien und durchsuche dann das gesamte Projekt nach dem alten Wert, der alten Schreibweise und anderen wahrscheinlichen Überbleibsel-Formen.
3. Entscheide für jeden Treffer, ob er wirklich veraltet ist oder bewusst bewahrte Historie, ein Beispiel, eine Migration oder eine Kompatibilitätsregel; behebe nur die veralteten Treffer.
4. Wiederhole dieselben Suchen, bis kein veralteter Treffer mehr verbleibt; kehrt einer über zwei Runden zurück, stoppe und identifiziere den Generator oder Prozess, der ihn wiederherstellt.

**Warum:** Die wiederholte Suche ist der entscheidende Teil: Sie fängt Kopien ab, die die erste Aktualisierung übersehen hat. Jeden Treffer zu prüfen verhindert außerdem, dass eine breite Ersetzung historische Notizen, Migrationscode oder Beispiele beschädigt, die den alten Wert absichtlich zeigen.

### 035 — Der Goal-Forge-Loop

**Einsatz:** Verwende dies, wenn eine grobe Coding-Idee zu vage ist, um sie Codex für einen langen autonomen Lauf zu übergeben, und der Nutzer zuerst Geltungsbereich, Abschlussprüfungen, Sicherheitsgrenzen und benötigte Tools festlegen muss.

**Prompt:**

> Verwandle [grobe Coding-Idee] in zwei Planungsdateien, bevor Codex /goal startet, seinen Modus für langlaufende Aufgaben. Befrage den Nutzer und schreibe dann SPEC.md: was zu bauen, auszuschließen und zu bedenken ist, plus messbare done_when-Abschlussprüfungen. Schreibe GOAL.md: den Arbeitsplan, eine Fortschritts-Scorecard, schnelle und finale Prüfungen, Memory-Dateien, Belege und Freigabegrenzen. Wenn eine wichtige Entscheidung, Berechtigung, ein Tool, eine Umgebungsanforderung oder ein Test fehlt, stoppe als nicht bereit. Beginne die Umsetzung nicht ohne Freigabe.

**Prüfen:** Die Planungsdateien sagen, was zu bauen ist, wie es zu bewerten ist und wann zu stoppen ist. Jede done_when-Abschlussprüfung benennt beobachtbare Belege, die schnellen und finalen Prüfungen sind tatsächlich ausführbar, die Umgebung ist bereit, und ungelöste Entscheidungen sind klar als nicht bereit markiert.

**Schritte:**

1. Frage den Nutzer, was das fertige Feature tun soll, was außerhalb des Geltungsbereichs liegt, welche Randfälle wichtig sind, was schiefgehen könnte und welcher Beleg den Abschluss nachweisen würde; halte diese Entscheidungen in SPEC.md fest.
2. Weise auf mehrdeutige Anforderungen mit konkreten Interpretationen hin und lass den Nutzer Produktentscheidungen lösen, statt den Coding-Agenten still wählen zu lassen.
3. Schreibe GOAL.md mit der geordneten Arbeit, einer Fortschritts-Scorecard, schnellen Prüfungen für jede Iteration, langsameren finalen Prüfungen, Memory-Dateien für lange Läufe, Freigabegrenzen und den erforderlichen Belegen.
4. Bestätige, dass die Tools, Berechtigungen, Umgebung und Tests vorhanden sind; stoppe als nicht bereit, wenn etwas Wesentliches fehlt, und starte die langlaufende Aufgabe erst nach Freigabe.

**Warum:** Goal Forge lässt den Nutzer entscheiden, was Erfolg bedeutet, bevor ein Agent stundenlang programmiert. Die zwei Dateien geben Codex ein stabiles Ziel, wiederholbare Prüfungen, Memory über einen langen Lauf hinweg und einen ehrlichen Nicht-bereit-Zustand, wenn wichtige Informationen fehlen.

### 037 — Der Kaltstart-Trimmer-Loop

**Einsatz:** Setze dies ein, wenn sich eine Web-App beim ersten Besuch schwerfaellig anfuehlt, weil sie zu viel Code, Styling, Medien oder andere Daten herunterlaedt, bevor der erste Bildschirm erscheint.

**Prompt:**

> Reduziere die Daten, die [Web-App] herunterlaedt, bevor ihr erster Bildschirm erscheint. Erfasse zunaechst bestehende Tests im gruenen Zustand, Mobil- und Desktop-Screenshots sowie komprimierte uebertragene Bytes - die tatsaechlich heruntergeladenen Daten. Nutze den Build-Report nur, um Kandidaten vorzuschlagen. Verschiebe, komprimiere oder entferne ein Element, baue dann neu und fuehre jeden Pruefschritt erneut aus. Behalte es nur, wenn die Tests bestehen, die Screenshots pixelidentisch sind und die Bytes sinken; andernfalls setze zurueck. Stoppe, wenn kein sicherer Kandidat mehr bleibt, der Fortschritt stockt oder eine Freigabe noetig ist. Gib Messwerte, Aenderungen und ungetestete Zustaende zurueck.

**Prüfen:** Der erste Bildschirm laedt weniger Daten herunter, ohne dass sich ein getestetes Verhalten oder ein Pixel aendert. Dieselbe produktionsnahe Messung meldet weniger heruntergeladene Bytes, die bestehenden Tests bestehen, jeder repraesentative Screenshot ist pixelidentisch, und das unsichere Entfernen von Abhaengigkeiten bleibt freigabepflichtig.

**Schritte:**

1. Erfasse vor jeder Code-Aenderung bestehende Tests im gruenen Zustand, repraesentative Mobil- und Desktop-Screenshots des ersten Bildschirms sowie einen wiederholbaren Ausgangswert fuer komprimierte uebertragene Bytes - die tatsaechlich heruntergeladene Menge.
2. Nutze einen Build- oder Bundle-Report, um grosse oder fruehe Downloads zu finden, und waehle dann einen sicheren Kandidaten aus, um ihn bis zum Bedarf zu verzoegern, zu komprimieren, inline einzubinden oder zu entfernen.
3. Baue neu und fuehre dieselben Tests, Screenshots und Download-Messungen erneut aus; behalte die Aenderung nur, wenn jeder Pruefschritt besteht und die Bytes sinken, andernfalls setze sie vollstaendig zurueck.
4. Wiederhole, bis kein sicherer Kandidat mehr bleibt, mehrere Versuche keine Verbesserung bringen, die Messung unzuverlaessig ist oder die naechste Aenderung eine Freigabe braucht.

**Warum:** Verhalten und Screenshots vor der ersten Aenderung festzuhalten verhindert, dass ein kaputter Bildschirm zum neuen Normalzustand wird. Eine Download-Aenderung pro Runde macht ausserdem klar, welche Bearbeitung Bytes gespart hat, und macht einen fehlgeschlagenen Versuch leicht rueckgaengig.

### 041 — Der Hausmeister-Loop

**Einsatz:** Setze dies ein, wenn sich in einem Code-Projekt kleine Wartungsprobleme angesammelt haben - ungenutzter Code, veraltete Dateien, doppelte Logik, kaputte Links, alte Kommentare, inkonsistente Namen oder verwirrende Organisation -, breites Löschen aber riskant wäre.

**Prompt:**

> Prüfe [Repository oder Code-Projekt] auf toten Code, also nicht erreichbaren oder ungenutzten Code; veraltete Dateien oder Kommentare; ungenutzte Abhängigkeiten; Duplikation; kaputte Links; inkonsistente Namen; und verwirrende Struktur. Schütze unbeteiligte, aktive, nicht committete, generierte und unsichere Arbeit. Belege eine risikoarme Bereinigung, nimm die kleinste in sich stimmige Änderung vor, und führe dann Build, Tests, Laufzeitprüfungen und Diff-Review erneut aus. Behalte nur verifizierte Verbesserungen. Stoppe, wenn keine mehr verbleibt, der Fortschritt stagniert, eine Verifikation nicht verfügbar ist oder eine Freigabe erforderlich ist. Gib Änderungen, Belege und zurückgestellte Kandidaten zurück.

**Prüfen:** Keine bestätigte risikoarme Bereinigung verbleibt, und das bestehende Verhalten besteht weiterhin. Jede beibehaltene Bereinigung ist durch direkten Beleg gestützt, relevante Builds und Tests bestehen, die Anwendung läuft weiterhin, wo zutreffend, unbeteiligte Arbeit bleibt unberührt, und unsichere Kandidaten werden zurückgestellt statt gelöscht.

**Schritte:**

1. Inspiziere den aktuellen Zustand des Code-Projekts und identifiziere aktive Branches, nicht committete Bearbeitungen, generierte Dateien, Konfiguration und andere Arbeit, die nicht gestört werden darf.
2. Sammle mögliche Bereinigungen und belege dann anhand von Code-Referenzen, Konfiguration, Dokumentation, Tests oder Laufzeitverhalten, dass ein Kandidat tatsächlich risikoarm ist.
3. Nimm die kleinste nützliche Änderung vor und führe den bestehenden Build, die Tests, Anwendungsprüfungen und den Diff-Review aus; behalte sie nur, wenn das Verhalten intakt bleibt und sich keine unbeteiligte Arbeit ändert.
4. Wiederhole, bis keine bestätigte risikoarme Bereinigung mehr verbleibt, der Fortschritt stagniert, eine Verifikation nicht verfügbar ist oder der nächste Kandidat eine Freigabe benötigt.

**Warum:** Eine belegte Bereinigung nach der anderen hält die Arbeit leicht prüfbar und rückgängig zu machen. Vor dem Löschen einen Beleg zu fordern - und unsichere Dateien und Bearbeitungen zu schützen - verhindert, dass ein Aufräum-Durchlauf Code entfernt, der aktiv, aber schlecht verstanden ist.

### 043 — Der Neues-Projekt-vorbereiten-Loop

**Einsatz:** Setze dies vor dem Bau eines neuen Softwareprojekts ein, wenn seine Idee oder frühen Dokumente noch wichtige Implementierungsentscheidungen offen für Interpretation lassen.

**Prompt:**

> Bereite [Projekt] für die Implementierung vor. Stelle sicher, dass seine Dokumente Anforderungen, technisches Design, Aufgaben mit Akzeptanzkriterien und Teststrategie abdecken. Behebe in jeder Runde die größte Lücke oder den größten Widerspruch, der dazu führen könnte, dass zwei kompetente Ingenieure unterschiedliche Systeme bauen. Halte Details nachvollziehbar, halte Annahmen fest, und frage nach, bevor Produktentscheidungen sich verzweigen. Prüfe die Konsistenz erneut und lasse dann zwei unabhängige Prüfer die Komponenten, das Datenmodell, die Abhängigkeiten und die Definition of Done beschreiben. Stoppe, wenn sie substanziell übereinstimmen und jedes Artefakt testbar ist, oder eine Entscheidung den Nutzer braucht.

**Prüfen:** Zwei unabhängige Prüfer leiten aus den Projektdokumenten im Wesentlichen denselben Bau ab. Ihre Beschreibungen stimmen bei den Komponenten, dem Datenmodell, den Abhängigkeiten und der Definition of Done überein, und jedes erforderliche Artefakt ist konkret, konsistent, nachvollziehbar und testbar.

**Schritte:**

1. Inventarisiere die aktuellen Projektdokumente und identifiziere die fehlenden Anforderungen, das technische Design, die Aufgabenaufgliederung, die Akzeptanzkriterien oder die Teststrategie, die vor der Implementierung nötig sind.
2. Finde die einzelne größte Lücke, den Widerspruch oder die vage Anforderung, die kompetente Ingenieure dazu bringen könnte, unterschiedliche Systeme zu bauen, und schließe sie dann mit konkretem Detail, das auf eine festgehaltene Anforderung zurückführbar ist.
3. Halte Annahmen fest, die sich sicher treffen lassen, frage den Nutzer bei echten Produktverzweigungen, und prüfe jedes bearbeitete Dokument erneut gegen die anderen auf Konsistenz.
4. Lasse zwei unabhängige Prüfer die beabsichtigten Komponenten, das Datenmodell, die Abhängigkeiten und die Definition of Done beschreiben; wiederhole, bis ihre Beschreibungen substanziell übereinstimmen oder eine erforderliche Entscheidung den Fortschritt blockiert.

**Warum:** Ein konkreter Konvergenztest legt Mehrdeutigkeit offen, über die ein einzelner Autor hinweglesen kann. Eine Divergenz nach der anderen zu beheben hält die Dokumente kohärent und macht aus der Projektvorbereitung einen Beleg, dem ein anderer Ingenieur folgen kann, statt eines Stapels Planungstext.

### 044 — Der Test-Stabilisierer-Loop

**Einsatz:** Setze dies ein, wenn eine Test-Suite über ansonsten vergleichbare Durchläufe hinweg inkonsistente Ergebnisse liefert und die Fehlschläge aus gemeinsamem Zustand, Timing, Reihenfolge oder externen Abhängigkeiten stammen könnten.

**Prompt:**

> Führe [Test-Suite] [N] Mal unter denselben Bedingungen aus und liste Tests auf, deren Ergebnis sich ändert. Behebe die häufigste Flake an ihrer Wurzelursache - gemeinsamer Zustand, Timing, Reihenfolge oder eine externe Abhängigkeit - niemals mit einem blinden Sleep oder Retry. Führe diesen Test [N] Mal aus, dann führe die vollständige Suite erneut aus. Wiederhole, bis [N] aufeinanderfolgende Durchläufe der vollständigen Suite bestehen, der Fortschritt stagniert oder eine Freigabe erforderlich ist. Gib jede Flake, Wurzelursache, Behebung, Beleg und begründete Quarantäne zurück.

**Prüfen:** Die vollständige Test-Suite besteht für die erforderliche Folge aufeinanderfolgender Durchläufe. Der reparierte Test besteht wiederholt, [N] aufeinanderfolgende Durchläufe der vollständigen Suite sind grün unter den erfassten Bedingungen, und kein blinder Sleep oder Retry verbirgt eine ungelöste Ursache.

**Schritte:**

1. Wähle die Test-Suite, die erforderliche Durchlaufanzahl und die Bedingungen, die fest bleiben müssen, führe dann die vollständige Suite wiederholt aus und erfasse jeden inkonsistenten Test.
2. Wähle die häufigste Flake aus, reproduziere sie so eng wie praktikabel, und identifiziere die zugrunde liegende Ursache aus gemeinsamem Zustand, Timing, Reihenfolge oder Abhängigkeit.
3. Behebe den Test oder den Produktcode, ohne einen blinden Sleep oder Retry hinzuzufügen, führe dann den betroffenen Test wiederholt aus, bevor du zur vollständigen Suite zurückkehrst.
4. Wiederhole, bis die erforderliche Anzahl aufeinanderfolgender Durchläufe der vollständigen Suite besteht, der Fortschritt stagniert oder eine Freigabe nötig ist, und berichte jede Wurzelursache, Behebung, Quarantäne und jeden verbleibenden Blocker.

**Warum:** Wiederholte Durchläufe verwandeln sporadische Fehlschläge in messbaren Beleg. Die häufigste Flake zuerst zu reparieren und eine Folge über die vollständige Suite zu fordern verhindert, dass eine lokale Behebung eine andere Quelle der Instabilität verbirgt.

### 048 — Die Groundtruth-Schleife

**Einsatz:** Setze dies ein, bevor du auf die Sicherheit, Korrektheit, Plattformkompatibilität, privilegierten Flächen, geplanten Aufgaben oder operativen Annahmen eines Projekts vertraust, und wenn die erste Aufgabe das Auditieren statt das Reparieren ist.

**Prompt:**

> Auditiere [Projekt] aus seinem tatsächlichen Code und seiner Konfiguration, nicht aus Framework-Annahmen. Erfasse für Architektur, Plattformkompatibilität, Sicherheit, privilegierte Bereiche, Performance, Deployment, Jobs, Geschäftslogik und Codequalität jeweils belegt, kein Problem, schwach oder N/A mit direktem Beleg; verifiziere externe Grenzen anhand aktueller Primärquellen und berechne Zahlen. Frage nach, bevor du Code änderst. Stoppe, wenn jeder Bereich mit Schweregrad erfasst ist, oder gib nicht verifizierte Bereiche als blockiert zurück. Schließe mit einer allgemeinverständlichen Übersicht und einer Bereich-zu-Beleg-Tabelle ab.

**Prüfen:** Jeder Audit-Bereich hat ein aktuelles, belegbasiertes Ergebnis und einen Schweregrad. Die Bereich-zu-Beleg-Tabelle enthält keine stillen Lücken: Jeder Bereich ist belegt, kein Problem gefunden, schwach, N/A mit Begründung oder ausdrücklich nicht verifiziert und blockiert.

**Schritte:**

1. Ermittle die tatsächliche Sprache, das Framework, die Hosting-Plattform, die privilegierten Flächen, die geplanten Jobs und die Deployment-Konfiguration aus dem abgegrenzten Projekt selbst.
2. Untersuche jeden geforderten Bereich, knüpfe die Schlussfolgerungen an Code oder Konfiguration, verifiziere Plattform- und Bibliotheksverhalten anhand aktueller Primärquellen und berechne quantitative Aussagen, statt sie zu schätzen.
3. Halte für jeden Bereich ein Ergebnis, einen Beleg und einen Schweregrad fest und trenne bestätigte Schwächen von Kein-Problem-Befunden, begründeten N/A-Ergebnissen und nicht verifizierten Lücken.
4. Liefere die allgemeinverständliche Projektübersicht und die Bereich-zu-Beleg-Tabelle, ohne Code zu ändern; stoppe nur dann als vollständig, wenn jeder Bereich berücksichtigt ist, andernfalls gib die blockierten Lücken zurück.

**Warum:** Breite Audits scheitern, wenn sie Framework-Standards übernehmen, sich auf erinnerte Grenzen verlassen oder stille Bereiche auslassen. Eine feste Beleg-Tabelle zwingt die prüfende Person, jede Fläche zu belegen, zu entlasten, auszuschließen oder ausdrücklich zu blockieren.


## Evaluation

### 009 — Der Qualitäts-Serien-Loop

**Einsatz:** Verwende dies, wenn die Produktqualität eine strenge Hürde aufeinanderfolgender Erfolge benötigt und Fehler die Test- und Benchmark-Suite dauerhaft verbessern sollen.

**Prompt:**

> Teste realistische Szenarien. Wenn eines fehlschlägt, dokumentiere es, ergänze Regressions- und Benchmark-Abdeckung, behebe es und starte die Serie neu. Stoppe nach [N] erfolgreichen Fällen in Folge.

**Prüfen:** Die letzten [N] realistischen Fälle bestehen in Folge. Jeder frühere Fehler ist dokumentiert, behoben und durch Regressions- und Benchmark-Abdeckung geschützt.

**Schritte:**

1. Definiere realistische Szenarien, die Qualitätshürde, den Wert von [N] und den für ein Bestehen erforderlichen Beleg.
2. Führe die Fälle einzeln unter konsistenten Bedingungen aus und bewahre das Ergebnis zur Prüfung auf.
3. Tritt ein Fehler auf: Dokumentiere ihn, ergänze Regressions- und Benchmark-Abdeckung, behebe die Ursache, verifiziere die Behebung und setze die Serie auf null zurück.
4. Stoppe erst, nachdem [N] aufeinanderfolgende Fälle die ursprüngliche Qualitätshürde erfüllen.

**Warum:** Das Neustarten der Serie verhindert, dass isolierte Erfolge sporadische Schwächen verbergen. Jeden Fehler in dauerhafte Abdeckung umzuwandeln, macht die Evaluation nach jedem Fehlschlag stärker.

### 010 — Der vollständige Produktevaluations-Loop

**Einsatz:** Verwende dies für einen erschöpfenden End-to-End-QA-Durchlauf einer Anwendung, wenn eine produktionsnahe lokale Umgebung und die vollständige Abdeckung aller interaktiven Oberflächen wichtiger sind als eine enge Regression oder eine Stichprobe der wichtigsten Funktionen.

**Prompt:**

> Erstelle bereinigte, produktionsskalige lokale Daten unter produktionsnahen Einstellungen. Inventarisiere jede nutzerseitige Funktion, Rolle, Route, Schaltfläche, Eingabe, jedes Modal, jeden Zustand und jeden Workflow; definiere für jedes dokumentierte Akzeptanzkriterien und endliche risikobasierte Randfälle. Teste als echter Nutzer und protokolliere jeden Bug mit reproduzierbarem Beleg. Prüfe die Befunde auf gemeinsame Ursachen und Abhängigkeiten; implementiere kohärente Behebungen mit Regressionstests und führe dann das vollständige Inventar erneut aus. Stoppe bei einem sauberen Durchlauf oder einer blockierten Übergabe. Frage nach, bevor du in Produktion gehst, sensible Daten verwendest oder destruktive Aktionen durchführst.

**Prüfen:** Jede inventarisierte Produktoberfläche erfüllt ihre dokumentierten Akzeptanzkriterien. Der abschließende vollständige Regressionslauf deckt jede inventarisierte Oberfläche und ihre endlichen risikobasierten Randfälle in der produktionsnahen lokalen Umgebung ab, wobei jeder reproduzierbare Bug behoben und durch einen Beleg gestützt ist.

**Schritte:**

1. Erstelle einen bereinigten oder synthetischen produktionsskaligen lokalen Datensatz, spiegle sichere Produktionseinstellungen und halte unvermeidbare Unterschiede fest.
2. Inventarisiere jede nutzerseitige Funktion, Rolle, Route, jedes Bedienelement, jeden Zustand und jeden Workflow; definiere für jedes Element dokumentierte Akzeptanzkriterien und eine endliche risikobasierte Randfall-Menge.
3. Übe jedes Inventarelement als echter Nutzer unter seinen normalen und definierten Randfallbedingungen aus und protokolliere jeden Bug sofort mit reproduzierbarem Beleg.
4. Prüfe die vollständige Bug-Menge auf gemeinsame Ursachen, Abhängigkeiten und widersprüchliche Behebungen und implementiere dann die kleinste kohärente Lösung mit Regressionsabdeckung.
5. Führe die betroffenen Pfade und das vollständige Inventar erneut aus; stoppe nur bei einem sauberen vollständigen Durchlauf oder einer ausdrücklich blockierten Übergabe.

**Warum:** Ein endliches Oberflächen-Inventar verhindert, dass wichtige Bedienelemente und Zustände hinter einigen wenigen Happy-Path-Szenarien verschwinden. Alle Befunde vor der Behebung zu prüfen, deckt gemeinsame Ursachen und Wechselwirkungen auf, während der abschließende vollständige Lauf Änderungen abfängt, die einen Pfad reparieren, aber einen anderen schwächen.

### 023 — Der selbstverbessernde Champion-Loop

**Einsatz:** Nutze dies, um einen Prompt, eine Policy oder eine Konfiguration zu justieren, wenn günstiges Iterieren nützlich ist, die finale Abnahme aber frische Beispiele verwenden muss.

**Prompt:**

> Verbessere einen Prompt, eine Policy oder eine Konfiguration. Der System-Prompt eines Support-Assistenten ist ein Beispiel. Speichere den Champion, seine Bewertung, ein Arbeitsset, unberührte Holdout-Fälle, Muss-bestehen-Prüfungen und [Budget]. Ändere pro Runde eine Sache auf Basis eines aufgezeichneten Fehlschlags. Befördere den Herausforderer nur, wenn er den Champion auf den Holdouts um [Marge] schlägt, ohne eine Muss-bestehen-Prüfung zu schwächen; behalte andernfalls den Champion. Stoppe beim Ziel, bei der Budget-Grenze oder bei fehlendem Fortschritt. Gib den Gewinner, die Bewertungen, das Experiment-Log und die verbleibenden Fehlschläge zurück.

**Prüfen:** Der beste auf Holdouts geprüfte Champion wird zurückgegeben. Jeder Herausforderer ist protokolliert, und angenommene Änderungen schlagen den vorherigen Champion auf unberührten Fällen, ohne eine Muss-bestehen-Prüfung zu schwächen.

**Schritte:**

1. Speichere den aktuellen Champion, das Arbeitsset, die unberührten Holdout-Fälle, die Muss-bestehen-Prüfungen, die Verbesserungsmarge, das Budget und das Experiment-Log.
2. Nutze einen aufgezeichneten Fehlschlag, um einen gezielten Herausforderer vorzuschlagen, und teste ihn am Arbeitsset.
3. Friere vielversprechende Herausforderer ein und bewerte sie an den unberührten Holdout-Fällen und jeder Muss-bestehen-Prüfung.
4. Befördere nur einen bedeutsamen, regressionsfreien Holdout-Sieg; protokolliere jedes Ergebnis und gib bei der Stoppbedingung den Champion zurück.

**Warum:** Das Arbeitsset von frischen Holdout-Fällen zu trennen, begrenzt Overfitting. Standardmäßig den aktuell Besten zu behalten, verhindert Regressionen, während ein festes Budget die Suche begrenzt.

### 024 — Der Advocatus-Diaboli-Loop

**Einsatz:** Nutze dies, bevor du dich auf eine Architektur, Schnittstelle, einen Rollout-Plan oder ein anderes folgenreiches Design festlegst, das von strukturierter adversarialer Prüfung profitiert.

**Prompt:**

> Bevor du dich auf eine Architektur, Schnittstelle oder einen Rollout-Plan festlegst, lass einen Kritiker argumentieren, dass sie falsch sind. Halte jeden Einwand, seine Auswirkung und seinen Status in einem repository-lokalen Log unter .agent-reviews/redteam.md fest. Der Erbauer muss jede Schwäche mit hoher Auswirkung beheben und verifizieren oder dokumentieren, warum sie akzeptiert wird; der Kritiker darf unbelegte Antworten wieder eröffnen. Stoppe, wenn kein Einwand mit hoher Auswirkung mehr offen ist oder sich dieselben Probleme zwei Runden lang ohne neuen Beleg wiederholen. Schließe ab mit der Entscheidung, den gelösten und akzeptierten Einwänden, den Belegen und jeder Pattsituation.

**Prüfen:** Kein Einwand mit hoher Auswirkung bleibt offen. Jeder protokollierte Einwand ist als gelöst verifiziert oder ausdrücklich mit Beleg akzeptiert, oder der Abschlussbericht hält wahrheitsgemäß eine Zwei-Runden-Pattsituation fest.

**Schritte:**

1. Schreibe die Designziele und Abnahmekriterien auf, initialisiere dann .agent-reviews/redteam.md im Repository und halte es aus den Commits heraus.
2. Lass den Kritiker den stärksten beleggestützten Fall gegen das aktuelle Design vorbringen und jeden Einwand nach Auswirkung einordnen.
3. Lass den Erbauer die Schwäche reparieren oder eine ausdrückliche Akzeptanzbegründung dokumentieren und das Ergebnis dann gegen die genannten Kriterien verifizieren.
4. Lass den Kritiker schwache Antworten wieder eröffnen und wiederhole, bis die Einwände mit Beleg geschlossen sind oder der Loop ehrlich eine Pattsituation meldet.

**Warum:** Die Trennung der Rollen von Kritiker und Erbauer macht Uneinigkeit explizit. Ein persistentes Einwand-Log verhindert zirkuläre Debatten, während beleggestützter Abschluss den Erbauer daran hindert, Erfolg allein durch Erklärung zu behaupten.

### 029 — Der Revolve-versionierte-Experiment-Loop

**Einsatz:** Verwende Revolve, um einen Prompt, eine Policy, einen Workflow, eine Modellkonfiguration, einen Code-Pfad oder ein Dataset zu verbessern, wenn Experimente über Sessions hinweg vergleichbar und wiederaufnehmbar bleiben müssen.

**Prompt:**

> Verwende Revolve, um einen Support-Prompt, einen Code-Pfad oder ein testbares Objekt zu verbessern. Definiere in revolve/ das Ziel und [Budget], friere die Tests und die Bewertung ein, lege einen Checkpoint der aktuellen Version an und erfasse eine Baseline. Teste in jeder Runde eine Hypothese; behalte nur einen klaren, regressionsfreien Gewinn. Wenn sich die Bewertung ändert, eröffne eine neue Revision und führe die Baseline erneut aus. Frage nach, bevor du Live-Dateien änderst. Stoppe bei Erfolg, ausbleibendem Fortschritt, einem Blocker oder erschöpftem Budget. Gib den besten Checkpoint, die Vergleiche, den Rollback und die nächste Aktion zurück.

**Prüfen:** Der beste Revolve-Checkpoint gewinnt innerhalb einer Bewertungsrevision. Amtsinhaber und Kandidaten haben vergleichbare erfasste Läufe, akzeptierte Änderungen bestehen jeden Schutz, ein Rollback ist verfügbar, und die Live-Promotion ist freigegeben.

**Schritte:**

1. Erstelle oder setze revolve/ fort, definiere das Ziel und die Berechtigungen, friere eine Bewertungsrevision ein, lege einen Checkpoint des Amtsinhabers an und erfasse seine Baseline.
2. Wähle eine belegte Hypothese, erstelle einen Kandidaten-Checkpoint und teste ihn unter der unveränderten Revision.
3. Promote intern nur bei einem bedeutenden, schutzsicheren Gewinn; wenn sich die Bewertung ändert, eröffne eine neue Revision und führe den Amtsinhaber erneut aus.
4. Stoppe bei einer benannten Bedingung und verlange eine ausdrückliche Freigabe sowie Verifikation, bevor du Live-Dateien änderst.

**Warum:** Die Revisionsgrenzen von Revolve verhindern, dass Bewertungen aus verschiedenen Tests oder Rastern als gleichwertig verglichen werden. Checkpoints und eine Intern-vor-Live-Promotion-Grenze halten langlaufende Forschung wiederaufnehmbar und umkehrbar.

### 032 — Der Versprechen-zu-Beleg-Loop

**Einsatz:** Verwende dies, wenn das, was ein Produkt zu tun verspricht, möglicherweise nicht mehr dem entspricht, was es tatsächlich tut – über Marketing, Dokumentation, Demos, Support-Antworten oder das Live-Produkt hinweg.

**Prompt:**

> Liste jedes kundengerichtete Versprechen auf, das [Produkt] in Marketing, Dokumentation, Demos und KI-Antworten macht. Vergleiche jedes Versprechen mit dem aktuellen Produktverhalten und den Belegen und kennzeichne es dann als belegt, teilweise belegt, irreführend, unbelegt, veraltet oder ohne Beleg. Behebe oder enge die riskanteste Abweichung ein und führe den betroffenen Prüfschritt erneut aus. Wiederhole, bis kein hochriskantes unbelegtes Versprechen mehr verbleibt. Frage nach, bevor du Produktion oder öffentliche Texte änderst. Gib die Versprechen, Belege, Behebungen und benötigten Entscheidungen zurück.

**Prüfen:** Jedes hochriskante Kundenversprechen ist belegt, eingeengt oder wartet auf eine ausdrückliche Entscheidung. Jedes Versprechen ist mit einem aktuellen Beleg verknüpft, und jede hochriskante Abweichung ist behoben, auf das eingeengt, was das Produkt belegen kann, oder klar freigabepflichtig.

**Schritte:**

1. Liste die für Kunden sichtbaren Versprechen auf und formuliere jedes als konkrete Erwartung um, etwa ein funktionierendes Feature, eine eingehaltene Grenze oder eine zutreffende Antwort.
2. Vergleiche jede Erwartung mit dem aktuellen Produktverhalten, Code, Tests, Dokumentation, Beispielen, Logs oder anderen direkten Belegen; rate nicht.
3. Ordne die Abweichungen nach dem Schaden, den sie dem Kundenvertrauen zufügen könnten, und behebe dann die riskanteste oder enge das öffentliche Versprechen auf das ein, was das Produkt belegen kann.
4. Führe denselben Prüfschritt erneut aus und wiederhole, bis kein hochriskantes unbelegtes Versprechen mehr verbleibt, der Fortschritt blockiert ist oder die nächste Handlung eine Freigabe erfordert.

**Warum:** Dies verwandelt eine vage Frage – können Kunden dem vertrauen, was wir sagen? – in eine Liste von Versprechen, die einzeln geprüft werden können. Eine riskante Abweichung nach der anderen zu beheben hält das Produkt und seine öffentliche Erklärung in Einklang, ohne das Audit in ein unkontrolliertes Umschreiben zu verwandeln.

### 034 — Der Multi-LLM-Konvergenz-Loop

**Einsatz:** Verwende dies, wenn ein wichtiger Plan, eine Spezifikation, ein Design, ein Dokument oder eine Code-Änderung von zwei unabhängigen KI-Perspektiven profitiert, statt dass ein Modell seine eigenen blinden Flecken prüft.

**Prompt:**

> Prüfe [Plan, Spezifikation, Dokument oder Code-Änderung] gegen [Qualitätsmaßstab] für höchstens [Durchlaufgrenze] Runden. Lass eine von zwei wirklich verschiedenen Modellfamilien – KI-Systemen von getrennten Anbietern – sie prüfen. Verifiziere jeden Befund und wende nur notwendige Behebungen an, übergib dann die überarbeitete Version dem anderen Prüfer. Erfolg nur, wenn beide dieselbe unveränderte Version freigeben. Stoppe bei der Grenze, bei wiederkehrender Uneinigkeit (Oszillation), nicht verfügbarer Prüfung oder erforderlicher Freigabe. Gib das finale Werk, das Rundenprotokoll, das Verdikt und die Uneinigkeiten zurück.

**Prüfen:** Zwei verschiedene KI-Modellfamilien geben exakt dieselbe Version frei. Die letzten beiden sauberen Prüfungen stammen von verschiedenen Modellfamilien ohne Änderung dazwischen; eine Durchlaufgrenze, wiederkehrende Uneinigkeit, ein nicht verfügbarer Prüfer oder eine Freigabegrenze wird als Stillstand statt als Konsens gemeldet.

**Schritte:**

1. Wähle das zu prüfende Werk, definiere, was als akzeptabel gilt, setze eine maximale Rundenzahl und sammle das Quellmaterial, dem die Prüfer vertrauen sollen.
2. Übergib die aktuelle Version der ersten KI-Modellfamilie, prüfe, ob jeder Befund gültig ist, wende nur notwendige Behebungen an und protokolliere die Runde.
3. Übergib die resultierende Version der anderen Modellfamilie; wenn einer der Prüfer eine weitere Änderung auslöst, müssen beide die neue Version erneut prüfen.
4. Schließe nur ab, wenn beide unabhängig eine unveränderte Version freigeben; andernfalls stoppe bei der Rundengrenze, beim wiederkehrenden Hin und Her, beim Prüferausfall oder an einer Freigabegrenze.

**Warum:** Verschiedene Modellfamilien können verschiedene Probleme bemerken. Beide zur Freigabe exakt derselben Version zu verpflichten verhindert, dass eine saubere Prüfung eines älteren Entwurfs als Freigabe eines neueren gewertet wird, und das Rundenprotokoll zeigt, wie die Übereinstimmung erreicht wurde.

### 039 — Der Easy-Onboarding-Loop

**Einsatz:** Setze dies ein, wenn neue Nutzer auf unklare Anweisungen, versteckte Annahmen, muehsame Wiederherstellung oder unnoetige Schritte stossen koennten, die erfahrene Nutzer nicht mehr bemerken, weil ihre Konten und Browser fruehere Einrichtung gespeichert haben.

**Prompt:**

> Verhalte dich wie ein Erstnutzer von [Produkt]. Starte am echten Einstiegspunkt in einer sauberen Sitzung ohne gespeicherten Login, Website-Daten, gemerkte Route oder versteckte Einrichtung. Schliesse das Onboarding nur mit sichtbarer Anleitung ab und halte Hindernisse fest. Behebe das schlimmste mit der kleinsten Aenderung, die jede Sicherheits-, Zugriffs- und Produktanforderung wahrt. Verwirf die Sitzung und versuche es erneut. Stoppe nach einem ununterbrochenen Erfolg, wenn keine sichere Behebung moeglich ist, der Zugang blockiert ist oder eine Freigabe erforderlich ist. Gib den Pfad, Aenderungen, Belege und Blocker zurueck.

**Prüfen:** Ein Erstnutzer kann das Onboarding in einer ununterbrochenen sauberen Sitzung abschliessen. Das gesamte Erlebnis gelingt vom echten Ausgangspunkt aus ohne gespeicherten Browserzustand, geheime Einrichtung, erratene Routen oder manuelle Reparaturen, und jede echte Anforderung bleibt intakt.

**Schritte:**

1. Oeffne eine saubere Sitzung ohne gespeicherten Login, Cookies, Website-Speicher, gemerkte Webadresse, geheime Einrichtung oder Reparatur aus einem frueheren Versuch.
2. Beginne dort, wo ein echter Neuling beginnt, schliesse die Onboarding-Schritte nur mit sichtbarer Anleitung ab und halte alles fest, was unklar, unerklaert, unnoetig muehsam oder nicht wiederherstellbar ist.
3. Behebe das schaedlichste Hindernis mit der kleinsten Aenderung, die Sicherheits-, Zugriffs-, Rechts-, Onboarding- und Produktanforderungen wahrt.
4. Verwirf die Sitzung und versuche das gesamte Erlebnis erneut, bis ein ununterbrochener sauberer Durchlauf gelingt oder kein sicherer Fortschritt mehr moeglich ist, der Zugang blockiert ist oder eine Freigabe erforderlich ist.

**Warum:** Gespeicherte Logins und gemerkte Einrichtung verbergen Probleme vor erfahrenen Nutzern. Nach jeder Behebung von vorn zu beginnen zeigt, ob das Produkt selbst den Weg nun erklaert, waehrend das Wahren echter Anforderungen verhindert, dass ein einfacheres Erlebnis Sicherheits- oder Zugriffskontrollen schwaecht.

### 042 — Der Axelrod-Subagenten-Arena-Loop

**Einsatz:** Setze dies als kontrolliertes Experiment ein, um zu sehen, ob KI-Agenten Verhaltensweisen wiederholter Interaktion erlernen, etwa Kooperation, Vergeltung nach Verrat, Vergebung, Ausbeutung und unterschiedliche Strategien für unterschiedliche Gegner.

**Prompt:**

> Führe ein festes Axelrod-Turnier mit zwei schlussfolgernden KI-Agenten durch. In jeder Runde wählt jeder Spieler privat kooperieren (C) oder defektieren (D); der Code erfasst gleichzeitige Züge und wendet feste Bewertung an. Schließe Immer-Defektieren- und Immer-Kooperieren-Vergleichsspieler ein. Führe drei Zyklen aus, sechs Paarungen pro Zyklus und zehn Runden pro Paarung: 18 Matches und 180 Runden. Verberge Gegnertyp und private Schlussfolgerung. Validiere jeden Zug und jede Summe. Gib Rohwert- und Kooperationsstabilitäts-Ranglisten, Schlussfolgerungs-Zusammenfassungen, Verstöße und das Protokoll zurück; Teil-Turniere sind unvollständig.

**Prüfen:** Alle 18 Matches und 180 Runden lassen sich aus den erfassten Zügen und den festen Bewertungsregeln reproduzieren. Jeder Agent wählt, bevor er den Zug des Gegners sieht, jeder Zug wird vor der Bewertung erfasst, Summen reproduzieren sich aus der vollständigen Historie, ungültige Antworten werden protokolliert, und jedes Teil- oder ungültige Turnier bleibt ausdrücklich unvollständig.

**Schritte:**

1. Richte feste Bewertung, Zugvalidierung, den Match-Spielplan, gespeicherte Historie für jedes Paar, zwei schlussfolgernde KI-Spieler, einen Spieler, der immer kooperiert, und einen, der immer defektiert, ein; der Code darf Züge bewerten, aber niemals für die schlussfolgernden Agenten wählen.
2. Lasse vor jedem der drei Turnierzyklen jeden schlussfolgernden Agenten eine begrenzte Strategie wählen, die nur auf dem beruht, was in seinen eigenen früheren Matches mit dem jeweiligen Gegner geschah.
3. Führe alle sechs möglichen Paarungen über zehn Runden aus und erfasse Kooperieren- oder Defektieren-Entscheidungen gleichzeitig, während Gegneridentität und private Schlussfolgerung verborgen bleiben; erfasse jeden Zug, jeden Wert und jede erlaubte Erklärung.
4. Berechne alle 18 Matches und 180 Runden aus dem gespeicherten Protokoll neu und berichte dann sowohl Gesamtpunkte als auch Kooperationsstabilitäts-Maße, Strategiewechsel, Schlussfolgerungs-Zusammenfassungen, Regelverstöße und etwaige unvollständige Daten.

**Warum:** Die Immer-Kooperieren- und Immer-Defektieren-Spieler liefern einfache Vergleichspunkte: Sie zeigen, ob die schlussfolgernden Agenten leichte Gegner ausbeuten, sich verteidigen, Kooperation wieder aufbauen oder die Strategie wechseln. Verborgene Identitäten, gleichzeitige Entscheidungen, gespeicherte Paar-Historien und neu berechnete Werte halten das Experiment fair und auditierbar.

### 045 — Der Artefakt-zu-Skill-Loop

**Einsatz:** Setze dies ein, wenn ein fertiggestelltes Artefakt einen Erfolgsbeleg besitzt, eine wiederholbare Methode zu enthalten scheint und ähnliche Arbeit wahrscheinlich wieder vorkommt.

**Prompt:**

> Verwandle [Artefakt] in einen Skill, ein Playbook oder eine Prozedur. Halte den Beleg fest, dass das Artefakt erfolgreich war, und definiere Erfolgskriterien. Extrahiere Entscheidungen, Abfolge, Prüfungen und Muster zur Fehlervermeidung - nicht Kontext oder oberflächlichen Stil. Entferne sensibles Material. Lasse einen unabhängigen Prüfer es auf einen frischen echten zweiten Fall anwenden; markiere hypothetisches Testen als vorläufig. Überarbeite höchstens zweimal. Stoppe, wenn es die Qualitätsmesslatte ohne das Artefakt erreicht, oder melde, dass es nicht generalisierbar ist. Gib die Methode, Grenzen, Fehlermodi, Testbeleg, Überarbeitungen, Einschränkungen und Zuschreibung zurück.

**Prüfen:** Die extrahierte Methode gelingt bei einem frischen zweiten Fall ohne das ursprüngliche Artefakt. Ein unabhängiger Prüfer wendet die wiederverwendbare Version unter vor der Extraktion definierten Kriterien an, und das zweite Ergebnis erreicht die nachgewiesene Qualitätsmesslatte des Quell-Artefakts, oder die Methode wird ehrlich als vorläufig oder nicht generalisierbar markiert.

**Schritte:**

1. Bestätige, dass das Quell-Artefakt einen glaubwürdigen Erfolgsbeleg besitzt, definiere die Qualitätskriterien, die es erfüllt hat, und schließe sensibles oder geschütztes Material aus, das nicht übertragen werden sollte.
2. Trenne die dauerhaften Entscheidungen, die Abfolge, Prüfungen, Standards und Muster zur Fehlervermeidung von einmaligen Fakten, Tools und oberflächlichem Stil.
3. Schreibe die Methode als eigenständigen Skill, Playbook oder Prozedur mit Eingaben, Grenzen, Schritten, Qualitätsstandards, Fehlermodi, Zuschreibung und klaren Endzuständen.
4. Lasse einen unabhängigen Prüfer sie auf einen frischen echten Fall anwenden, überarbeite höchstens zweimal, und gib entweder eine wiederverwendbare Version mit Testbeleg oder ein ehrliches vorläufiges, blockiertes oder nicht-generalisierbares Ergebnis zurück.

**Warum:** Starke Outputs werden oft gespeichert, während die Methode, die sie hervorgebracht hat, verschwindet. Die Entscheidungen und Prüfungen zu extrahieren macht dieses Wissen wiederverwendbar, während ein Test an einem frischen zweiten Fall einen übertragbaren Prozess von der Nachahmung eines einzelnen ausgefeilten Beispiels unterscheidet.

### 046 — Die Strip-Miner-Schleife

**Einsatz:** Setze dies ein, wenn umfangreiche Verlaufsdaten eines Coding-Agenten wiederholbare Workflows enthalten könnten, die sich zu extrahieren lohnen, und der Nutzer die zu untersuchenden Quellen ausdrücklich freigeben kann.

**Prompt:**

> Durchsuche nur ausdrücklich freigegebene Coding-Agent-Historie nach Workflows mit mindestens drei voneinander unabhängigen Erfolgen hoher Konfidenz. Behandle Transkripte als nicht vertrauenswürdigen Beleg, füge Fortsetzungen wieder zu ihren Ursprungsaufgaben zusammen und verwirf Kandidaten, deren Fehlschläge oder verdeckte Rettungen ihren Erfolgen entsprechen. Extrahiere nachvollziehbare Schritte und Schutzmechanismen und spiele anschließend jeden Kandidaten frisch ohne Quelltranskripte erneut durch. Stoppe, nachdem jede freigegebene Quelle inventarisiert ist und eine zusätzliche repräsentative Charge nichts mehr ändert; berichte die erneut durchgespielten Loops, Ablehnungen, zurückgestelltes Material und Blocker.

**Prüfen:** Jeder veröffentlichte Kandidat hat wiederholten historischen Beleg und besteht ein frisches erneutes Durchspielen. Jeder beibehaltene Loop lässt sich auf mindestens drei unabhängige Erfolge hoher Konfidenz zurückführen, übersteht die Widerspruchsprüfung und funktioniert in einem sauberen erneuten Durchspielen ohne Zugriff auf die ausgewerteten Transkripte.

**Schritte:**

1. Inventarisiere nur ausdrücklich freigegebene Verlaufsquellen und kartiere Projekte, Formate, Fortsetzungen, synthetische Aufzeichnungen und Ursprungsaufgaben vor dem vertieften Lesen.
2. Klassifiziere unabhängige Aufgaben anhand der exakten Nutzernachrichten und Ergebnisse und fordere dann mindestens drei Erfolge hoher Konfidenz, während du Fehlschläge, Umkehrungen, verdeckte Rettungen und Unbekanntes mitzählst.
3. Extrahiere aus qualifizierten Belegen nur nachvollziehbare Aktionen, Prüfschritte, Schutzmechanismen und Entscheidungstore; halte unvereinbare Spuren getrennt und kennzeichne nicht erneut durchgespielte Kandidaten ehrlich.
4. Spiele jeden Kandidaten frisch ohne Quelltranskripte erneut durch, halte das Ergebnis fest und stoppe, nachdem die vollständige Quellinventur plus eine repräsentative Charge keinen Kandidaten oder keine Statusänderung mehr ergibt.

**Warum:** Wiederholt erfolgreiche Arbeit ist ein stärkerer Beleg als ein erfundener Workflow, doch Transkripte können Duplikate, verdeckte Eingriffe und spätere Umkehrungen enthalten. Qualifikation, Widerspruchszählung und sauberes erneutes Durchspielen trennen wiederverwendbare Praxis von einer überzeugenden Anekdote.


## Operations / Betrieb

### 013 — Der veralterungssichere Sammel-Release-Loop

**Einsatz:** Verwende dies, wenn mehrere Branches oder Pull Requests gleichzeitig bereit sein könnten und das Release veraltete Worktrees, teilweise angewendete Overlays und unfertige Änderungen vermeiden muss.

**Prompt:**

> Prüfe ausstehende Änderungen und Pull Requests, schließe veraltete oder unfertige Arbeit aus, kombiniere die gültigen Änderungen und veröffentliche sie gemeinsam.

**Prüfen:** Nur aktuelle, vollständige Änderungen gehen im kombinierten Release in Produktion. Die veröffentlichte Revision ist der jüngste integrierte Main, der jede ausgewählte Änderung enthält.

**Schritte:**

1. Hole den aktuellen Zustand von Repository und Pull Requests ab und untersuche dann jede Kandidaten-Änderung auf Aktualität, Vollständigkeit, Eigentümerschaft, Prüfschritte und Abhängigkeiten.
2. Schließe veraltete, abgelöste, in Konflikt stehende oder unfertige Arbeit aus und halte fest, warum jeder Kandidat weggelassen wurde.
3. Integriere die gültigen Änderungen, lasse die kombinierten Prüfschritte erneut laufen und wähle die neueste Main-Revision, die den vollständigen Stapel enthält.
4. Veröffentliche vollständige Artefakte aus einem sauberen Checkout, serialisiere das Deployment und verifiziere die Produktion, bevor du den Stapel abschließt.

**Warum:** Das Bewerten aller Kandidaten vor der Integration verhindert, dass veralteter Code aus Bequemlichkeit oder durch Worktree-Verwirrung in ein Release gelangt. Das Veröffentlichen aus dem integrierten Main belegt, dass das ausgelieferte Artefakt dem geprüften Stapel entspricht.

### 014 — Der Produktionsdaten-Aufräum-Loop

**Einsatz:** Verwende dies, wenn ein Produktionsdatensatz Datensätze enthält, die nicht mehr zu einer Produkt-, Richtlinien-, Taxonomie- oder Qualitätsdefinition passen, und der Klassifizierer sie durchgelassen hat.

**Prompt:**

> Prüfe Produktionsdatensätze, entferne alles, was die zulässige Definition nicht erfüllt, verbessere die Klassifizierungslogik und verifiziere die verbleibenden Daten.

**Prüfen:** Jeder verbleibende Datensatz erfüllt die zulässige Definition. Repräsentative Klassifizierungstests und ein Audit nach dem Aufräumen belegen, dass die behaltenen Daten gültig sind.

**Schritte:**

1. Schreibe die zulässige Definition als explizite Einschluss-, Ausschluss- und Randfallregeln auf, bevor du Daten veränderst.
2. Auditiere Produktionsdatensätze, bewahre einen wiederherstellbaren Beleg der vorgeschlagenen Entfernungen und trenne klare Verstöße von unsicheren Fällen.
3. Entferne bestätigte ungültige Datensätze über den freigegebenen Produktionspfad und verbessere den Klassifizierer mit Regressionsbeispielen.
4. Lasse die Klassifizierungstests erneut laufen und auditiere die verbleibenden Produktionsdaten, bis jeder stichprobenartig geprüfte und abgefragte Datensatz die Definition erfüllt.

**Warum:** Das Beheben sowohl der vorhandenen Datensätze als auch des Klassifizierers schließt das unmittelbare Datenproblem und verringert das erneute Auftreten. Explizite Regeln und Regressionsbeispiele machen künftige Aufräum-Entscheidungen nachprüfbar.

### 015 — Der Post-Release-Baseline-Loop

**Einsatz:** Verwende dies unmittelbar nach einem Release, wenn künftige Regressionen oder Verbesserungen gegen die exakte Version gemessen werden müssen, die jetzt in Produktion ist.

**Prompt:**

> Nachdem die aktuellen Releases abgeschlossen sind, lasse die Standard-Benchmarks laufen und erfasse die Ergebnisse als neue Baseline.

**Prüfen:** Die neue Baseline gehört zum abgeschlossenen Release. Revision, Umgebung, Benchmark-Version, Bedingungen und Ergebnisse werden gemeinsam erfasst.

**Schritte:**

1. Bestätige, dass jedes im Umfang liegende Release abgeschlossen ist, und erfasse die Produktionsrevision oder Artefakt-Identität.
2. Lasse die Standard-Benchmark-Suite unter ihren dokumentierten Regeln für Umgebung, Daten, Aufwärmen und Wiederholung laufen.
3. Untersuche ungültige oder instabile Läufe und lasse sie nur unter denselben dokumentierten Bedingungen erneut laufen.
4. Speichere die endgültigen Ergebnisse zusammen mit der Release-Identität und den Benchmark-Metadaten und markiere sie als neue Vergleichs-Baseline.

**Warum:** Das Verknüpfen der Baseline mit einem verifizierten Release schafft einen vertrauenswürdigen Bezugspunkt für spätere Performance- und Qualitätsarbeit. Das Erfassen der Bedingungen verhindert, dass unzusammenhängende Umgebungsänderungen sich als Produktänderungen ausgeben.

### 017 — Der Kunden-KI-Deployment-Loop

**Einsatz:** Verwende dies, wenn ein KI-Workflow in einem echten Kundenprozess leben muss und Validierung, Freigabe, schrittweisen Rollout, Monitoring und ein klares Geschäftsergebnis benötigt.

**Prompt:**

> Führe dies aus, wenn ein Kunde einen KI-Workflow anfragt, einen Fehler meldet oder ein Operations-Review erreicht wird. Wähle eine Priorität, etwa das Anreichern von Leads, das Verfassen von E-Mails, das Zusammenfassen von Meetings oder das Aktualisieren eines CRM. Definiere den Verantwortlichen, die Eingaben, die Freigaben, die Erfolgsmetrik und die ROI-Hypothese. Führe einen Probelauf mit realistischen Kundendaten durch, behebe das kleinste verifizierte Problem und gib dann über freigegebene Stufen frei und überwache die Produktion. Schließe ab mit dem Ergebnis, dem Beleg, dem Kunden-Update, den gesicherten Erkenntnissen und dem nächsten Review.

**Prüfen:** Eine Kundenpriorität erreicht einen nachgewiesenen Endzustand. Der Workflow erreicht seine vereinbarte Rollout-Stufe, ein Produktionsproblem ist behoben, oder ein Blocker wird mit Verantwortlichem und nächstem Schritt eskaliert.

**Schritte:**

1. Prüfe die Kundenpriorität, das jüngste Feedback, die Workflow-Historie, Fehler, Freigaben, Nutzung, Kosten und ROI-Signale.
2. Wähle einen Workflow oder eine Verbesserung und definiere den Verantwortlichen, die Systeme, die Daten, das Risiko, die Freigabe-Gates, die Erfolgskriterien und die ROI-Hypothese.
3. Führe einen Probelauf mit realistischen Kundendaten durch, behebe das kleinste zugrunde liegende Problem und gib über kontrollierte Stufen frei.
4. Überwache die Produktion, sende das Kunden-Update und sichere wiederverwendbare Präferenzen, Fehler, Beispiele und ROI-Beobachtungen.

**Warum:** Der Workflow selbst ist nur ein Teil eines echten Deployments. Dieser Loop hält Validierung, Freigabe, Rollout, Monitoring, Lernen und Verantwortlichkeit an eine Kundenpriorität gebunden.

### 047 — Die Living-Story-Schleife

**Einsatz:** Setze dies ein, wenn sich die Arbeit über mehrere Repositories oder Kontextquellen erstreckt und künftige Agenten eine wiederkehrende, belegbasierte Darstellung von Prioritäten, Fortschritt, Fristen und unerledigter Arbeit brauchen.

**Prompt:**

> Lies in jedem [Fenster] die konfigurierten Repositories, Ziele, die vorherige STORY.md und optionale freigegebene Quellen. Aktualisiere die Projektdateien und schreibe dann STORY.md mit Fokus, Fristen, offenen Strängen und belegbasierten jüngsten Erfolgen. Trage jeden vorherigen Strang weiter, belege ihn als abgeschlossen oder markiere ihn als STALE/NEEDS-REVIEW — lass nie einen stillschweigend wegfallen. Archiviere den Schnappschuss und halte die Änderung fest. Stoppe, wenn der Prüfschritt besteht; fehlen Beleg oder Zugriff, gib einen ausdrücklich dünneren oder blockierten Schnappschuss zurück.

**Prüfen:** Die aktuelle Story berücksichtigt jeden vorherigen Strang und belegt jeden jüngsten Erfolg. Jeder zuvor offene Strang wird weitergetragen, mit Beleg geschlossen oder sichtbar markiert, und jeder behauptete Erfolg verweist auf einen Commit, ein Release, eine geschlossene Aufgabe, ein Deployment, ein versendetes Ergebnis oder ein erzeugtes Artefakt.

**Schritte:**

1. Lies die konfigurierten Repositories, Ziele, den persönlichen Kontext, optionale freigegebene Quellen, die vorherige STORY.md und die bestehenden Projektdateien; melde fehlende Eingaben, statt sie zu erfinden.
2. Aktualisiere jeden Projektdatensatz mit der aktuellen Aktivität, dem Branch-Stand, ausgeliefertem Beleg, laufender Arbeit und veraltetem Status innerhalb des konfigurierten Fensters.
3. Schreibe die neue Story mit Deutung, Fokus, Fristen, offenen Strängen und belegbasierten jüngsten Erfolgen statt einer rohen Commit-Liste.
4. Gleiche jeden vorherigen Strang ab, archiviere den geprüften Schnappschuss, aktualisiere das Changelog und stoppe mit einem ausdrücklichen vollständigen, dünneren oder blockierten Ergebnis.

**Warum:** Eine wiederkehrende Erzählung bewahrt die Bedeutung hinter der Aktivität, ohne alte Zusagen verschwinden zu lassen. Belegpflichten halten jüngste Erfolge faktisch, während der Strang-Abgleich veraltete oder unerledigte Arbeit für den nächsten Agenten sichtbar macht.

### 049 — Die Recovery-Proof-Schleife

**Einsatz:** Setze dies ein, wenn die bloße Existenz von Backups nicht ausreicht und die Organisation wiederholbaren Beleg braucht, dass sich erforderliche Systeme aus dokumentierten Materialien innerhalb der vereinbarten Wiederherstellungsziele zurückspielen lassen.

**Prompt:**

> Wähle für jedes erforderliche Wiederherstellungsszenario zufällig ein geeignetes echtes Backup oder einen geeigneten Wiederherstellungspunkt aus und spiele es von Null in einem verwerfbaren, isolierten Clean-Room ausschließlich anhand dokumentierter Materialien zurück. Verifiziere Integrität, Abhängigkeiten, repräsentative Lese- und Schreibzugriffe sowie die tatsächlichen RPO und RTO. Behebe einen Blocker, zerstöre die Umgebung und versuche es frisch erneut. Stoppe, wenn jedes Szenario seine vorab festgelegte Serie aufeinanderfolgender Erfolge erreicht oder eine Ausnahme ausdrücklich akzeptiert wird. Überschreibe niemals die Produktion, lege niemals wiederhergestellte Daten offen und löse niemals ohne Freigabe ein Failover aus.

**Prüfen:** Jedes erforderliche Wiederherstellungsszenario gelingt wiederholt aus einem echten Wiederherstellungspunkt. Frische Clean-Room-Wiederherstellungen erfüllen die Prüfungen zu Integrität, Abhängigkeiten, repräsentativen Lese-/Schreibzugriffen, RPO und RTO unter unveränderten Kriterien, wobei Fehlschläge als Regressionsübungen erhalten bleiben und wiederhergestellte Daten sicher zerstört werden.

**Schritte:**

1. Definiere die erforderlichen Szenarien, geeigneten Wiederherstellungspunkte, unveränderten Erfolgskriterien, die Serie aufeinanderfolgender Erfolge, die Isolationskontrollen und die Freigabegrenzen, bevor du irgendetwas zurückspielst.
2. Wähle zufällig einen geeigneten echten Wiederherstellungspunkt aus, spiele ihn von Null in einem verwerfbaren Clean-Room ausschließlich anhand dokumentierter Materialien zurück und miss die tatsächlichen RPO und RTO.
3. Verifiziere Prüfsummen, Kontrollsummen, referenzielle Integrität, Schlüssel, Abhängigkeiten sowie repräsentative geschäftliche Lese- und Schreibzugriffe; bewahre jeden Fehlschlag als Regressionsübung.
4. Behebe einen Wiederherstellungs-Blocker, zerstöre die Umgebung sicher und versuche es frisch erneut, bis jedes Szenario seine Serie besteht oder eine ungelöste Ausnahme ausdrücklich akzeptiert wird.

**Warum:** Ein Backup ist nur nützlich, wenn ein echter Wiederherstellungspunkt das erforderliche System unter dokumentierten Bedingungen wieder aufbauen kann. Zufällige Auswahl, frische Umgebungen, gemessene Ziele und wiederholter Erfolg decken Lücken auf, die eine einmalige skriptgesteuerte Wiederherstellung verbergen kann.

### 050 — Die Rückerstattungs-Nachfass-Schleife

**Einsatz:** Setze dies ein, wenn dir jemand eine Rückerstattung schuldet und es mehr als ein Support-Gespräch oder Nachfassen erfordern könnte, sie zu bekommen.

**Prompt:**

> Hol meine Rückerstattung für [Firmen- und Abbuchungsangaben]. Starte den Anspruch jetzt über einen freigegebenen Support-Kanal und fasse dann bei Antworten, Zusagen und Fristen weiter nach, bis die Rückerstattung eintrifft. Führe eine kurze Fallnotiz, damit jedes Nachfassen Kontext hat. Stoppe nur, wenn die Rückerstattung eingegangen ist oder du wirklich blockiert bist und mich brauchst.

**Prüfen:** Die Rückerstattung ist eingegangen, oder ein echter Blocker erfordert den Nutzer. Ein offener Anspruch, eine Zusage oder eine ausstehende Rückerstattung ist Fortschritt, kein Erfolg; fasse weiter nach, bis das Geld eintrifft oder kein freigegebener nächster Schritt mehr besteht.

**Schritte:**

1. Sammle die Buchung, den Grund für die Rückerstattung, nützliche Belege, den aktuellen Status sowie jedes frühere Gespräch oder jede Zusage.
2. Starte oder setze den Anspruch über einen vom Nutzer freigegebenen Support-Kanal fort und notiere dann, was passiert ist und was als Nächstes geschehen sollte.
3. Fasse immer dann nach, wenn eine Antwort, Zusage oder Frist einen nützlichen nächsten Schritt ergibt; halte den Fall in Bewegung, statt einen ausstehenden Status als erledigt zu behandeln.
4. Stoppe, wenn die Rückerstattung eintrifft, oder erläutere den echten Blocker, wenn der nächste nützliche Schritt den Nutzer erfordert.

**Warum:** Rückerstattungen bleiben oft stecken, weil eine Zusage oder ein ausstehender Status als Abschluss behandelt wird. Diese Schleife behält die Verantwortung über Verzögerungen und Übergaben hinweg, bis das Geld tatsächlich eintrifft.


## Content / Redaktion

### 006 — Der SEO/GEO-Sichtbarkeits-Loop

**Einsatz:** Verwende dies, wenn eine Website eine definierte Menge an Prioritätsseiten und Zielfragen hat und du nach jeder Änderung denselben technischen Crawl und dieselben Such-Sichtbarkeitsprüfungen erneut ausführen kannst.

**Prompt:**

> Führe ein SEO/GEO-Audit über Crawlbarkeit, Indexierung, Seitenintention, Titel, interne Verlinkung, strukturierte Daten, Quellenzitate und Answer-First-Inhalte durch. Ordne die Lücken nach erwarteter Wirkung, behebe das Problem mit dem höchsten Hebel und führe dann denselben Crawl und denselben Zielanfragen-Benchmark über Suchmaschinen und KI-Antwortmaschinen erneut aus. Wiederhole, bis kein kritisches technisches Problem mehr besteht, jede Prioritätsanfrage einer klaren, antwortbereiten Seite zugeordnet ist und der Benchmark keine verbleibende Lücke mit hoher Wirkung mehr zeigt, die noch zu beheben wäre.

**Prüfen:** Prioritätsseiten sind indexierbar, antwortbereit und technisch solide. Der wiederholbare Crawl und der Anfragen-Benchmark finden keine verbleibenden Lücken mit hoher Wirkung.

**Schritte:**

1. Erfasse die Zielanfragen, Antwortmaschinen, Suchmaschinen, das Gebietsschema, das Datum und die Benchmark-Methode.
2. Auditiere Crawlbarkeit, Indexierung, Seitenintention, Titel, interne Verlinkung, strukturierte Daten, Zitate und die sichtbare Antwortqualität.
3. Ordne die Befunde nach erwarteter Wirkung und behebe jeweils ein Problem mit hohem Hebel.
4. Führe den ursprünglichen Crawl und den Anfragen-Benchmark erneut aus, bis kein kritisches technisches Problem und keine Inhaltslücke mit hoher Wirkung mehr besteht.

**Warum:** Ein fester Benchmark macht Sichtbarkeitsarbeit messbar und verhindert, dass eine lange Liste geringwertiger SEO-Aufgaben die Behebung mit der höchsten Wirkung verdrängt. Jede Prioritätsanfrage einer starken Seite zuzuordnen, gibt Such- und Antwortsystemen zudem ein klares Ziel.

### 018 — Der Produkt-Update-Podcast-Loop

**Einsatz:** Verwende dies, wenn ein Produkt häufig genug ausliefert, dass Nutzer von einer kurzen wiederkehrenden Audio-Erklärung profitieren würden, was sich geändert hat und wie es zu nutzen ist.

**Prompt:**

> Prüfe jede Nacht die öffentlich veröffentlichten Produktänderungen und wähle nur jene aus, die Nutzer kennen müssen. Verifiziere jede gegen das Produkt, die Doku oder die Release Notes. Nutze den Jellypod MCP, um die freigegebenen Änderungen in einen drei- bis fünfminütigen Podcast zu verwandeln, der erklärt, was sich geändert hat, warum es wichtig ist und wie man es ausprobiert. Prüfe das Skript und die Audioausgabe auf Korrektheit, Klarheit und Aussprache. Wenn nichts Bedeutsames ausgeliefert wurde, erstelle keine Folge. Frage vor dem Veröffentlichen. Schließe ab mit der Entwurfsfolge, den Quellen und dem Prüfergebnis.

**Prüfen:** Die Folge deckt jedes bedeutsame öffentliche Update korrekt ab. Schließe ab mit einer reviewreifen drei- bis fünfminütigen Folge oder einem bestätigten Kein-Folge-Ergebnis, wenn nichts Bedeutsames ausgeliefert wurde.

**Schritte:**

1. Sammle die öffentlichen Produktänderungen, die Dokumentation und die Release Notes des Vortags.
2. Wähle die für Nutzer bedeutsamsten Änderungen aus und verifiziere, was tatsächlich ausgeliefert wurde.
3. Nutze Jellypod, um eine drei- bis fünfminütige Folge zu entwerfen, die den Nutzen und das Ausprobieren jeder ausgewählten Änderung abdeckt.
4. Prüfe Skript und Audio gegen die Quellen, generiere schwache Passagen neu und fordere vor dem Veröffentlichen die Freigabe an.

**Warum:** Ein festes Release-Fenster hält die Abdeckung aktuell, während redaktionelle Auswahl und Quellenprüfung verhindern, dass die Folge zu einem automatisierten Vorlesen von Commit-Titeln wird.


## Design

### 021 — Der Boeing-747-Benchmark

**Einsatz:** Nutze dies als konkreten Three.js-Vision-Benchmark oder übertrage dasselbe Capture-und-Kritiker-Muster auf ein anderes gerendertes Objekt.

**Prompt:**

> Wähle vor dem Bau Referenzbilder, ein Bewertungsraster, [visuelle Schwelle] und [Budget]. Baue die realistischste Boeing 747, die du aus Three.js-Primitiven erstellen kannst, und richte dann ein Rig ein, das neun wiederholbare Winkel als Screenshot festhält. Rendere und bewerte nach jeder Änderung dieselben Ansichten, lass einen Kritiker das schwächste Merkmal bestimmen und behebe es, ohne stärkere Ansichten zu verschlechtern. Behalte die beste Version. Stoppe bei der Schwelle, stockendem Fortschritt oder Budget. Schließe ab mit dem Modell, neun Renderings, Bewertungen, verbleibenden Lücken und einer Lauf-Zusammenfassung.

**Prüfen:** Die Boeing 747 erreicht aus allen neun Winkeln die visuelle Messlatte. Dasselbe Kamera-Rig und Bewertungsraster zeigen, dass jede geforderte Ansicht die voreingestellte Schwelle erreicht, oder der Lauf meldet Stagnation, Budget-Erschöpfung und verbleibende Lücken.

**Schritte:**

1. Wähle Referenzbilder, ein Bewertungsraster, eine visuelle Schwelle und ein Budget; baue dann die erste Boeing 747 aus Three.js-Primitiven.
2. Richte ein wiederholbares Rig ein, das nach jeder bedeutsamen Änderung dieselben neun Winkel rendert.
3. Bewerte jede Ansicht gegen die Referenzen, lass einen Kritiker das schwächste Merkmal bestimmen und behebe es, ohne stärkere Arbeit zu verlieren.
4. Behalte die beste Version und wiederhole, bis alle neun Ansichten die visuelle Messlatte überschreiten oder ein anderer benannter Stopp erreicht ist.

**Warum:** Das Neun-Winkel-Rig verwandelt einen subjektiven 3D-Bau in einen wiederholbaren visuellen Test. Dieselben Ansichten nach jeder Änderung zu kritisieren, deckt Probleme auf, die ein einzelnes Hero-Rendering verbergen kann.

### 022 — War Loops: Frontend-Rekonstruktion

**Einsatz:** Nutze War Loops, wenn eine autorisierte Oberfläche aus einer URL oder einem Bild nachgebaut und nach Erscheinungsbild, Bewegung und responsivem Verhalten beurteilt werden muss.

**Prompt:**

> Richte War Loops auf eine autorisierte URL oder ein autorisiertes Bild. Erfasse sie mit einem echten Browser und erfasse Layout, Stile, Inhalt, Bewegung und responsives Verhalten. Baue eine statische Pencil-Spiegelung und eine bewegte Forge-Version. Vergleiche beide mit der Quelle in Desktop-, Tablet- und Mobil-Größen; repariere nur die schwächsten Treuesignale. Stoppe, wenn jeder Prüfschritt besteht, der Fortschritt stockt oder die Erfassung blockiert ist. Schließe ab mit den Builds, der Spezifikation, den Renderings, den Bewertungen und den verbleibenden Lücken.

**Prüfen:** Die Builds stimmen mit der Quelle über alle drei Treue-Achsen hinweg überein. Statisches Erscheinungsbild, erlebbare Bewegung und responsives Umfließen bestehen ihre Prüfschritte, oder der Lauf meldet Stagnation oder eine blockierte Erfassung.

**Schritte:**

1. Erfasse die Quelle mit einem echten Browser und extrahiere ihre Design-Spezifikation, Bewegung und Ziel-Viewports.
2. Baue die statische Pencil-Spiegelung und die bewegte Forge-Version aus der verifizierten Spezifikation.
3. Beurteile beide hinsichtlich statischem Design, erlebbarer Bewegung und responsivem Umfließen.
4. Repariere die schwächsten Signale, ohne neu zu bauen, was bereits übereinstimmt, und wiederhole bis zu einer finalen Treue-Entscheidung.

**Warum:** War Loops trennt das ruhende Erscheinungsbild einer Seite davon, wie sie sich bewegt und umfließt. Sein chirurgischer Kritiker zielt auf die schwächsten gemessenen Signale, ohne Bereiche aufzuwirbeln, die bereits übereinstimmen.

### 026 — Der Infinite-Clickbait-Thumbnail-Loop

**Einsatz:** Verwende dies, wenn ein Videothema und ein Asset-Set bereit sind, das Thumbnail aber vor der Produktion mehrere strukturierte Ideen- und Kritikrunden braucht.

**Prompt:**

> Erstelle für [Video] mithilfe von [freigegebenen Assets] zehn Thumbnail-Konzepte. Bewerte jedes in echten YouTube-Größen gegen [Inspirationskanal] hinsichtlich Klarheit, Neugier, emotionaler Zugkraft, Kontrast und Genauigkeit. Nimm die besten drei, verbessere bei jedem die schwächste Dimension und bewerte sie nach demselben Bewertungsraster neu. Iteriere das stärkste Konzept weiter, bis es [Qualitätsschwelle] erreicht oder [Budget] endet. Lehne alles ab, was das Video nicht einlösen kann. Gib den Sieger, zwei Zweitplatzierte, Vorschauen, finale Bewertungen und die Begründung zurück.

**Prüfen:** Ein genaues Thumbnail erreicht die fixe Qualitätsschwelle. Der Sieger schneidet unter denselben Bedingungen besser ab als die Alternativen, bleibt in realistischen Größen lesbar und stellt das Video genau dar.

**Schritte:**

1. Definiere das Videothema, die freigegebenen Assets, den Inspirationskanal, die Qualitätsschwelle, das Budget und das fünfteilige Bewertungsraster.
2. Erstelle zehn verschiedene Konzepte, prüfe sie in echten YouTube-Größen und bewerte jedes unter denselben Bedingungen.
3. Wähle die besten drei aus, verbessere bei jedem die schwächste Dimension und bewerte sie neu.
4. Stoppe an der Qualitätsgrenze oder am Budget, lehne irreführende Konzepte ab und gib den Sieger plus zwei Zweitplatzierte zurück.

**Warum:** Ein vielfältiges erstes Set schafft echte Optionen, während ein fixes Bewertungsraster spätere Runden vergleichbar macht. Genauigkeit zu bewerten verhindert, dass Neugier zu einem Versprechen wird, das das Video nicht halten kann.

### 036 — Der UI/UX-Score-Loop

**Einsatz:** Setze dies fuer eine echte Aufgabe wie Registrierung, Login, Onboarding, Checkout, Teilen oder das Erstellen und Bearbeiten eines Objekts ein, wenn sich das gesamte Erlebnis im Browser durchspielen und konsistent bewerten laesst.

**Prompt:**

> Verbessere [Nutzerflow, z. B. Registrierung] unter [URL], bis [Abschlusskriterium] erfuellt ist. Starte jeden Durchlauf in einem echten Browser aus frischem Zustand - kein gespeicherter Login, keine Cookies, keine Website-Daten. Erfasse aussagekraeftige Bildschirme in den vereinbarten Groessen und Modi, bewerte sie mit einer einzigen Checkliste und verbessere den schwaechsten sicheren Bereich. Durchlaufe den gesamten Flow erneut und behalte nur regressionsfreie Aenderungen. Stoppe bei Erfolg, bei zwei vollstaendigen Durchlaeufen ohne Fortschritt, bei blockiertem Zugang oder wenn eine Freigabe erforderlich ist. Gib Bewertungen, Screenshots, Aenderungen und Stoppgrund zurueck.

**Prüfen:** Die vollstaendige Nutzeraufgabe erzielt eine bessere Bewertung, ohne dass ein anderer wichtiger Bildschirm schlechter wird. Das abschliessende Dashboard zeigt fuer jede beibehaltene Verbesserung denselben Einstiegspunkt, frischen Browserzustand, dieselben Bildschirmgroessen, Modi, dasselbe Bewertungsraster, Screenshots, Score-Aenderungen und den Stoppgrund.

**Schritte:**

1. Waehle die Nutzeraufgabe, die Start-URL, das Erfolgsziel, den Browser, die Clean-Session-Regel, die Bildschirmgroessen, Hell- oder Dunkelmodi, die zu erfassenden Bildschirme und alles, was der Agent nicht aendern darf.
2. Erledige die Aufgabe einmal ohne Bearbeitung; erfasse normale Bildschirme sowie aussagekraeftige Lade-, Fehler-, Wiederherstellungs- und Erfolgszustaende und bewerte jeden mit demselben nutzerzentrierten Raster.
3. Verbessere den schwaechsten sicheren Bereich, starte eine neue saubere Browsersitzung und wiederhole die gesamte Aufgabe unter denselben Bedingungen, damit Vorher-Nachher-Bewertungen vergleichbar sind.
4. Behalte nur Aenderungen, die das Ziel verbessern, ohne einem anderen wichtigen Bildschirm zu schaden; stoppe bei Erfolg, bei zwei Durchlaeufen ohne Fortschritt, bei blockiertem Zugang oder wenn eine Freigabe erforderlich ist.

**Warum:** Eine saubere Browsersitzung legt Probleme offen, die gespeicherte Logins, Cookies und gemerkte Einstellungen verbergen koennen. Dieselbe Aufgabe mit demselben Bewertungsraster zu wiederholen, macht das Ergebnis vergleichbar, statt sich auf den vagen Eindruck zu verlassen, die Oberflaeche fuehle sich besser an.

### 038 — Der pixelsichere CSS-Trim-Loop

**Einsatz:** Setze dies ein, wenn die Styling-Dateien einer Website ungenutzte Deklarationen, duplizierte Regeln oder alte Overrides enthalten koennten und sich repraesentative Seiten und Interaktionen in wiederholbaren Screenshots erfassen lassen.

**Prompt:**

> Reduziere den CSS-Styling-Code, den [Website] an Nutzer ausliefert, ohne getestete Bildschirme zu veraendern. Erfasse zunaechst repraesentative Seiten, Groessen, Themes und Interaktionen und halte die Groesse des gebauten CSS fest. Behandle Coverage-Reports nur als Vorschlaege. Entferne eine Deklaration oder Regel, baue neu und fuehre Screenshots und Projektpruefungen erneut aus. Behalte es nur, wenn jeder Screenshot pixelidentisch ist und das gebaute CSS kleiner ist; andernfalls setze zurueck. Stoppe, wenn kein belegter Kandidat mehr bleibt, der Fortschritt stockt oder eine Freigabe erforderlich ist. Gib die Reduktion, Belege und ungetestete Zustaende zurueck.

**Prüfen:** Das ausgelieferte Stylesheet ist kleiner, waehrend jeder getestete Bildschirm pixelidentisch bleibt. Dieselben Projektpruefungen und Screenshots bestehen nach jeder beibehaltenen Loeschung, die an Nutzer gesendete gebaute CSS-Datei ist kleiner, und ungetestete Browser, Bildschirme oder Interaktionen bleiben explizite Risiken.

**Schritte:**

1. Liste vor dem Loeschen von Styling-Code repraesentative Seiten, Bildschirmgroessen, Hell- und Dunkelmodi, bedingte Inhalte, Hover- und Tastaturfokus-Zustaende und andere wichtige Varianten auf; erfasse Screenshots und halte die endgueltige Groesse des gebauten CSS fest.
2. Nutze einen CSS-Coverage-Report, um moeglicherweise ungenutzte Deklarationen oder Regeln vorzuschlagen, und entferne dann einen Kandidaten aus der wartbaren Quelldatei.
3. Baue neu, fuehre Projektpruefungen aus und erstelle jeden Screenshot neu; behalte die Loeschung nur, wenn alle Bilder pixelidentisch sind und das gebaute CSS kleiner ist, andernfalls setze sie zurueck.
4. Wiederhole, bis kein gut belegter Kandidat mehr bleibt, wiederholte Versuche nichts sparen, die Screenshots das betroffene Verhalten nicht abdecken koennen oder eine Freigabe erforderlich ist.

**Warum:** Vor der Bereinigung aufgenommene Screenshots bewahren das aktuelle Erscheinungsbild als Massstab. Der exakte Bildvergleich und eine Loeschung pro Runde erfassen visuelle Aenderungen, die ein automatisierter Coverage-Report nicht verstehen kann, einschliesslich Regeln, die nur wegen ihrer Reihenfolge wichtig sind.

### 040 — Der Barrierefreiheits-Reparatur-Loop

**Einsatz:** Setze dies ein, wenn eine Website oder App ein definiertes Barrierefreiheitsziel hat und du die relevanten Seiten, Komponenten oder Aufgaben wiederholt fuer Menschen testen kannst, die Tastaturen, Screenreader, Zoom oder andere Zugangsmethoden nutzen.

**Prompt:**

> Pruefe [Umfang] gegen [Barrierefreiheitsstandard, z. B. WCAG 2.2 AA] mit automatisierten Scans und verfuegbaren manuellen Tests fuer Tastatur, Screenreader und weitere. Bestaetige jedes Problem, ordne es nach Schaden und behebe den Blocker mit der groessten Wirkung. Fuehre dieselben Pruefungen, die betroffene Aufgabe und Regressionstests erneut aus. Behalte nur verifizierte Behebungen. Stoppe, wenn kein Blocker mehr bleibt, der Fortschritt stockt, eine Verifikation nicht moeglich ist oder eine Freigabe erforderlich ist. Bringe niemals eine Pruefung zum Schweigen und schwaeche das Ziel nicht. Gib Probleme, Behebungen, Belege, Ausnahmen und ungetestete Bedarfe zurueck.

**Prüfen:** In den vereinbarten Seiten, Komponenten oder Nutzeraufgaben bleibt keine bestaetigte Barriere der Barrierefreiheit bestehen. Dieselben automatisierten Scans, verfuegbaren manuellen Pruefungen, die betroffene Nutzeraufgabe und die Regressionstests bestehen nach jeder beibehaltenen Behebung, ohne den gewaehlten Barrierefreiheitsstandard zu senken.

**Schritte:**

1. Waehle die zu testenden Seiten, Komponenten und Nutzeraufgaben; benenne den Barrierefreiheitsstandard, z. B. WCAG 2.2 AA; und liste die tatsaechlich verfuegbaren automatisierten Scans und manuellen Pruefungen auf.
2. Fuehre den Ausgangswert aus, reproduziere jeden Befund, statt einer Tool-Warnung allein zu vertrauen, und ordne bestaetigte Barrieren nach der Zahl der betroffenen Menschen und dem Grad ihrer Blockierung.
3. Behebe die schaedlichste Barriere mit der kleinsten zugrunde liegenden Aenderung und wiederhole dann denselben Scan, dieselbe manuelle Pruefung, Nutzeraufgabe und die relevanten Regressionstests.
4. Behalte nur verifizierte Behebungen und wiederhole, bis keine bestaetigte Barriere mehr bleibt oder der Fortschritt stockt, Belege nicht erhoben werden koennen, die Arbeit blockiert ist oder eine Freigabe erforderlich ist.

**Warum:** Ein fester Umfang und wiederholte Pruefungen halten die Barrierefreiheitsarbeit an echte Menschen und reproduzierbare Belege gebunden, statt an eine endlose Score-Jagd. Die schaedlichste bestaetigte Barriere zuerst zu beheben lenkt den Aufwand zu den Nutzern, die am staerksten blockiert sind.
