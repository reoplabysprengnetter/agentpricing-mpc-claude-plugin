# AgentPricing Connector

Plugin Claude con 11 skill per agenti immobiliari e connessione MCP a `https://mcp.agentpricing.com/mcp`.

| Skill | Ambito |
| --- | --- |
| `agentpricing-valutazione-immobile` | Valutazione per incarico |
| `agentpricing-ricerca-comparabili` | Comparabili standalone |
| `agentpricing-verifica-prezzo` | Prezzo richiesto vs mercato |
| `agentpricing-prepara-appuntamento` | Briefing appuntamento |
| `agentpricing-evidenze-proprietario` | Evidenze per il venditore |
| `agentpricing-mercato-locale` | Snapshot / market update |
| `agentpricing-confronta-zone` | Confronto aree |
| `agentpricing-scenario-investimento` | Buy-to-rent |
| `agentpricing-approfondisci-report` | Sezioni di un report |
| `agentpricing-presenta-valutazione` | Spiegazione al proprietario |
| `agentpricing-recupera-report` | Storico valutazioni |

Le skill non limitano i tool MCP: richieste puntuali su un singolo tool vanno eseguite direttamente. Autenticazione OAuth sul server remoto; nessun segreto nel pacchetto.
