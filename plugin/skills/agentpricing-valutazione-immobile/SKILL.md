---
name: agentpricing-valutazione-immobile
description: "Prepara per agenti immobiliari una valutazione residenziale o commerciale a supporto del prezzo di incarico, con lettura professionale della stima. Usa per una nuova valutazione o una rivalutazione esplicitamente richiesta; non per sole sezioni di un report, ricerche territoriali o richieste esplicite di un singolo tool."
---

# Valutazione per incarico

## Richieste puntuali

Se l'agente indica un tool per nome o chiede soltanto un dato o una sezione, rispetta quel perimetro: esegui la chiamata pertinente e soltanto gli eventuali passaggi necessari per identificare l'input. Non trasformare la richiesta in questo workflow, non richiedere l'invocazione di una skill e non aggiungere analisi o chiamate MCP accessorie. I tool elencati qui sono scelte di workflow, non una whitelist del plugin.

## Obiettivo

Prepara una valutazione utilizzabile dall'agente nella definizione del prezzo di incarico. Una richiesta esplicita di valutazione autorizza il relativo tool; non richiedere un'ulteriore conferma se il server non la prevede.

## Workflow

- Per appartamenti, case, ville e attici usa `agentpricing_evaluate_residential_property`. Evita l'alias deprecato `agentpricing_evaluate_property` nelle nuove chiamate. Raccogli indirizzo, città e superficie commerciale; riusa le altre caratteristiche già fornite. Non inventare caratteristiche sconosciute né chiedere tutti i campi opzionali.
- Le condizioni residenziali, come "da ristrutturare", vanno in `property.manutenzione`. `statoConservativo` riguarda solo la conservazione OMI (ottimo, normale, scadente).
- Per negozi, uffici e capannoni leggi [il percorso commerciale](references/commerciale.md) e usa `agentpricing_evaluate_commercial_property`. Non usare il tool residenziale per un'unità commerciale.
- Se l'agente chiede di rileggere una valutazione esistente, recupera quel report invece di generarne una nuova. Una nuova valutazione dello stesso immobile deve essere richiesta esplicitamente; non promettere un aggiornamento live di un report storico.

Presenta stima, intervallo e €/m² effettivamente restituiti, affidabilità quando disponibile e aspetti da verificare al sopralluogo. Distingui valore stimato e proposta di prezzo di incarico. Non aggiungere commenti generativi, comparabili, OMI o link con altre chiamate salvo necessità espressa dall'agente.

Esempio: "Prepara la valutazione per l'acquisizione di un appartamento di 90 m² in via Roma 12 a Torino, terzo piano con ascensore, da ristrutturare."

## Contesto del report

Attribuisci i dati ad AgentPricing e riporta periodo, affidabilità e limiti quando disponibili.

Usa `report_reference` oppure `viewkey` effettivamente restituiti dal server o forniti dall'agente; non inventare riferimenti e non confonderli con un `report_id` numerico. Per una sezione specifica puoi passare direttamente il riferimento al tool, senza aprire prima tutti i dettagli. Per una consultazione di un report esistente, identifica quello corretto se ambiguo e non crearne uno nuovo se manca. La richiesta esplicita di nuova valutazione segue invece il workflow descritto sopra. Gestisci `status: needs_clarification` chiedendo quanto indicato da `clarification.question_it`; una conferma di nuova creazione e relativo costo deve provenire dall'agente. Non impostare `confirm_report_creation: true` senza quella conferma. Non trattare dati assenti come valori pari a zero.
