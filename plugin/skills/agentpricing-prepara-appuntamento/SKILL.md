---
name: agentpricing-prepara-appuntamento
description: "Prepara per un agente immobiliare un briefing prima di un appuntamento di acquisizione o sopralluogo, con contesto di mercato e domande pertinenti, senza report. Non usare per fissare appuntamenti, generare una valutazione, preparare sole evidenze o chiamare un singolo tool."
---

# Prepara appuntamento

## Richieste puntuali

Se l'agente indica un tool per nome o chiede soltanto un dato o una sezione, rispetta quel perimetro: esegui la chiamata pertinente e soltanto gli eventuali passaggi necessari per identificare l'input. Non trasformare la richiesta in questo workflow, non richiedere l'invocazione di una skill e non aggiungere analisi o chiamate MCP accessorie. I tool elencati qui sono scelte di workflow, non una whitelist del plugin.

## Workflow

Usa `agentpricing_prepare_appointment`. Raccogli `area`; passa `subject_property`, `asking_price` e `appointment_goal` quando conosciuti. Le caratteristiche dell'immobile e il prezzo sono opzionali: non bloccare un briefing territoriale se non sono ancora disponibili. Chiarisci l'obiettivo dell'incontro solo se necessario per adattare la preparazione.

Il tool include già contesto territoriale, OMI, comparabili e analisi del prezzo quando gli input lo consentono. Parti da quel risultato senza ricostruire il pacchetto con ulteriori chiamate.

Prepara una scheda consultabile prima dell'incontro: fatti di mercato disponibili, punti da discutere e domande sul venditore e sull'immobile. Separa fatti dai punti da verificare al sopralluogo e adatta le domande all'obiettivo dichiarato.

Nel riepilogo dei comparabili, `suggested_price` e `suggested_price_sqm` sono mediane ponderate calcolate separatamente sui prezzi totali e sui prezzi al mq degli immobili confrontati. Presentale come riferimenti del campione: non devono necessariamente coincidere moltiplicando il prezzo al mq per la superficie dell'immobile oggetto dell'appuntamento. Questa differenza, da sola, non dimostra un errore nei dati. Non presentare la mediana dei prezzi totali come una valutazione personalizzata dell'immobile.

Questo workflow prepara l'incontro; non crea eventi di calendario, non contatta proprietari e non invia materiale. Per un pacchetto documentato di compravendite da mostrare al proprietario usa il tool specifico solo se richiesto.

Esempio: "Domani ho un appuntamento di acquisizione in via Roma: prepara un briefing con le domande da fare al proprietario."

## Perimetro e risultati

Questo workflow è standalone: non crea né richiede un report. Non passare a tool report-bound per completare una sezione mancante. Usa i dati AgentPricing restituiti, indicando campione, periodo e limiti quando disponibili. I tool compositi includono già più analisi: non richiamare le loro componenti salvo una richiesta di approfondimento. Non controllare automaticamente il saldo crediti e non eseguire tutte le azioni suggerite dal server.
