# BCM-Fallstudie: HanseCloud Services GmbH

**Praxisorientiertes Portfolio-Projekt zum Business Continuity Management in Anlehnung an BSI-Standard 200-4**

> **Projektstatus: Konzept-/Analysephase (Version 0.3, Stand 25.10.2026).** Sämtliche Unternehmensdaten, Kundenverträge und Übungsergebnisse sind **fiktiv**. Die Dokumente sind eigene modellhafte Ausarbeitungen, keine freigegebenen Unternehmenspläne, keine technische Implementierung und keine BSI-Zertifizierung.

## Kurzüberblick

Für die fiktive **HanseCloud Services GmbH** (120 Mitarbeitende, IT-/Managed-Security-Dienstleister, 20 Managed-Security-Kunden) werden die geschäftlichen Folgen eines Ausfalls der Sicherheitsüberwachung untersucht. Ausgehend von einem vereinfachten Geschäftsprozessmodell wurde **GP-03: Sicherheitsüberwachung und Bereitschaft** vertieft betrachtet. Hierzu entstanden eine vorläufige Business Impact Analyse (BIA), eine Ressourcen- und Abhängigkeitsanalyse, der Entwurf einer Business-Continuity-Strategie, ein **Geschäftsfortführungsplan (GFP)**, eine technische **Wiederanlaufkonzeption (WAP)** und eine textbasierte Tabletop-Fallstudie.

**Ergebnis:** Bevorzugte Strategie zur **weiteren Prüfung** ist eine unabhängig betreibbare Ersatzüberwachung mit kontrolliertem Notfallzugang, vertrauenswürdigen Offline-/separat geschützten Konfigurationen, geregelter Eskalation und kontinuierlicher Log-Sicherung. Eine vollständige technische oder wirtschaftliche Eignung **ist noch nicht nachgewiesen**.

## Was im Projekt tatsächlich gemacht wurde

- Fiktives Unternehmen, Leistungsmodell und SLA-Randbedingungen modelliert.
- Zeitabhängige Ausfallfolgen für GP-03 anhand konstruierter Szenarien in Betrieb, Verträgen, Finanzen und Reputation bewertet.
- MTPD-Arbeitshypothese, RTO-/RPO-Planungsziele und vorgeschlagenes Notbetriebsniveau voneinander abgegrenzt.
- Kritische technische und personelle Abhängigkeiten, Single Points of Failure und Missbrauchsrisiken privilegierter Notfallzugänge betrachtet.
- Zwei BC-Strategien mit fiktiven Kosten über drei Jahre verglichen.
- Geschäftsfortführungs- und Wiederanlaufkonzept entworfen.
- Eine **textbasierte, hypothetische** Tabletop-Entscheidungsübung zu einer möglichen Kompromittierung besprochen und Lessons Learned erfasst.
- Rechenbeispiele für Logrückstand und Datenwiederherstellung erstellt und offene technische Tests spezifiziert.

**Noch nicht gemacht:** Installation von Monitoring-/Ersatzsystemen, technische Umschalttests, echte Interviews mit Unternehmen/Kunden, Freigaben, unabhängige externe Prüfung oder eine vollständige BIA aller Unternehmensprozesse.

## Kennzahlen: ausschließlich Entwurf / Szenario

| Kennzahl | Wert | Status |
|---|---:|---|
| MTPD GP-03 | 4 Stunden | **Konservative Arbeitshypothese**, nicht per BIA bestätigt |
| RTO GP-03 / relevante Ressource | 30 Minuten **ab Ausfall** | **Planungsziel**, kein Testnachweis |
| RPO erforderlicher Sicherheitslogs | 0 Minuten | **Ambitioniertes Soll**, kein Nachweis |
| SLA-Nichtverfügbarkeit | 60 Minuten **kumuliert je Kalendermonat** | Fiktive Vertragsvorgabe |
| Informationspflicht bei Unterbrechung | mehr als 30 Minuten | Fiktive Vertragsvorgabe |
| Phase stark eingeschränkter Auswertung | maximal 8 Stunden | Entwurf, nicht als maximal tragbare Dauer nachgewiesen |
| Übertragene Logereignisse im fiktiven Recovery-Test | 5.000 nach 35 Minuten | **Rechen-/Lehrszenario**, keine reale Messung |

