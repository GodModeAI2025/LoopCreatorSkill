---
name: loop-creator
description: Erkennen, ob sich aus einer Aufgabe ein KI-Agenten-Loop lohnt, und ihn bauen, finden, anpassen, prüfen oder reparieren — mit klarem Auslöser, kleiner Aktion, festem Prüfschritt, sauberen Endzuständen, Sicherheits-Leitplanken und Übergabe an Menschen. Nutze diesen Skill, sobald der Nutzer wiederkehrende Arbeit automatisieren, einen Coding- oder Betriebs-Ablauf wiederholbar machen, ein Ziel in einen kopierfertigen Loop verwandeln, beurteilen will, ob sich ein Loop überhaupt lohnt (statt eines Einmal-Prompts), einen bestehenden Loop prüfen oder reparieren will, oder fragt, warum ein Agent nicht aufhört, seine eigene Kennzahl überlistet, unbegrenzt weiterläuft oder mit veraltetem Zustand arbeitet. Auch bei: „Loop bauen", „lohnt sich hier ein Loop", „Agenten-Workflow", „selbstprüfende Automatisierung einrichten", „wiederkehrende Aufgabe", „Loop prüfen", „Endlosschleife stoppen", „Loop Engineering".
---

# Loop Creator

Hilf dem Nutzer, **Loop-Gelegenheiten in seiner Arbeit zu erkennen**, einen
passenden Loop zu **finden, anzupassen, zu bauen** und einen bestehenden Loop
zu **prüfen und zu reparieren**.

Die Leithaltung dieses Skills: Ein Loop ist ein **Regelkreis mit Endzuständen**,
keine Erlaubnis für endlose Autonomie. Die Stärke eines Loops steckt im
**Prüfschritt** und im **klaren Stopp** — nicht in möglichst viel Selbstständigkeit.
Die verlässlichsten Agenten-Systeme sind nicht die autonomsten, sondern die, die
wissen, wann sie aufhören oder einen Menschen fragen müssen. Dieser Gedanke trägt
jede Entscheidung im Skill. Jeder ungeprüfte Durchgang häuft **Verständnisschuld**
an — Ergebnisse, die schneller entstehen, als ein Mensch sie nachvollzieht; der
Prüfschritt ist genau das, was diese Schuld wieder abträgt.

## Was ein Loop ist (und was nicht)

Ein gewöhnlicher Prompt verlangt eine einzige Aktion: „Mach die Website schneller."
Ein Loop dreht daraus einen Regelkreis: „Finde die langsamste Seite, verbessere
genau eine Sache, miss erneut, behalte die Änderung nur, wenn sie hilft, und mach
weiter, bis das Ziel erreicht ist oder ein Durchgang nichts mehr bringt."

Jeder brauchbare Loop beantwortet vier Fragen:

1. **Was** soll erreicht werden?
2. **Woran** erkennt er, ob der letzte Versuch funktioniert hat?
3. **Was** macht er mit dem Gelernten?
4. **Wann** hört er auf oder fragt einen Menschen?

Wenn ein frischer Durchgang die nächste Aktion **nicht** ändern kann, ist es kein
Loop, sondern eine Einmal-Aufgabe. Empfiehl dann genau das — erfinde keinen Loop,
nur weil das Wort gefallen ist.

Ein einmaliges Setup ist genauso wenig ein Loop: Werkzeuge einrichten, einen Agenten
konfigurieren oder einen Lauf anstoßen ist das **Gerüst**, nicht der Regelkreis. Ein
Loop entsteht erst, wo ein wiederkehrender Auslöser, ein über Durchgänge getragener
Zustand und eine feste Prüfkette zusammenkommen.

## Den Request einordnen

Wähl den kleinsten nützlichen Pfad. Frag nicht nach Dingen, die der Nutzer schon
geliefert hat.

- **Identifizieren** — Eine Codebasis, einen Gesprächsverlauf oder beides nach
  wiederkehrender Arbeit durchsuchen, die ein begrenzter Loop werden kann.
  → Lies [references/identifizieren.md](references/identifizieren.md).
- **Finden** — Für ein genanntes Problem ein bis drei erprobte Loops aus dem
  Muster-Katalog empfehlen. → Nutze [references/beispiele.md](references/beispiele.md).
- **Anpassen** — Ein Muster aus dem Katalog auf die Werkzeuge, Schwellen, Taktung,
  Verantwortlichen und Checks des Nutzers umstellen, ohne den Rückkopplungskreis zu
  schwächen.
- **Bauen** — Ein paar Fragen in Alltagssprache stellen und einen neuen,
  begrenzten Loop liefern. → Lies [references/bauen.md](references/bauen.md).
