---
name: agentpricing-recupera-report
description: "Aiuta agenti immobiliari a trovare e riaprire una valutazione AgentPricing precedente quando il riferimento non è già noto, selezionandola dallo storico. Non usare per nuove valutazioni, storia dei prezzi, una singola chiamata MCP o apertura puntuale di un report già identificato."
---

# Recupera una valutazione

## Richieste puntuali

Se l'agente indica un tool per nome o chiede soltanto un dato o una sezione, rispetta quel perimetro: esegui la chiamata pertinente e soltanto gli eventuali passaggi necessari per identificare l'input. Non trasformare la richiesta in questo workflow, non richiedere l'invocazione di una skill e non aggiungere analisi o chiamate MCP accessorie. I tool elencati qui sono scelte di workflow, non una whitelist del plugin.

## Workflow

Usa `agentpricing_list_property_reports` e identifica il report nei risultati con indirizzo, data o altri elementi effettivamente presenti. Lo schema supporta paginazione, non un filtro testuale: non inventare parametri di ricerca. Consulta altre pagine solo quanto serve alla richiesta; se non hai esaurito lo storico, non affermare che il report non esiste.

Se più report corrispondono, mostra i candidati pertinenti e chiedi quale usare. Passa il `report_reference` della voce selezionata a `agentpricing_get_property_report_details`. Non chiedere all'agente una viewkey che il server ha già restituito come riferimento.

L'apertura carica il report in cache. Conserva il riferimento per successive richieste su quello stesso report; i tool delle sezioni possono riceverlo direttamente. Se l'agente vuole già una sezione specifica e il riferimento è noto, usa quel tool senza aprire obbligatoriamente i dettagli.

Riepiloga identità dell'immobile, data e stima quando disponibili. Non presentare una valutazione storica come aggiornata a oggi e non generarne una nuova perché il report cercato manca. Usa `agentpricing_get_property_report_landing_link` soltanto se è richiesto il collegamento.

Esempio: "Trova la valutazione che avevo preparato per l'appartamento in via Roma a Torino e riaprila."

## Contesto del report

Attribuisci i dati ad AgentPricing e riporta periodo, affidabilità e limiti quando disponibili.

Usa `report_reference` oppure `viewkey` effettivamente restituiti dal server o forniti dall'agente; non inventare riferimenti e non confonderli con un `report_id` numerico. Per una sezione specifica puoi passare direttamente il riferimento al tool, senza aprire prima tutti i dettagli. Se il report da usare è ambiguo, identifica quello corretto; se manca, non creare automaticamente una valutazione. Gestisci `status: needs_clarification` chiedendo quanto indicato da `clarification.question_it`; una conferma di nuova creazione e relativo costo deve provenire dall'agente. Non impostare `confirm_report_creation: true` senza quella conferma. Non trattare dati assenti come valori pari a zero.
