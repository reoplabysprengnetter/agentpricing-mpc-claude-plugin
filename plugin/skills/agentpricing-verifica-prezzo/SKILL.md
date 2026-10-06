---
name: agentpricing-verifica-prezzo
description: "Prepara per agenti immobiliari un'analisi del prezzo richiesto di un immobile rispetto a venduti, annunci e OMI, senza creare un report, per discuterlo con il proprietario. Non usare per stime di valore, confronti con una valutazione esistente o richieste di un singolo tool o dato."
---

# Verifica prezzo richiesto

## Richieste puntuali

Se l'agente indica un tool per nome o chiede soltanto un dato o una sezione, rispetta quel perimetro: esegui la chiamata pertinente e soltanto gli eventuali passaggi necessari per identificare l'input. Non trasformare la richiesta in questo workflow, non richiedere l'invocazione di una skill e non aggiungere analisi o chiamate MCP accessorie. I tool elencati qui sono scelte di workflow, non una whitelist del plugin.

## Workflow

Usa `agentpricing_analyze_listing_price` con `area`, `subject_property` e `asking_price`. Chiedi posizione, superficie commerciale e prezzo richiesto solo quando mancanti; conserva le caratteristiche note dell'immobile. Non calcolare una valutazione report-bound come passaggio preliminare.

Restituisci assessment, scostamento rispetto ai venduti e agli annunci attivi, riferimenti OMI e scenari restituiti dal server, quando presenti. Separa le basi del confronto: una mediana dei prezzi richiesti non equivale a un prezzo di chiusura.

Prepara una breve spiegazione che l'agente possa usare per discutere il prezzo di partenza o una revisione con il proprietario. Non dedurre le cause di mancata vendita dal solo scostamento di prezzo: contatti, visite, durata dell'incarico e commercializzazione richiedono dati ulteriori dell'agente. Non trasformare lo scostamento in uno sconto garantito.

Se l'agente vuole il confronto con un report identificato, questa skill non si applica: usa direttamente `agentpricing_analyze_property_asking_price` con il riferimento e `asking_price`, limitandoti a quella richiesta.

Esempio: "Il proprietario vuole 350.000 € per questo appartamento di 110 m²: prepara un confronto con il mercato per discutere il prezzo di incarico."

## Perimetro e risultati

Questo workflow è standalone: non crea né richiede un report. Non passare a tool report-bound per completare una sezione mancante. Usa i dati AgentPricing restituiti, indicando campione, periodo e limiti quando disponibili. I tool compositi includono già più analisi: non richiamare le loro componenti salvo una richiesta di approfondimento. Non controllare automaticamente il saldo crediti e non eseguire tutte le azioni suggerite dal server.
