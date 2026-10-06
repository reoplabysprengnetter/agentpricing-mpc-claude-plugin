---
name: agentpricing-scenario-investimento
description: "Prepara per agenti immobiliari uno scenario di acquisto e messa a reddito da discutere con un cliente investitore, rendendo espliciti canone, costi e assunzioni. Non usare per valutazioni commerciali in locazione, confronto di aree, semplici metriche o richieste di un singolo tool."
---

# Scenario per investitore

## Richieste puntuali

Se l'agente indica un tool per nome o chiede soltanto un dato o una sezione, rispetta quel perimetro: esegui la chiamata pertinente e soltanto gli eventuali passaggi necessari per identificare l'input. Non trasformare la richiesta in questo workflow, non richiedere l'invocazione di una skill e non aggiungere analisi o chiamate MCP accessorie. I tool elencati qui sono scelte di workflow, non una whitelist del plugin.

## Workflow

Usa `agentpricing_get_investment_scenario` con `area`, `subject_property` e `purchase_price`. Raccogli posizione, superficie e prezzo di acquisto quando mancanti. Passa canone, costi, sfitto, orizzonte e altre assunzioni solo se forniti; il canone non è obbligatorio perché il server può usare riferimenti o default.

Distingui dati del cliente, valori derivati da OMI e ipotesi predefinite. Separa rendimenti lordi e netti solo dove il risultato lo consente, ed esplicita i costi inclusi. Non chiamare "netto" un rendimento che non include tutte le spese considerate dal cliente.

Per confrontare assunzioni alternative, riusa dati già noti ed esegui soltanto gli scenari richiesti; non generare automaticamente molte simulazioni. Non trattare il CAGR OMI o la rivalutazione ipotizzata come una previsione certa e non introdurre aliquote o agevolazioni fiscali non fornite dai dati.

Prepara un riepilogo per l'agente e una spiegazione delle assunzioni da discutere con l'investitore. Per stimare il canone di un negozio o capannone usa il percorso di valutazione commerciale, non questo scenario.

Esempio: "Per un cliente investitore, prepara lo scenario di acquisto a 180.000 € con canone di 850 € al mese e 15.000 € di lavori."

## Perimetro e risultati

Questo workflow è standalone: non crea né richiede un report. Non passare a tool report-bound per completare una sezione mancante. Usa i dati AgentPricing restituiti, indicando campione, periodo e limiti quando disponibili. I tool compositi includono già più analisi: non richiamare le loro componenti salvo una richiesta di approfondimento. Non controllare automaticamente il saldo crediti e non eseguire tutte le azioni suggerite dal server.
