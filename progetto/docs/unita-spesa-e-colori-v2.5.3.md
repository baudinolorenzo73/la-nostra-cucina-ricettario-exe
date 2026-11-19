# Unità della spesa e colori delle sezioni — 2.5.3

## Obiettivo

Rendere le quantità della Spesa comunità non ambigue e distinguere visivamente le aree principali dell'app.

## Requisiti verificabili

- Ogni prodotto della Spesa comunità conserva separatamente quantità e unità.
- Le unità disponibili sono: nessuna, pz, gr, lt, conf e altro.
- L'unità si può scegliere nell'elenco, nel modulo di aggiunta e nella modifica del prodotto.
- Stampa A4 e CSV includono l'unità senza aggiungere pagine o colonne visive inutili alla stampa.
- Gli archivi precedenti privi del campo `unit` vengono caricati con unità vuota, senza perdere dati.
- Ricette, turni, calendario e spesa hanno colori distinti e leggibili nei temi chiaro e scuro.
- Restano invariati salvataggio giornaliero, copia della giornata, backup, importazione e funzionamento offline.

## Scelte tecniche

Il campo `unit` usa abbreviazioni stabili (`pz`, `gr`, `lt`, `conf`, `altro`). L'opzione Altro non aggiunge testo automatico alla stampa: consente di scrivere una quantità libera, per esempio “2 scatole grandi”. Le unità note vengono invece stampate in forma compatta, per esempio “500 gr”.

I colori delle aree sono applicati con variabili CSS locali e mescolati con il colore dei riquadri del tema attivo. Non cambiano i dati né le stampe.

## Collaudo

- apertura e migrazione di una giornata salvata senza unità;
- salvataggio e riapertura delle cinque unità;
- aggiunta e modifica di un prodotto;
- presenza di quantità e unità in stampa e CSV;
- controllo sintattico degli script e delle risorse offline;
- verifica del pacchetto ZIP installabile.
