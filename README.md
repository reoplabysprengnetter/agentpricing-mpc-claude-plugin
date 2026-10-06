# AgentPricing Connector (Claude)

Marketplace pubblico del plugin **AgentPricing Connector** per Claude Code / Claude.

Collega il server MCP remoto `https://mcp.agentpricing.com/mcp` e fornisce 11 skill per agenti immobiliari (valutazioni, comparabili, mercato locale, report storici).

Questo repository contiene **solo** il plugin Claude. Il server MCP e le altre integrazioni restano in un repository privato separato; le modifiche al plugin vengono sincronizzate automaticamente da lì.

## Installazione

```bash
claude plugin marketplace add reoplabysprengnetter/agentpricing-mpc-claude-plugin
claude plugin install agentpricing@agentpricing-marketplace
```

In alternativa, con URL completo:

```bash
claude plugin marketplace add https://github.com/reoplabysprengnetter/agentpricing-mpc-claude-plugin.git
claude plugin install agentpricing@agentpricing-marketplace
```

Dopo l’installazione, autentica il server MCP dal pannello `/mcp` (OAuth). Il pacchetto non include token né credenziali.

## Struttura

```text
.
├── .claude-plugin/marketplace.json
└── plugin/
    ├── .claude-plugin/plugin.json
    ├── .mcp.json
    ├── LICENSE
    ├── assets/
    └── skills/
```

## Licenza e supporto

Licenza: vedi [plugin/LICENSE](plugin/LICENSE) (AgentPricing Proprietary License).  
Sviluppato da [Reopla srl](https://www.agentpricing.com/).  
Privacy: https://www.agentpricing.com/static/docs/informativa_clienti.html  
Termini: https://www.agentpricing.com/static/docs/terms.pdf