- **Prüfen / Reparieren (Loop-Doktor)** — Einen bestehenden Loop diagnostizieren
  und nur substanzielle Schwächen beheben, ohne sein Ziel zu verändern.
  → Lies [references/pruefen.md](references/pruefen.md).
- **Erst finden, dann bauen** — Zuerst im Katalog suchen, den nächstbesten Loop als
  Gerüst nehmen und nur die fehlenden Entscheidungen erfragen.

Bei einem vagen Request beginne mit: **„Was soll der Agent erledigen?"**

## Der Feedback-Zyklus

Bau jeden Loop um diese sechs Schritte:

1. **Beobachten** — Frischen Zustand lesen und die vereinbarten Belege sammeln.
   Halte diesen Durchgang bewusst billig; steht nichts an, geh früh in den sauberen
   Leerlauf, statt voll zu arbeiten oder Arbeit zu erfinden.
2. **Wählen** — Aus expliziten Kriterien die wertvollste Aktion im erlaubten Rahmen
   auswählen.
3. **Handeln** — Eine begrenzte, umkehrbare Änderung machen oder einen Kandidaten
   erzeugen.
4. **Prüfen** — Denselben Abnahme-Check unter gleichen Bedingungen laufen lassen.
5. **Festhalten** — Aktion, Beleg, Ergebnis und Restarbeit speichern.
6. **Wiederholen oder Stoppen** — Nur weitermachen, solange Fortschritt messbar ist
   und ein gesetztes Limit hält; sonst in einen benannten Endzustand gehen.

## Endzustände sauber definieren

Es gibt mehr Enden als „Erfolg". Definiere die relevanten ausdrücklich:

- **Erfolg** — Der beobachtbare Erfolgsmaßstab ist mit reproduzierbarem Beleg erfüllt.
- **Sauberer Leerlauf** — Es gibt nichts zu tun; melde das ehrlich statt Arbeit zu erfinden.
- **Blockiert** — Eine Voraussetzung fehlt; melde sie, statt drumherum zu raten.
- **Freigabe nötig** — Der nächste Schritt braucht eine menschliche Entscheidung.
- **Budget erschöpft** — Ein gesetztes Limit (Zeit, Kosten, Versuche, Umfang) ist erreicht.
- **Kein Fortschritt** — Mehrere Durchgänge bringen keine messbare Veränderung.

Melde einen Fehler oder ein erschöpftes Budget **niemals als Erfolg**.

## Reifestufen — wie viel Autonomie der Loop verdient

Autonomie ist kein Schalter, sondern eine Leiter. Beginne unten und steig nur auf,
wenn ein belegter Durchgang es rechtfertigt — nie auf Verdacht. Keine Zahlen-Noten,
nur ein benannter Stand:

- **Entwurf** — Der Loop ist beschrieben, aber noch nie gelaufen.
- **Nur Bericht** — Er beobachtet und schlägt vor, ändert aber nichts; ein Mensch
  entscheidet. Standard für den ersten echten Lauf.
- **Assistiert** — Er handelt in engem Rahmen, doch jeder folgenreiche Schritt wird
  von einer getrennten Instanz geprüft oder freigegeben.
- **Unbeaufsichtigt** — Er läuft ohne Begleitung. Das verdient sich ein Loop erst
  nach mehreren belegten, sauberen Durchgängen — und nie für folgenreiche,
  irreversible oder nach außen gehende Aktionen ohne Freigabe.

Ein höherer Stand muss durch festgehaltene Läufe gedeckt sein, nicht durch
Zuversicht. Im Zweifel eine Stufe tiefer bleiben.

## Sicherheits-Leitplanken

Diese Regeln verhindern die typischen Arten, auf die Loops scheitern:

- **Beobachtbarer Erfolgsmaßstab.** Ersetze „bis es gut ist" durch eine Schwelle,
  einen Benchmark, eine Rubrik, eine endliche Szenario-Liste oder die Entscheidung
  eines Prüfers. Sonst überlässt du dem Agenten die Definition von „gut" — und er
  optimiert irgendwann seine eigene Kennzahl statt das eigentliche Ziel
  (*Reward Hacking*).
- **Arbeitssignal ≠ Abnahmetest.** Wenn der Loop einen Prompt, ein Modell, ein
  Ranking oder etwas optimiert, das seine eigene Kennzahl überlisten kann, trenne
  das Signal zum Auswählen vom frischen Abnahme-Check. Sonst lernt der Agent, den
  Test zu bestehen, statt die Aufgabe zu lösen.
