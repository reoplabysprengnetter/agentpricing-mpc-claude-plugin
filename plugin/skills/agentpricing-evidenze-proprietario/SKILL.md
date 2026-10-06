---
name: agentpricing-evidenze-proprietario
description: "Prepara per agenti immobiliari un pacchetto di evidenze su venduti simili e quotazioni OMI da discutere con il proprietario durante acquisizione o revisione del prezzo, senza report. Non usare per briefing, argomenti basati su un report, soli comparabili o richieste di un singolo tool."
---

# Evidenze per il proprietario

## Richieste puntuali

Se l'agente indica un tool per nome o chiede soltanto un dato o una sezione, rispetta quel perimetro: esegui la chiamata pertinente e soltanto gli eventuali passaggi necessari per identificare l'input. Non trasformare la richiesta in questo workflow, non richiedere l'invocazione di una skill e non aggiungere analisi o chiamate MCP accessorie. I tool elencati qui sono scelte di workflow, non una whitelist del plugin.

## Workflow

Usa `agentpricing_generate_seller_evidence_pack` con `area` e `subject_property`; aggiungi `asking_price` se l'agente comunica l'aspettativa o il prezzo attuale. Chiedi soltanto gli input necessari mancanti, inclusa la superficie commerciale.

Il tool restituisce già comparabili selezionati per similarità, riferimenti OMI ed eventuale analisi del prezzo. Usa queste evidenze senza richiamare automaticamente le analisi componenti. Il risultato è un pacchetto strutturato, non un PDF: prepara il contenuto in chat; un file richiede una richiesta ulteriore dell'agente.

Presenta le evidenze più pertinenti, il criterio di selezione, i limiti del campione e punti di discussione formulati in modo professionale. Non eliminare i confronti sfavorevoli alla proposta di prezzo e non attribuire motivazioni ai proprietari senza informazioni.

Se mancano comparabili sufficienti, spiega il limite; non inventare casi o link e non sostituire il workflow con una valutazione report-bound. Questo pacchetto non è una perizia.

Esempio: "Prepara evidenze sui venduti per discutere con il proprietario la richiesta di 400.000 €, senza generare una valutazione."

## Perimetro e risultati

Questo workflow è standalone: non crea né richiede un report. Non passare a tool report-bound per completare una sezione mancante. Usa i dati AgentPricing restituiti, indicando campione, periodo e limiti quando disponibili. I tool compositi includono già più analisi: non richiamare le loro componenti salvo una richiesta di approfondimento. Non controllare automaticamente il saldo crediti e non eseguire tutte le azioni suggerite dal server.
