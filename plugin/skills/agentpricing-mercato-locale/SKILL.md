---
name: agentpricing-mercato-locale
description: "Prepara per agenti immobiliari una lettura del mercato locale o un aggiornamento scritto per proprietari, acquirenti, investitori o uso interno, senza report. Non usare per una sola quotazione OMI, una singola metrica o chiamata MCP, confronti tra zone o sezioni di un report."
---

# Mercato locale

## Richieste puntuali

Se l'agente indica un tool per nome o chiede soltanto un dato o una sezione, rispetta quel perimetro: esegui la chiamata pertinente e soltanto gli eventuali passaggi necessari per identificare l'input. Non trasformare la richiesta in questo workflow, non richiedere l'invocazione di una skill e non aggiungere analisi o chiamate MCP accessorie. I tool elencati qui sono scelte di workflow, non una whitelist del plugin.

## Workflow

Identifica l'area con indirizzo e città o coordinate. Chiarisci il destinatario del testo solo se influisce sulla richiesta.

- Per una panoramica analitica usa `agentpricing_get_area_market_snapshot`.
- Per un aggiornamento scritto usa `agentpricing_generate_market_update`, con `audience` coerente con il destinatario (seller, buyer, investor, internal). Include già snapshot e Opportunity Score quando disponibili.
- Usa `agentpricing_get_omi_zone_analysis` soltanto quando servono dettagli OMI o uno storico non già restituito; una richiesta limitata alle quotazioni si esegue direttamente senza questo workflow.

Interpreta prezzi, compravendite, stock, tempi di vendita e altri indicatori solo dove presenti. Indica periodo effettivo, area e qualità del campione. La data di generazione della risposta non è il periodo dei dati. Non presentare il campione dei venduti come l'intero mercato e non usare il trend OMI come trend certo dei prezzi di chiusura.

La richiesta di un aggiornamento mensile o trimestrale non autorizza a inventare filtri temporali non supportati. Se il periodo desiderato non è disponibile, esplicita il periodo effettivo. Non programmare invii o pubblicare il testo.

Esempio: "Prepara un aggiornamento sul mercato di questa zona da usare nei colloqui con i proprietari."

## Perimetro e risultati

Questo workflow è standalone: non crea né richiede un report. Non passare a tool report-bound per completare una sezione mancante. Usa i dati AgentPricing restituiti, indicando campione, periodo e limiti quando disponibili. I tool compositi includono già più analisi: non richiamare le loro componenti salvo una richiesta di approfondimento. Non controllare automaticamente il saldo crediti e non eseguire tutte le azioni suggerite dal server.
