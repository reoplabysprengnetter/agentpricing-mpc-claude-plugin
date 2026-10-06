---
name: agentpricing-presenta-valutazione
description: "Prepara per agenti immobiliari una spiegazione professionale di una valutazione AgentPricing identificata o argomenti di acquisizione fondati su quel report. Non usare per pacchetti territoriali senza report, nuove stime, una sola sezione o richieste esplicite di un singolo tool."
---

# Presenta la valutazione

## Richieste puntuali

Se l'agente indica un tool per nome o chiede soltanto un dato o una sezione, rispetta quel perimetro: esegui la chiamata pertinente e soltanto gli eventuali passaggi necessari per identificare l'input. Non trasformare la richiesta in questo workflow, non richiedere l'invocazione di una skill e non aggiungere analisi o chiamate MCP accessorie. I tool elencati qui sono scelte di workflow, non una whitelist del plugin.

## Workflow

Distingui il risultato richiesto: spiegazione della valutazione oppure argomenti per discutere prezzo e incarico. Usa dati del report identificato, preservando eventuali informazioni sulla situazione del proprietario fornite dall'agente.

- `agentpricing_generate_property_commentary`: commento professionale del report.
- `agentpricing_generate_acquisition_arguments`: argomenti di acquisizione; passa `seller_expected_price` quando noto.
- `agentpricing_get_property_report_landing_link`: soltanto se l'agente richiede anche il collegamento. Può richiedere login; non presentarlo come un link pubblico anonimo.

I tool generativi combinano già le sezioni. Non richiamare automaticamente tutte le componenti. Usa i fatti disponibili e i limiti del report; separa una spiegazione neutra della stima dagli argomenti relativi alle aspettative del proprietario.

### Compatibilità del server attuale

I due tool generativi accettano il riferimento nello schema ma le loro chiamate interne richiedono ancora un payload dell'immobile. Se hai soltanto `report_reference`/`viewkey`, usa i dati già disponibili o recupera i dettagli e le sole sezioni necessarie, quindi prepara il testo su quei risultati. Non chiamare i due compositi con il solo riferimento e non ricostruire un payload commerciale da dati residenziali. Puoi usarli quando disponi del payload corretto della valutazione già in cache; non usare questa via per generare un nuovo report implicito. Una richiesta diretta del composito rimane diretta: se l'input richiesto fallisce, riporta il limite senza avviare un workflow alternativo non richiesto.

Non creare automaticamente PDF, presentazioni o messaggi al proprietario. Restituisci il testo in chat, adattato allo scopo dell'agente.

Esempio: "Prepara la spiegazione di questa valutazione per il proprietario, che si aspetta 400.000 €."

## Contesto del report

Attribuisci i dati ad AgentPricing e riporta periodo, affidabilità e limiti quando disponibili.

Usa `report_reference` oppure `viewkey` effettivamente restituiti dal server o forniti dall'agente; non inventare riferimenti e non confonderli con un `report_id` numerico. Per una sezione specifica puoi passare direttamente il riferimento al tool, senza aprire prima tutti i dettagli. Se il report da usare è ambiguo, identifica quello corretto; se manca, non creare automaticamente una valutazione. Gestisci `status: needs_clarification` chiedendo quanto indicato da `clarification.question_it`; una conferma di nuova creazione e relativo costo deve provenire dall'agente. Non impostare `confirm_report_creation: true` senza quella conferma. Non trattare dati assenti come valori pari a zero.
