# Foto ricette e selezione rapida della spesa — 2.5.4

## Risultato atteso

Consentire di associare una fotografia a ogni ricetta da telefono o computer e velocizzare la selezione dei prodotti nella Spesa comunità.

## Requisiti verificabili

- L'editor offre due ingressi distinti: galleria e fotocamera posteriore.
- Sono accettati soltanto file immagine fino a 20 MB.
- La foto viene ridimensionata, compressa in JPEG e limitata a circa 180.000 caratteri per contenere l'uso dello spazio locale.
- La conversione tramite canvas elimina EXIF e coordinate GPS.
- Anteprima, sostituzione e rimozione sono disponibili prima del salvataggio.
- La foto compare sulla scheda e nella ricetta aperta ed è inclusa in esportazione e ripristino del backup.
- I backup precedenti senza foto restano compatibili.
- Se lo spazio locale è esaurito, il salvataggio fallisce senza chiudere l'editor.
- La Spesa comunità offre selezione totale, deselezione totale e inversione.
- Le azioni di selezione non modificano quantità, unità, supermercato o testo ALTRO.

## Confini

Le fotografie sono salvate nel browser insieme alle ricette e non vengono caricate su servizi esterni. Molte fotografie possono raggiungere il limite di spazio del browser: l'app comprime ogni immagine e segnala l'errore senza perdere la bozza aperta.

## Verifiche

- controllo sintattico degli script;
- validazione di backup con e senza foto;
- rifiuto di immagini non valide o troppo grandi;
- presenza dei controlli galleria, fotocamera e rimozione;
- visualizzazione su scheda e dettaglio;
- controllo dei tre comandi di selezione e della persistenza;
- integrità dello ZIP PWA e cache offline aggiornata.
