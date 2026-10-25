# Vereinfachte Zielarchitektur – konzeptionell

```mermaid
flowchart TB
    A[20 fiktive Kundenumgebungen] -->|Sicherheitsereignisse| B[Primäre Logverarbeitung / SIEM]
    A -->|Unabhängig / mit Puffern| C[Ersatzmonitoring]
    D[Separat geschützte Referenzkonfiguration] --> C
    E[Unabhängiger Notfallzugang] --> C
    B --> F[Security Operations]
    C --> F
    F --> G[Alarmierung / Incident Response]
```

**Hinweis:** Die Grafik zeigt eine **Zielidee**, keine bereits implementierte Architektur. Die Unabhängigkeit der Netzwerkpfade, Logpuffer, Zugriffskontrollen, Konfigurationsquellen und Alarmierungswege ist **nicht geprüft**. Ein regelmäßiger Datenfluss zum Ersatzsystem allein garantiert weder echte Redundanz noch lückenloses Logging.