**Methodische Korrektur gegenüber einem früheren Entwurf:** Die RTO wird nach dem herangezogenen BSI-Standard 200-4 **ab Ausfall des betroffenen Prozesses oder der Ressource** bis zur Bereitstellung der BC-Lösung betrachtet, nicht erst ab Notfallausrufung. Detektion und Alarmierung müssen in der Gesamtzeit berücksichtigt werden. Details: [Qualitäts- und Korrekturprotokoll](docs/07-qualitaetspruefung.md).

## Projektstruktur

| Datei | Inhalt |
|---|---|
| [01 – Unternehmensszenario](docs/01-unternehmen-und-scope.md) | Unternehmensmodell, Prozesse GP-01–GP-07 und fiktiver SLA-Auszug |
| [02 – BIA-Methodik](docs/02-bia-methodik.md) | Schadenskategorien, Untragbarkeitsniveau, Annahmen und Abgrenzungen |
| [03 – BIA GP-03](docs/03-bia-gp03.md) | Schadensverlauf, Rechenwerte und vorläufige Wiederanlaufziele |
| [04 – Ressourcen](docs/04-ressourcen-und-abhaengigkeiten.md) | Kritische Abhängigkeiten, SPOFs und Resilienzmaßnahmen |
| [05 – BC-Strategien](docs/05-strategievergleich.md) | Optionen A/B, Kostenmodell, Entscheidung unter Vorbehalt |
| [06 – Maßnahmenregister](docs/06-massnahmenregister.md) | Offene Aufgaben und Nachweise, nach Priorität geordnet |
| [07 – Qualitätsprüfung](docs/07-qualitaetspruefung.md) | Fachliche Korrekturen und ausdrücklich unbestätigte Aussagen |
| [08 – Quellen & Begriffe](docs/08-quellen-und-begriffe.md) | BSI-200-4-Methodenbezug, Definitionen, Nachweisgrenzen |
| [Geschäftsfortführungsplan](plans/GFP-GP03.md) | Operativer GFP **als Konzeptentwurf** |
| [Wiederanlaufplan](plans/WAP-GP03-Konzept.md) | Technischer WAP **als Konzept**, nicht ausführbar |
| [Tabletop-Übung](exercises/GP03-tabletop.md) | Szenario, Entscheidungen und Verbesserungen |
| [Test- und Nachweiskonzept](tests/GP03-testplan.md) | Noch **nicht durchgeführte** Abnahme-, RTO-, RPO- und Belastungstests |
| [Architekturkonzept](assets/architektur.md) | GitHub-kompatibles Mermaid-Diagramm |

## Nächste Arbeitsschritte

1. Prozessverantwortliche, fiktive Vertragsanforderungen und Untragbarkeitsniveau detailliert validieren; BIA für weitere Schadenskategorien und GP-01/GP-02 fortsetzen.
2. RTO/RPO **ressourcenbezogen** ableiten; Notbetriebsniveau und SLA-Gleichwertigkeit abstimmen.
3. Technische Architektur spezifizieren; Labor-Test für Umschaltung, Logvollständigkeit, Notfallzugänge und Alarmierung durchführen.
4. Gemessene RTA/RPA gegen RTO/RPO prüfen, Kosten-Nutzen-Analyse vervollständigen und erst danach eine reale Freigabeempfehlung simulieren.

## Veröffentlichungsregeln

Keine echten Unternehmens-, Kunden- oder personenbezogenen Daten, Logexporte, Tokens, Kennwörter, Schlüssel oder Zugangshinweise veröffentlichen. Notfallkontaktlisten und administrative Zugangsdaten wären in einem echten Unternehmen nur in geschützten und auch bei Systemausfall erreichbaren Ablagen vorzuhalten. Diese öffentlichen Unterlagen enthalten keine produktiv einsetzbaren Notfallzugänge.

## Methodische Referenz

[BSI-Standard 200-4 – Business Continuity Management](https://www.bsi.bund.de/SharedDocs/Downloads/DE/BSI/Grundschutz/BSI_Standards/standard_200_4.pdf?__blob=publicationFile&v=8). Kein Vollständigkeits- oder Konformitätsanspruch.
