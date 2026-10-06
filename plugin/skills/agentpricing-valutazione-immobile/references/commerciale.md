# Valutazione commerciale

Usa `agentpricing_evaluate_commercial_property`; il backend corrente richiede `legacy`. Leggi lo schema del tool disponibile: uffici supportano attualmente la vendita; negozi e capannoni vendita o locazione. Non promettere una valutazione di locazione per un ufficio se lo schema non la consente.

Raccogli i campi comuni necessari: `property_type`, `operation`, `address`, `civico`, `city`, `street_level_surface`, `basement_surface` (0 solo se l'agente dichiara assenza), `energy_class`, `manutenzione`, `locali`, `bagni`, `totPiani`, `shop_windows`. Non usare `mq` come sostituto delle due superfici.

Per uffici servono anche `piano` e `common_services`. Per capannoni servono `internal_height`, `location_accessibility`, `outdoor_spaces`, `construction_year`, `systems_compliance` e `no_offices`, con i valori previsti dallo schema. Non inferire conformità impiantistica, assenza di uffici o caratteristiche sconosciute.

Riunisci i dati mancanti in una richiesta concisa. Una volta ricevuti, continua con lo stesso tool commerciale. Le caratteristiche di posizione e accessibilità sono opzionali: segnala la possibilità di aggiungerle senza bloccare la stima se l'agente non le conosce. Per stimare il canone, ometti `rental_amount` e `estimated_rent` se non noti.

Se il server restituisce `PRICE_RANGE_REQUIRED`, raccogli la scelta `LOW`, `MEDIUM` o `HIGH` e riprova con `options.price_range`. Riporta `UNSUPPORTED_API_MODE` senza cambiare la configurazione del server.

Gli approfondimenti commerciali usano il riferimento del report quando disponibile, altrimenti il medesimo payload in `commercial: { property, options }`. Sezioni OMI, venduti ed energia possono essere assenti: non integrare default residenziali.
