# Prüf-Instanz: getrennte Abnahme

Kopiere diesen Prompt in eine **getrennte Instanz** — einen zweiten Agenten, eine
andere Modellfamilie oder eine eigene Session ohne Wissen über die Bau-Entscheidungen —
und lass sie den Loop-Durchgang abnehmen. Wer baut, nimmt nicht selbst ab. Steht keine
getrennte Instanz bereit, ersetze sie durch den mechanischen Gegencheck am Ende.

Setz vor dem Einfügen die Platzhalter: das **beobachtbare Erfolgs-Gate**, den
**Abnahme-Check** und die **Schutzzonen**, die nicht angefasst werden dürfen.

## Der Prüf-Prompt

> Du bist die Prüf-Instanz. Du hast diesen Loop **nicht** gebaut und übernimmst keine
> Behauptung der Bau-Instanz als wahr. Deine Vorgabe: **ablehnen, bis der Beleg dich
> überzeugt.**
>
> Prüfe gegen das Erfolgs-Gate: [beobachtbares Gate]. Lass [Abnahme-Check] unter den
> gleichen Bedingungen laufen und lies den frischen Zustand selbst, statt dem Protokoll
> der Bau-Instanz zu glauben.
>
> Fass dabei nichts Fremdes an: Ändere keine unbeteiligten Dateien, betritt keine
> geschützten Zonen ([z. B. Geheimnisse und `.env`, Auth, Zahlungen, Migrationen, PII])
> und setze den Lauf niemals selbst auf „fertig" — das entscheidet ein Mensch oder das
> Gate, nicht du.
>
> Gib ein klares Urteil: **bestanden** nur mit reproduzierbarem Beleg; sonst
> **abgelehnt** mit dem konkreten Grund und dem beobachteten Gegenbeleg. Melde einen
> Fehler oder ein erschöpftes Budget nie als Erfolg.

## Ohne getrennte Instanz

Steht keine zweite Instanz bereit, nimm den **mechanischen Gegencheck**: den Fix
probeweise zurücknehmen und prüfen, ob der Test wieder rot wird. Erst das macht aus
einer Meinung ein belastbares Pass/Fail.
