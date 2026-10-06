---
name: agentpricing-ricerca-comparabili
description: "Prepara per agenti immobiliari un confronto tra immobili venduti simili e/o annunci concorrenti intorno a un immobile, senza report. Usa per una ricerca comparativa con selezione e interpretazione; non per comparabili di un report esistente o per una singola chiamata MCP o un solo dato."
---

# Ricerca comparabili

## Richieste puntuali

Se l'agente indica un tool per nome o chiede soltanto un dato o una sezione, rispetta quel perimetro: esegui la chiamata pertinente e soltanto gli eventuali passaggi necessari per identificare l'input. Non trasformare la richiesta in questo workflow, non richiedere l'invocazione di una skill e non aggiungere analisi o chiamate MCP accessorie. I tool elencati qui sono scelte di workflow, non una whitelist del plugin.

## Workflow

Chiarisci quali confronti servono soltanto se non emerge dalla richiesta: compravendite vicine, venduti simili all'immobile oppure concorrenza attiva. Non richiedere entrambe le famiglie di dati se l'agente ne vuole una sola.

- `agentpricing_search_sold_properties`: transazioni vicine, con posizione, raggio e filtri supportati; non richiede le caratteristiche di un immobile di riferimento.
- `agentpricing_get_property_sold_comparables`: venduti ordinati per similarità; richiede `area` e `subject_property`, con `surface_sqm`. Il risultato include già anche comparabili di mercato attivi quando disponibili.
- `agentpricing_search_active_listings`: annunci attivi, con filtri ed eventuale `reference_property` per la similarità. Il raggio di questo tool è `radius_km`; gli input territoriali degli altri tool usano `radius_meters`.

Usa indirizzo e città oppure coordinate reali; rendi esplicito il raggio applicato. Non ampliare silenziosamente area, tipologia o filtri per ottenere risultati. Se il campione è insufficiente, spiega quali vincoli andrebbero modificati.

Produci un confronto leggibile con superficie, prezzo, €/m², distanza, data e similarità se disponibili. Separa prezzi richiesti e prezzi di vendita. Mantieni l'ordinamento per similarità e non selezionare solo casi favorevoli a un prezzo desiderato. Non inventare URL degli annunci: il tool non restituisce link ai portali.

Esempio: "Confronta i venduti simili e la concorrenza attiva per questo appartamento di 100 m², entro un chilometro."

## Perimetro e risultati

Questo workflow è standalone: non crea né richiede un report. Non passare a tool report-bound per completare una sezione mancante. Usa i dati AgentPricing restituiti, indicando campione, periodo e limiti quando disponibili. I tool compositi includono già più analisi: non richiamare le loro componenti salvo una richiesta di approfondimento. Non controllare automaticamente il saldo crediti e non eseguire tutte le azioni suggerite dal server.
