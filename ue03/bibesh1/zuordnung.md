# Anforderung oder Lösung? — Terminplaner für die THM

GitHub-Benutzername: bibesh1

## Funktionale Anforderung (FA)

- Studierende können einen freien Sprechstundentermin bei einer Lehrperson buchen.
- Ein bereits gebuchter Termin kann kein zweites Mal gebucht werden.
- Sagt eine Lehrperson eine Sprechstunde ab, erhalten alle, die gebucht haben, eine Nachricht.
- Jeder gebuchte Termin lässt sich als iCal-Datei herunterladen.
- Ein Sekretariat sieht alle Prüfungstermine seines Fachbereichs auf einen Blick.
- Über die API kann ein KI-Agent freie Termine abfragen und im Namen einer Person buchen.

## Qualitätsanforderung (QA)

- Eine Buchung ist für Studierende in höchstens drei Schritten abgeschlossen.
- Auch zu Beginn der Prüfungsanmeldung, wenn bis zu 2.000 Personen zugleich buchen, zeigt das System eine Seite in weniger als zwei Sekunden an.
- Die Buchungsseite ist mit einem Screenreader vollständig bedienbar.

## Randbedingung (RB)

- Die Anmeldung erfolgt ausschließlich über das Hochschulkonto.
- Die erste Ausbaustufe geht zum Sommersemester 2027 in Betrieb.
- Personenbezogene Daten werden nach den Vorgaben der EU-DSGVO verarbeitet.
- Das System wird im Rechenzentrum der THM betrieben.

## Keine Anforderung — Lösung (WIE)

- Termine werden in einer PostgreSQL-Datenbank gespeichert.
- Vor jeder Buchung fragt die Komponente „Buchung“ bei der Komponente „Kalender“ an, ob der Termin noch frei ist.
- Die API nimmt Anfragen als REST-Aufrufe entgegen und antwortet in JSON.

## Bei welchen Karten waren Sie unsicher — und was haben Sie abgewogen?

- **Termine werden in einer PostgreSQL-Datenbank gespeichert.** (Keine Anforderung — Lösung (WIE)): Das beschreibt, wie das System gebaut wird (WIE). Es wäre nur dann eine Randbedingung, wenn die THM PostgreSQL verbindlich vorschreibt.
- **Die Anmeldung erfolgt ausschließlich über das Hochschulkonto.** (Randbedingung (RB)): Ich habe zwischen Randbedingung und funktionaler Anforderung abgewogen und Randbedingung gewählt, weil die THM die Anmeldung über das Hochschulkonto vorgibt.
- **Die API nimmt Anfragen als REST-Aufrufe entgegen und antwortet in JSON.** (Keine Anforderung — Lösung (WIE)): Das beschreibt, wie die Schnittstelle gebaut wird (WIE). Es wäre nur dann eine Randbedingung, wenn ein anderes System REST und JSON verbindlich vorgibt.
- **Die Buchungsseite ist mit einem Screenreader vollständig bedienbar.** (Qualitätsanforderung (QA)): Ich habe zwischen Qualitätsanforderung und Randbedingung abgewogen und Qualitätsanforderung gewählt, weil es um die Bedienbarkeit als Eigenschaft geht. Es wäre eine Randbedingung, wenn ein Gesetz es vorschreibt.
- **Das System wird im Rechenzentrum der THM betrieben.** (Randbedingung (RB)): Ich habe zwischen Randbedingung und WIE abgewogen und Randbedingung gewählt, weil die THM den Betriebsort vorgibt. Es wäre ein WIE, wenn das Projekt den Ort frei entscheiden könnte.
- **Über die API kann ein KI-Agent freie Termine abfragen und im Namen einer Person buchen.** (Funktionale Anforderung (FA)): Ich habe funktionale Anforderung gewählt, weil es beschreibt, was der Agent tun darf. Dass es über die API läuft, ist nur der Weg dorthin.

<!-- zuordnung ue03-anforderung-oder-loesung: k01=fa k02=wie k03=rb k04=qa k05=fa k06=rb k07=wie k08=fa k09=rb k10=qa k11=wie k12=fa k13=qa k14=fa k15=rb k16=fa | unsicher: k02 k03 k11 k13 k15 k16 -->
