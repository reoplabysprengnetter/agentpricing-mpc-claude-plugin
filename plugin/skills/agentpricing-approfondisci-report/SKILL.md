---
name: agentpricing-approfondisci-report
description: "Prepara per agenti immobiliari una lettura coordinata di più sezioni di un report AgentPricing identificato: mercato, comparabili, OMI, prezzo, energia e scenari disponibili. Non usare per dati territoriali, nuove valutazioni, una sola sezione o una richiesta esplicita di un singolo tool."
---

# Approfondisci una valutazione

## Richieste puntuali

Se l'agente indica un tool per nome o chiede soltanto un dato o una sezione, rispetta quel perimetro: esegui la chiamata pertinente e soltanto gli eventuali passaggi necessari per identificare l'input. Non trasformare la richiesta in questo workflow, non richiedere l'invocazione di una skill e non aggiungere analisi o chiamate MCP accessorie. I tool elencati qui sono scelte di workflow, non una whitelist del plugin.

## Workflow

Lavora sul report indicato dall'agente. Usa direttamente il riferimento nelle sezioni richieste; chiama `agentpricing_get_property_report_details` solo se serve anche il quadro della valutazione. Se il riferimento non è noto e l'agente vuole un report storico, usa `agentpricing_list_property_reports` per identificarlo, rispettando la paginazione e chiedendo la scelta se ci sono più candidati.

Scegli soltanto le sezioni necessarie all'obiettivo:

| Informazione | Tool |
| --- | --- |
| Sintesi dei riferimenti di mercato | `agentpricing_get_property_market_summary` |
| Annunci concorrenti del report | `agentpricing_get_property_comparables` |
| Quotazioni OMI del report | `agentpricing_get_property_omi` |
| Venduti e sezione Agenzia delle Entrate | `agentpricing_get_property_sold_data` |
| Composizione dell'offerta | `agentpricing_get_property_market_statistics` |
| Trend, NTN e demografia disponibili | `agentpricing_get_property_advanced_market_data` |
| Posizionamento del valore stimato | `agentpricing_get_property_price_positioning` |
| Prezzo richiesto contro la valutazione | `agentpricing_analyze_property_asking_price`, con `asking_price` |
| Classe e contesto energetico | `agentpricing_get_property_energy_summary` |
| Scenari di ristrutturazione energetica | `agentpricing_get_property_renovation_energy_scenarios` |

Spiega come le sezioni richieste sostengono o limitano la valutazione. Separa prezzi degli annunci, venduti, fasce OMI e stima. Distingui classe dell'immobile e distribuzione energetica della zona. Gli scenari disponibili non equivalgono a un preventivo lavori o a una diagnosi energetica.

Se una sezione è assente, riportalo senza creare dati sostitutivi con ricerche standalone. Non rigenerare il report per un dato mancante. Se l'agente chiede un solo dato, chiama direttamente il tool corrispondente e fermati.

Esempio: "Approfondisci questa valutazione confrontando mercato, venduti e posizionamento del prezzo di 320.000 €."

## Contesto del report

Attribuisci i dati ad AgentPricing e riporta periodo, affidabilità e limiti quando disponibili.

Usa `report_reference` oppure `viewkey` effettivamente restituiti dal server o forniti dall'agente; non inventare riferimenti e non confonderli con un `report_id` numerico. Per una sezione specifica puoi passare direttamente il riferimento al tool, senza aprire prima tutti i dettagli. Se il report da usare è ambiguo, identifica quello corretto; se manca, non creare automaticamente una valutazione. Gestisci `status: needs_clarification` chiedendo quanto indicato da `clarification.question_it`; una conferma di nuova creazione e relativo costo deve provenire dall'agente. Non impostare `confirm_report_creation: true` senza quella conferma. Non trattare dati assenti come valori pari a zero.