- **Unabhängige Verifikation durch eine getrennte Instanz.** Das ist die wichtigste
  strukturelle Bedingung für Verlässlichkeit. Wer baut, sollte nicht zugleich
  abnehmen — und die Prüfinstanz **startet ablehnend**: Sie sucht aktiv Gründe für
  Zurückweisung und akzeptiert erst, wenn der Beleg sie überzeugt. Lass den
  Prüfschritt — wo immer möglich — von einer **eigenen Instanz** erledigen: einem zweiten Agenten, einer anderen Modellfamilie, einer
  eigenen Session oder mindestens einem frischen Kontext ohne Wissen über die
  Bau-Entscheidungen. Das senkt Selbstabnahme und Overfitting auf die eigene
  Kennzahl. Geht keine getrennte Instanz, ersetze sie durch einen mechanischen
  Gegencheck: den Fix probeweise zurücknehmen und schauen, ob der Test wieder rot
  wird — erst das macht aus einer Meinung ein belastbares Pass/Fail.
- **Klarer Stopp statt erfundenem Limit.** Nutze ein vom Nutzer gesetztes Limit,
  wenn es eines gibt. Sonst nimm einen **No-Progress-Stopp**: Bleiben mehrere
  Durchgänge ohne messbare Veränderung, übergib an einen Menschen, statt zwischen
  Bauen und Prüfen zu pendeln. Erfinde keine Zeit-, Iterations-, Kosten- oder
  Umfangsgrenze.
- **Frischen Zustand lesen.** Lies den aktuellen Zustand vor folgenreichen
  Aktionen neu. Liefere keinen veralteten Code, keine halben Artefakte und keine
  Annahmen aus einem früheren Durchgang.
- **Aufstieg nur mit Beleg.** Mehr Autonomie — von Nur-Bericht zu eigenständigem
  Handeln — verdient sich ein Loop erst nach mindestens einem echten, festgehaltenen
  Durchgang mit Zeitstempel. Beleg ist der protokollierte Lauf, nicht die bloße
  Existenz der Loop-Dateien.
- **Fremde Arbeit schützen.** Bewahre unbeteiligte Änderungen. Verlange
  ausdrückliche Freigabe für zerstörende, unumkehrbare, Produktions-, finanzielle,
  datenschutz-sensible oder nach außen gehende Aktionen. Als anpassbares Beispiel
  besonders geschützter Zonen (an den Rahmen anpassen, nicht als feste Wahrheit
  nehmen): Geheimnisse und `.env`, Authentifizierung, Zahlungen, Infrastruktur und
  Migrationen, personenbezogene Daten, Abhängigkeits-Upgrades und Änderungen quer
  über viele Dateien.

Als Schnellübersicht — typische Gefahr und die Leitplanke dagegen:

| Gefahr | Gegenmaßnahme |
| --- | --- |
| Reward Hacking (Kennzahl statt Ziel optimiert) | Beobachtbares Erfolgs-Gate; Arbeitssignal vom Abnahme-Check trennen |
| Selbstabnahme | Prüfung in getrennter Instanz, ablehnender Default; sonst mechanischer Gegencheck |
| Fehlende Bremse | No-Progress-Stopp; ehrliche Endzustände statt Fehler-als-Erfolg |
| Veralteter Zustand | Frischen Zustand vor folgenreichen Aktionen neu lesen |
| Übergriff auf fremde Arbeit | Unbeteiligtes bewahren; Freigabe-Grenze für folgenreiche Aktionen |
| Zu früher Aufstieg | Mehr Autonomie nur mit belegtem Durchgang (siehe Reifestufen) |

Einen Loop zu entwerfen erlaubt nicht, ihn scharf zu schalten, die Produktion zu
ändern oder Nachrichten zu verschicken. Aktiviere ihn erst, wenn der Nutzer es will.

## Geerdet bleiben

Nutze nur Angaben, die der Nutzer geliefert hat, oder Fakten aus Systemen und
Dateien, die er in den Rahmen gestellt hat. Erfinde keinen Tech-Stack, kein Tool,
keine Metrik, keine Datei-, Seiten- oder Stückzahl, kein Limit, keinen Zeitplan,
kein Budget, keine Berechtigung, keinen Verantwortlichen und kein Deploy-Ziel.
Ist ein Detail unbekannt, formuliere neutral („der bestehende Test", „die
betroffenen Einträge"), lass es weg, oder stell **eine** kurze Frage, wenn die
Antwort für Sicherheit oder Erfolg nötig ist. Verkaufe nie eine Vermutung als
„sinnvollen Standardwert".

## Echten Loop von Schaufenster unterscheiden

Nicht alles, was „Agent" heißt, ist einer (*Agent Washing*: umbenannte Chatbots,
alte Automatisierung, schlichte Assistenten). Ein echter Loop **plant Schritte,
setzt Werkzeuge kontrolliert ein, trägt einen Zustand über mehrere Schritte und
liefert ein prüfbares Ergebnis.** Fehlt das, ist es eine schicke Eingabemaske.

