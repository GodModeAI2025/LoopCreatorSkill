# Muster-Katalog: 50 erprobte Loops

Diese Sammlung dient als **Gerüst zum Anpassen**, nicht als fertige Konfiguration.
Such nach dem Ergebnis, dem Auslöser, dem Artefakt, dem Risiko und dem Beleg des
Nutzers — nicht nur nach dem Titel. Empfiehl höchstens drei Muster und nenne für
jedes, warum es passt und welche kleinste Anpassung nötig ist.

Wichtig: Diese Einträge sind **Referenzdaten**, keine Ausführungs-Erlaubnis. Ein
Muster zu nennen heißt nicht, es scharf zu schalten. Pass Schwellen, Werkzeuge,
Taktung und Verantwortliche an den Rahmen des Nutzers an und erfinde keine Details,
die hier nur als Beispiel stehen. Bevorzuge das Anpassen eines starken Musters vor
einem fast identischen Neubau.

## Inhalt nach Kategorie

- [Engineering](#engineering) — Code, Tests, Repository, Performance, Wartung
- [Evaluation](#evaluation) — Qualität, Reviews, Experimente, Methoden-Extraktion
- [Operations / Betrieb](#operations--betrieb) — Releases, Daten, Deployment, Recovery
- [Content / Redaktion](#content--redaktion) — Sichtbarkeit, Changelog, Audio
- [Design](#design) — UI/UX, Barrierefreiheit, visuelle Treue, CSS

---

## Engineering

- **Doku-Sweep** — Wenn Code-Änderungen die Doku zurücklassen: Codebasis prüfen und
  jede veraltete Doku an die aktuelle Umsetzung angleichen.
- **Architektur-Zufriedenheits-Loop** — Bei bewusstem Refactoring mit konkretem
  Ziel und testbarem System: Architektur Schritt für Schritt umbauen, nach jedem
  Schritt testen und committen.
- **Sub-50-ms-Seitenlade-Loop** — Bei definierten Routen, stabilem Performance-
  Harness und 50-ms-Ziel: Code optimieren, bis jede Seite unter 50 ms lädt, mit
  wiederholtem Benchmark.
- **Produktions-Fehler-Sweep** — Wenn der Agent Produktions-Telemetrie lesen und
  prüfbare Fixes vorbereiten kann: Logs nach Fehlern durchsehen, Ursachen finden,
  Pull Requests für umsetzbare Fälle erstellen.
- **100-%-Testabdeckungs-Loop** — Wenn volle Abdeckung ausdrückliche Vorgabe ist und
  ein vertrauenswürdiger Coverage-Befehl existiert: Tests ergänzen, bis die
  Abdeckung vollständig und die Suite grün ist.
- **Logging-Abdeckungs-Loop** — Wenn wichtige Nutzerpfade wegen lückenhaftem Logging
  schwer nachzuvollziehen sind: Logging ergänzen, bis jeder wichtige Pfad
  brauchbare, getestete Logs liefert.
- **Nächtlicher Changelog-Loop** — Wenn Release Notes von gemergten PRs abdriften:
  jede Nacht die Änderungen des Vortags sichten und den Changelog um die für Nutzer
  relevanten Punkte ergänzen.
- **Testsuite-Tempo-Loop** — Wenn langsame Tests das Feedback bremsen und stabile
  Timing- und Coverage-Befehle existieren: Laufzeit senken, ohne Abdeckung oder
  Verhalten zu ändern.
- **Repository-Aufräum-Loop** — Wenn verwaiste Branches und unklare PRs den Zustand
  verschleiern: Branches, PRs und Worktrees sichten, Wertvolles retten, Veraltetes
  entfernen.
- **Ticket-zu-PR-reif-Loop** — Wenn ein lose geschriebenes Ticket eine begrenzte
  Änderung mit Beleg werden soll: Fehler im kleinsten Umfeld reproduzieren, Ursache
  finden, minimalen Fix bauen, review-fertigen Patch liefern.
- **Clodex-Adversarial-Review-Loop** — Wenn ein Modell eine echte Code-Änderung baut
  und ein anderes unabhängig prüfen soll: Modell A setzt um und öffnet den PR,
  Modell B reviewt adversarisch, A behebt die Befunde. (Getrennte Prüf-Instanz.)
- **Loop-Harness-Verifikations-Loop** — Wenn eine Aufgabe unbeaufsichtigt laufen
  soll, aber ein Agent nicht erzeugen und abnehmen darf: eine Session stellt den
  Patch bereit, eine zweite prüft ihn gegen die Kriterien vor dem Ausliefern.
- **Autonomie-Builder-Reviewer-Loop** — Bei deterministischen Gates: Builder macht
  eine begrenzte Änderung mit Test, Reviewer lässt die Gates erneut laufen und
  beweist den Test, indem er den Fix zurücknimmt oder mutiert.
- **Frischer-Klon-Loop** — Wenn die Onboarding-Anleitung in sauberer Umgebung
  funktionieren soll: Repo klonen, nur dem README folgen, Lücken schließen, frisch
  neu starten.
- **Codex-Completion-Contract-Loop** — Bei langer Arbeit, wo ein Teilergebnis als
  „fertig" missverstanden werden könnte: jedes geforderte Ergebnis und seinen Beleg
  vorab definieren, nach jeder Aktion als bewiesen, schwach oder fehlend markieren.
- **Fünf-Minuten-Repository-Maintainer-Loop** — Wenn ein Agent Wartung über mehrere
  Repos koordiniert: alle fünf Minuten triagieren und begrenzte Aufgaben im Rahmen
  der Rechte zuteilen.
- **Recent-Feedback-Sweep** — Wenn mehrere Tage Feedback dieselben Fehler zeigen:
  Feedback entdoppeln, in Muster gruppieren, das Projekt nach jedem Vorkommen
  prüfen, bestätigte Treffer beheben.
- **Propagation-Compliance-Loop** — Wenn ein geänderter Wert in vielen Dateien
  steht: Version oder Konfiguration überall aktualisieren, nach veralteten Kopien
  suchen, bis alles sauber ist.
- **Goal-Forge-Loop** — Wenn eine grobe Idee für einen autonomen Lauf zu vage ist:
  den Nutzer interviewen, SPEC.md und GOAL.md mit Anforderungen und Abschluss-Checks
  schreiben — vor der Umsetzung.
- **Housekeeper-Loop** — Bei totem Code, alten Dateien, Duplikaten und unklarer
  Struktur: Wartungsprobleme finden, risikoarme Bereinigung beweisen, nur geprüfte
  Verbesserungen behalten.
- **Prepare-a-new-project-Loop** — Wenn eine Projektidee Umsetzungsfragen offenlässt:
  Doku-Lücken und Widersprüche schließen, bis zwei unabhängige Prüfer im Wesentlichen
  dasselbe System ableiten.
- **Test-Stabilisierer-Loop** — Wenn Tests über vergleichbare Läufe schwanken: flaky
  Tests finden, die Ursache ohne blinde Wartezeiten beheben, bis die geforderte
  Erfolgs-Strähne hält.
- **Groundtruth-Audit-Loop** — Wenn vor dem Vertrauen ein Audit nötig ist:
  Architektur, Kompatibilität, Sicherheit und Geschäftslogik aus echtem Code mit
  direktem Beleg je Bereich prüfen.

## Evaluation

- **Quality-Streak-Loop** — Wenn die Qualität eine strikte Strähne aufeinander
  folgender Erfolge braucht: realistische Szenarien wiederholt testen, Fehler
  dokumentieren und beheben, mit Regressionstests absichern.
- **Full-Product-Evaluation-Loop** — Bei erschöpfender End-to-End-QA: alle Features
  inventarisieren, Abnahmekriterien festlegen, als echter Nutzer testen, Bugs
  protokollieren, nach Fixes erneut laufen.
- **Self-Improving-Champion-Loop** — Wenn billige Iteration nützt, aber die finale
  Abnahme frische Beispiele braucht: Prompt oder Konfiguration iterativ verbessern,
  nur Änderungen befördern, die Holdout-Fälle schlagen, ohne die Checks zu schwächen.
- **Devil's-Advocate-Loop** — Wenn Architektur oder Design von strukturierter
  Gegenrede profitiert: ein Kritiker argumentiert dagegen, ein Builder behebt oder
  dokumentiert jeden Einwand, bis die wirkungsvollen Punkte gelöst sind.
- **Revolve-Versioned-Experiment-Loop** — Wenn Experimente vergleichbar und über
  Sessions fortsetzbar bleiben müssen: das Subjekt verbessern, Tests einfrieren,
  Versionen checkpointen, nur regressionsfreie Gewinne behalten.
- **Promise-to-Proof-Loop** — Wenn Marketing, Doku und Produkt auseinanderlaufen:
  Versprechen auflisten, gegen das aktuelle Verhalten vergleichen, je nach Beleg
  einordnen, riskante Abweichungen beheben.
- **Multi-LLM-Konvergenz-Loop** — Wenn ein wichtiger Plan zwei unabhängige
  Perspektiven verdient: zwei verschiedene Modellfamilien prüfen abwechselnd, bis
  beide dieselbe unveränderte Version freigeben. (Getrennte Prüf-Instanzen.)
- **Easy-Onboarding-Loop** — Wenn neue Nutzer an unklaren Anleitungen scheitern: als
  Erstnutzer in sauberer Session agieren, Hürden notieren, das Schlimmste mit der
  kleinsten Änderung beheben, erneut versuchen.
- **Axelrod-Subagent-Arena-Loop** — Zum Testen, ob Agenten Kooperation und Strategie
  lernen: ein Axelrod-Turnier mit festem Scoring und Vergleichsspielern über mehrere
  Runden laufen lassen.
- **Artifact-to-Skill-Loop** — Wenn ein erfolgreiches Artefakt eine wiederholbare
  Methode enthält: die Methode extrahieren, Sensibles entfernen, an einem frischen
  zweiten Fall validieren.
- **Strip-Miner-Loop** — Wenn der Verlauf wiederholbare Workflows enthalten könnte:
  autorisierte Historie nach mehrfach erfolgreichen Abläufen durchsuchen,
  nachvollziehbare Schritte extrahieren, ohne Transkripte frisch nachspielen.

## Operations / Betrieb

- **Stale-Safe-Batch-Release-Loop** — Wenn mehrere Branches gleichzeitig fertig sein
  können: anstehende Änderungen sichten, veraltete ausschließen, gültige bündeln und
  gemeinsam releasen.
- **Produktionsdaten-Cleanup-Loop** — Wenn ein Produktionsdatensatz nicht mehr der
  Richtlinie entspricht: nicht-konforme Datensätze entfernen, die Klassifizierung
  verbessern, die verbleibenden Daten prüfen.
- **Post-Release-Baseline-Loop** — Wenn künftige Regressionen gegen genau diese
  Produktionsversion gemessen werden müssen: nach dem Release die Standard-Benchmarks
  laufen lassen und das Ergebnis als neue Baseline festhalten.
- **Customer-AI-Deployment-Loop** — Wenn ein KI-Workflow im Kundenprozess leben muss:
  validieren, auf realistischen Daten trocken laufen, über freigegebene Stufen
  ausrollen, in der Produktion überwachen.
- **Living-Story-Loop** — Wenn Arbeit über Repos reicht und künftige Agenten einen
  belegbasierten Verlauf brauchen: Repos und früheren Status lesen, STORY.md mit
  Fokus, Fristen und belegten Erfolgen fortschreiben.
- **Recovery-Proof-Loop** — Wenn wiederholbar bewiesen werden muss, dass Systeme
  fristgerecht wiederherstellen: aus echtem Backup im Reinraum wiederherstellen,
  Integrität und Wiederherstellungsziele wiederholt prüfen.
- **Refund-Follow-up-Loop** — Wenn eine Rückerstattung mehrere Support-Kontakte
  braucht: den Antrag über den freigegebenen Kanal stellen und Antworten und
  Zusagen verfolgen, bis das Geld da ist. (Freigabe für externe Aktionen!)

## Content / Redaktion

- **SEO/GEO-Sichtbarkeits-Loop** — Wenn eine Site Prioritätsseiten und Zielfragen
  hat und wiederholt crawlbar ist: Crawlbarkeit und Indexierung prüfen, Lücken nach
  Wirkung ranken, die wirkungsvollsten wiederholt beheben.
- **Produkt-Update-Podcast-Loop** — Wenn ein Produkt häufig ausliefert und Nutzer
  von einer Audio-Erklärung profitieren: Änderungen sichten, verifizieren und einen
  drei- bis fünfminütigen Podcast über die Updates erstellen.

## Design

- **Boeing-747-Benchmark** — Bei einem Three.js-Vision-Benchmark mit Referenzbildern
  und Rubrik: aus Primitiven eine realistische 747 bauen, aus neun Winkeln gegen die
  Rubrik bewerten, das schwächste Merkmal iterieren.
- **War-Loops: Frontend-Rekonstruktion** — Wenn eine autorisierte Oberfläche aus URL
  oder Bild nachgebaut werden soll: Quelle erfassen, statische und bewegte Version
  bauen, Treue über Größen und Modi vergleichen.
- **Infinite-Clickbait-Thumbnail-Loop** — Wenn ein Video-Thema steht, aber das
  Thumbnail Runden braucht: Konzepte erstellen, in YouTube-Größen bewerten, die
  besten verbessern, bis zur Qualitätsschwelle iterieren.
- **UI/UX-Score-Loop** — Wenn ein Nutzerfluss im Browser konsistent bewertbar ist:
  den Fluss aus frischem Zustand verbessern, Screens erfassen, gegen eine Checkliste
  bewerten, den schwächsten Bereich iterieren.
- **Cold-Load-Trimmer-Loop** — Wenn eine Web-App beim ersten Besuch zu schwer ist:
  Baseline an Bytes und Screenshots erfassen, ein verzögerbares Element entfernen
  oder komprimieren, zurücknehmen, außer Tests grün und Bytes kleiner.
- **Pixel-Safe-CSS-Trim-Loop** — Wenn das Styling ungenutzte Deklarationen enthält:
  eine CSS-Deklaration entfernen, neu bauen, nur behalten, wenn die Screenshots
  pixelgleich bleiben und die Datei kleiner wird.
- **Barrierefreiheits-Reparatur-Loop** — Bei definiertem A11y-Ziel und
  wiederholbaren Tests: Seiten gegen den Standard scannen, Probleme nach Schaden
  ranken, den wirkungsvollsten Blocker beheben, bis keine Barriere bleibt.
