# Menù giornaliero modificabile — 2.5.1

## Risultato atteso

Permettere a chi usa l'app di correggere il menù di una singola data senza password, mantenendo protetti gli schemi stagionali generali e i turni.

## Requisiti

1. I pulsanti **Modifica menù del giorno** e **Copia da un altro giorno** sono visibili in modalità pubblica.
2. La variazione può modificare portate, ingredienti, quantità, unità, persone e note.
3. Il salvataggio scrive soltanto `overrides[data]` e non cambia lo schema settimanale.
4. **Usa lo schema stagionale** elimina soltanto la variazione della data selezionata.
5. Gli schemi invernale/estivo, la stagione globale, le persone predefinite, l'importazione completa e i turni richiedono ancora l'accesso operatori.
6. Le variazioni restano locali, offline e incluse nei backup esistenti.

## Casi limite

- Un errore di salvataggio ripristina lo stato precedente e mantiene aperto l'editor.
- Copiare lo stesso giorno è rifiutato.
- Chiudere un editor con modifiche non salvate richiede conferma.
- La scadenza della sessione operatore chiude l'editor solo se si sta modificando uno schema protetto; non interrompe l'editor giornaliero pubblico.

## Verifica

- parsing JavaScript;
- pulsanti giornalieri privi del vincolo operatore;
- salvataggio pubblico della variazione;
- blocco persistente degli schemi e dell'importazione completa;
- compatibilità dei backup e delle chiavi LocalStorage;
- cache PWA e pacchetto autonomo aggiornati alla 2.5.1.