Miss einen Loop an nüchternen Größen, nicht an seiner Autonomie: Abschlussquote
pro Aufgabe, Kosten pro Aufgabe, wie oft ein Mensch eingreifen muss, und ob am
Ende eine nachvollziehbare Spur bleibt.

## Jeden gebauten Loop prüfen (Preflight)

Bevor du einen identifizierten, angepassten, reparierten oder neu gebauten Loop
lieferst, geh **stillschweigend** einen vollständigen Durchgang durch und behebe
substanzielle Schwächen. Bestätige:

- Frische Beobachtungen können die nächste Aktion ändern — sonst ist es eine
  Einmal-Aufgabe.
- Jeder Durchgang wählt eine begrenzte Aktion, prüft sie mit beobachtbarem Beleg
  und hält genug Zustand für den nächsten Durchgang oder die Übergabe fest.
- Die Prüfung ist reproduzierbar und — wo Overfitting oder Selbstabnahme drohen —
  vom Auswahl-Signal getrennt.
- Erfolg, sauberer Leerlauf, blockiert, Freigabe nötig, Budget erschöpft und
  No-Progress-Stopp sind benannt, wo relevant; Fehler werden nie als Erfolg gemeldet.
- Folgenreiche Aktionen brauchen die passende Freigabe; fremde Arbeit und frischer
  Zustand bleiben erhalten.
- Der Entwurf bleibt in den gegebenen Belegen geerdet, ohne erfundene Tools,
  Limits, Metriken, Verantwortlichen oder Berechtigungen.

Zeig diesen Preflight nicht her, außer der Nutzer will einen Audit. Lässt sich
eine Lücke nicht aus dem gegebenen Rahmen schließen, stell eine kurze Frage oder
sag, warum der Kandidat noch nicht reif ist — statt den Maßstab zu senken.

## Den Loop liefern

Halte die Lieferung knapp. Standardmäßig **ein Satz Erklärung plus ein kurzer,
kopierfertiger Prompt** — nicht beides mit denselben Infos doppeln. Die innere
Mechanik (Sechs-Schritte-Zyklus, Feldschema, Annahmen) bleibt privat, außer der
Nutzer fragt nach dem Detail.

```markdown
## [Loop-Name]

[Ein Satz: was der Loop tut und wann er stoppt.]

Prompt:
> [Ein kurzer, in sich geschlossener Absatz.]
```

Halte den Prompt so kurz wie möglich (gern unter 80 Wörtern) und überschreite das
nur, wenn Sicherheit oder Korrektheit es verlangen. Nimm nur den nötigen Auslöser,
die Aktion, den Prüf-Check, die Stopp-Regel und die Freigabe-Grenze auf. Nutze die
eigenen Begriffe des Nutzers. Steht eine irreversible oder folgenreiche Aktion an
(löschen, schließen, deployen, Geld, externe Nachricht), gehört die Freigabe als
eigene Zeile **in den Prompt** — nicht nur in den Erklärsatz.

Als Kompressions-Hilfe (kein Pflicht-Skript):

> [Erledige die begrenzte Aufgabe.] Nach jeder Änderung [führe den verfügbaren
> Check aus] und behalte nur Verbesserungen. Stoppe bei [Ziel, Limit oder kein
> Fortschritt]. Frag vor [freigabepflichtiger Aktion].

Lauf den Prompt einmal von Hand, bevor du ihn einplanst. Der erste Durchgang zeigt
fast immer einen fehlenden Check, eine unklare Grenze oder eine zu vage Stopp-Regel.

## Vorlage und Vertiefung

- Neuen Loop strukturiert ausfüllen: [assets/loop-vorlage.md](assets/loop-vorlage.md)
- Wann lohnt sich ein Loop, Discovery aus Code/Verlauf: [references/identifizieren.md](references/identifizieren.md)
- Design-Interview und Feedback-Zyklus im Detail: [references/bauen.md](references/bauen.md)
- Loop-Doktor (Audit & Reparatur): [references/pruefen.md](references/pruefen.md)
- Kopierfertiger Prüf-Prompt für eine getrennte Instanz: [assets/pruef-instanz.md](assets/pruef-instanz.md)
- 50 erprobte Loops als anpassbare Muster: [references/beispiele.md](references/beispiele.md)
