# 04 – Ressourcenabhängigkeiten und Notbetriebsarchitektur

**Status:** Konzeptionelle Analyse, noch nicht technisch überprüft.

## Prozessnotwendige Ressourcen

| Ressourcenkategorie | Beispiele | Abhängigkeit / Ausfallfolge | Vorgeschlagene Maßnahme | Nachweis |
|---|---|---|---|---|
| IT / Plattform | SIEM, Regelwerk, Indexer, Dashboards | Alarmierung/Analyse kann ausfallen | Eigenständig lauffähige Ersatzlösung | Offen |
| Identität / Zugriff | IAM, MFA, Admin-Zugänge | Keine Administratoranmeldung möglich | Eigenständige Notfallidentitäten; Zugriffsschutz | Offen |
| Informationen | Logereignisse, Regeln, Konfigurationen | Datenverlust, blindes Monitoring | Geschützte Logpuffer, separate signierte Referenzkonfiguration | Offen |
| Netzwerk | Log-Transport, Admin-Verbindungen | Ereignisse erreichen Ersatzsystem nicht | Alternativer unabhängiger Übertragungsweg | Offen |
| Personal | 24/7 Analysten, Admin-Bereitschaft | Kein Alarm-Triage/Wiederanlauf | Vertretung, Rufbereitschaft, mehrere qualifizierte Personen | Offen |
| Kommunikation | Alarmierung, Telefon, Kundennachricht | Verzögerte Eskalation und Information | Unabhängiger Kanal, offline verfügbarer Kontaktplan | Offen |
| Externe Dienstleistungen | Rechenzentrum, Netzprovider | Gemeinsame Ausfallursache möglich | Trennung nach tatsächlichen Fehlerdomänen prüfen | Offen |

## Besondere Risiken

- **Single Point of Failure:** Eine einzelne Komponente kann Primär- und Ersatzmonitoring gemeinsam beeinträchtigen.
- **Single Point of Knowledge:** Nur eine Person kennt die Aktivierung oder verwaltet allein den Notfallzugang.
- **Single Point of Compromise:** Die Ersatzlösung bezieht ungeprüft Konfigurationen oder Zugangsdaten aus einer kompromittierten Primärumgebung.

## Konzeptionelle Schutzmaßnahmen

- Räumlich oder logisch ausreichend getrennte Infrastruktur **und** unabhängige Kontroll-/Management-Ebene; gemeinsame Fehlerdomänen ermitteln.
- Vorbereitetes System mit unabhängig gesicherter, validierbarer Referenzkonfiguration; keine ungeprüften Live-Konfigurationsimporte im Angriffsszenario.
- Zwei oder mehr autorisierte Mitarbeitende mit geübtem Notfallverfahren; Berechtigungen nur so weit wie nötig.
- Break-Glass-Accounts: unabhängige Authentifizierung, starke Zugangssicherung, protokollierte Nutzung und nachträgliche Prüfung. Ein solcher Account ersetzt **keine** Personalvertretung.
- Persistente Logpuffer mit nachweisbarer Integrität, Vollständigkeit und kontrollierter Nachübertragung.
- Unabhängige Erkennung, wenn der Monitoring-Dienst selbst ausfällt.

Die konkrete technische Architektur, Host-/Netzkomponenten, Zugangsmethoden und Datenflüsse werden erst in einem Labor nachgewiesen. Grafik: [Architekturkonzept](../assets/architektur.md).
