# 01 – Unternehmensszenario und Geltungsbereich

**Status:** Modellannahme | **Stand:** 25.10.2026

## Fiktive Organisation

**HanseCloud Services GmbH** ist ein erfundener mittelständischer IT-Dienstleister mit 120 Mitarbeitenden und Standort Hamburg. Er erbringt Managed IT, Cloud-Services, Kunden-Support und Managed-Security-Leistungen. Externe Rechenzentren hosten Teile der Kundenplattformen. Die interne IT betreut Identitäten, Administrationszugänge und Arbeitsplätze.

Die Fallstudie konzentriert sich auf **Managed Security**, nicht auf ein vollständiges BCMS des Unternehmens.

## Prozesslandkarte (grobe Aufnahme)

| ID | Geschäftsprozess | Typische Ressourcen | Status |
|---|---|---|---|
| GP-01 | Betrieb der Kundenplattformen | Rechenzentrum, Netz, Administratoren | Noch nicht vertieft |
| GP-02 | Störungsbearbeitung/Support | Ticketsystem, Telefonie, Personal | Noch nicht vertieft |
| **GP-03** | **Sicherheitsüberwachung und Bereitschaft** | SIEM/Monitoring, Log-Transport, IAM, Fachkräfte | **Vertiefte Fallstudie** |
| GP-04 | Kunden-Onboarding | CRM, Berechtigungsverwaltung | Nicht untersucht |
| GP-05 | Rechnungsstellung | ERP, Finanzteam | Nicht untersucht |
| GP-06 | Vertrieb/Vertragsmanagement | CRM, E-Mail | Nicht untersucht |
| GP-07 | Personalverwaltung | HR-Systeme | Nicht untersucht |

Eine belastbare Priorisierung *zwischen* diesen Prozessen wurde bisher nicht durchgeführt.

## Fiktive Verträge der Managed-Security-Sparte

- 20 Kunden mit je **2.000 EUR monatlicher Servicegebühr** (vereinfachtes, einheitliches Gebührenmodell).
- Vertraglich zugesagt: Sicherheitsüberwachung **24 Stunden an 7 Tagen**.
- Kumuliert höchstens **60 Minuten ungeplante Nichtverfügbarkeit je Kalendermonat** (allein diese Zahl garantiert weder die Einhaltung anderer SLAs noch die Gleichwertigkeit einer reduzierten Überwachung).
- **Kundeninformation** bei Unterbrechung von **mehr als 30 Minuten**.
- Bei Überschreiten der Toleranz können betroffene Kunden eine **Servicegutschrift von 10 % ihrer monatlichen Gebühr** verlangen.
- Eine zeitnahe Untersuchung kritischer Ereignisse wird zugesagt, **ohne bislang dokumentierte konkrete Reaktionsfrist**.
- Ob eine Ersatzüberwachung mit eingeschränkten Erkennungsregeln vertragskonform ist, ist **nicht geklärt**.

Diese Vertragswerte dienen ausschließlich der Übung und sind keine Mustervertrags- oder Rechtsberatung.

## Abgrenzung

Gegenstand: Auswirkungen eines vollständigen oder eingeschränkten Ausfalls von GP-03, Abhängigkeiten, BC-Strategie, Wiederanlauf-/Fortführungsplanung und eine textbasierte Tabletop-Fallstudie.

Nicht Gegenstand: vollständige rechtliche Bewertung, vollständiger Business-Impact aller Prozesse, vollständige technische Implementierung, produktiver Katastrophentest oder realer Zertifizierungsprozess.
