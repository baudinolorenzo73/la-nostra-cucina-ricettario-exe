# Menù giornaliero · specifica, piano e verifica

## Obiettivo e requisiti
Rendere evidente la modifica di una singola data anche da telefono. Conservare ricette, schemi stagionali, turni e archivi locali usando le stesse chiavi e lo stesso formato dati della 2.2.0.

1. Scelta diretta della data e comando di modifica sopra il calendario.
2. Modifica di portate, persone, ingredienti e note limitata alla data selezionata.
3. Copia da una data a un'altra come bozza da confermare; nessun salvataggio al semplice caricamento della bozza.
4. Avviso alla chiusura di una bozza modificata, via Annulla, X, Escape o ricaricamento (quando il browser lo supporta).
5. Errore di scrittura: conservare il menù precedente in memoria e lasciare aperto l'editor. Applicare lo stesso comportamento al ripristino dello schema.
6. Calendario compatto su telefono, con dettagli sotto e indicatore sui giorni personalizzati. A desktop conservare l'anteprima delle portate.

## Piano e attività completate
- HTML: barra con data/modifica/copia e finestra di copia.
- menu-calendar.js: copia profonda del menù effettivo, confronto bozza, ripristino dello stato se il salvataggio fallisce.
- CSS: griglia del mese e campi dell'editor adattati agli schermi stretti.
- Aggiornamento versione e cache a 2.3.0; HTML autonomo ricostruito dai medesimi sorgenti con Turni incorporato.
- Nessuna dipendenza nuova nell'app.

## Verifica
Test automatici DOM con jsdom: modifica e salvataggio, proporzione 2 kg per 20 persone → 1,2 kg per 12 persone, schema della settimana successiva invariato, rilettura dati, copia solo dopo conferma, avviso Escape, errore di quota con stato precedente conservato, ripristino schema, selezione di una data in un altro mese. Tutti superati.
Parsing JavaScript dei file e degli script incorporati in HTML e Turni: superato.
Controllo pacchetto PWA: eseguito con prepare_pubblica_zip.py.

Limite: in questo ambiente il browser di prova non è disponibile e il download non è riuscito. Resa visiva, stampa, aggiornamento reale della PWA e avvio offline richiedono verifica su browser/dispositivo. Non sono stati eseguiti accessi ai servizi AI.

## Uso e aggiornamento
Calendario menù → Data del menù → Modifica menù del giorno → Salva menù.
Copia da un altro giorno apre una bozza per la data di destinazione: confermare con Salva menù.
Modifica schema continua a cambiare il modello settimanale della stagione selezionata.
Prima dell'aggiornamento esportare il backup completo. Pubblicare il pacchetto allo stesso indirizzo conserva l'accesso ai dati locali; HTML, sito e browser diversi non condividono automaticamente i dati. Per trasferirli usare il backup.

## Miglioramenti consigliati, non implementati
- Lista spesa settimanale ottenuta dagli ingredienti dei menù selezionati, con riepilogo prima di aggiungere prodotti alla spesa comunità.
- Stampa del menù settimanale, utile da esporre in cucina.
- Campi espliciti per allergie e diete delle persone, con avvisi controllabili manualmente.
- Sincronizzazione tra dispositivi: richiede una scelta di archivio condiviso e gestione dei conflitti; il solo salvataggio locale non la fornisce.
- Chiarire la regola delle domeniche: attualmente «1ª e 3ª» significa giorni 1–7 e 15–21 del mese; la quinta settimana non riceve un pranzo precompilato. Il comportamento esistente è conservato e il giorno si può compilare dall'editor.
