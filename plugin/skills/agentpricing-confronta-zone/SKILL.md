---
name: agentpricing-confronta-zone
description: "Prepara per agenti immobiliari un confronto tra due e cinque aree usando indicatori territoriali e componenti dell'Opportunity Score, per orientare il lavoro o un cliente. Non usare per analisi di un immobile, semplici snapshot o richieste di un singolo tool o punteggio."
---

# Confronta zone

## Richieste puntuali

Se l'agente indica un tool per nome o chiede soltanto un dato o una sezione, rispetta quel perimetro: esegui la chiamata pertinente e soltanto gli eventuali passaggi necessari per identificare l'input. Non trasformare la richiesta in questo workflow, non richiedere l'invocazione di una skill e non aggiungere analisi o chiamate MCP accessorie. I tool elencati qui sono scelte di workflow, non una whitelist del plugin.

## Workflow

Usa `agentpricing_compare_acquisition_areas` per 2–5 aree, mantenendo comparabili tipologia e perimetri quando possibile. Ogni area deve avere indirizzo e città oppure coordinate; non inventare un punto centrale per un quartiere ambiguo. Chiarisci cosa l'agente vuole confrontare se manca un criterio decisionale.

Se la richiesta riguarda una sola area e i driver del punteggio, usa `agentpricing_get_area_opportunity_score`; non creare un confronto artificiale con altre zone. Una richiesta del solo score si esegue direttamente.

Presenta le differenze effettive, i componenti del punteggio, le carenze informative e le implicazioni rispetto all'obiettivo dell'agente. Non premiare automaticamente un'area con più dati e non equiparare l'Opportunity Score alla probabilità di ottenere incarichi.

Il server descrive il mercato: non misura direttamente concorrenza tra agenzie, costo di acquisizione, numero di proprietari contattabili o redditività dell'agenzia. Non trasformare lo score in una raccomandazione automatica di investimento.

Esempio: "Confronta queste tre zone per valutare dove concentrare la ricerca di immobili da acquisire."

## Perimetro e risultati

Questo workflow è standalone: non crea né richiede un report. Non passare a tool report-bound per completare una sezione mancante. Usa i dati AgentPricing restituiti, indicando campione, periodo e limiti quando disponibili. I tool compositi includono già più analisi: non richiamare le loro componenti salvo una richiesta di approfondimento. Non controllare automaticamente il saldo crediti e non eseguire tutte le azioni suggerite dal server.
