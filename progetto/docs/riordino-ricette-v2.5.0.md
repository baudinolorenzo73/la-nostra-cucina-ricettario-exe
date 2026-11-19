# Riordino ricette — 2.5.0

## Comportamento

- “Ordine personale” è l'ordinamento iniziale della prima pagina.
- Pressione prolungata di 500 ms, trascinamento e rilascio spostano una scheda.
- Il movimento è disponibile con touch, penna e mouse.
- Ricerca, categorie, “Solo da verificare” e vista Preferite disattivano il riordino per non salvare un sottoinsieme.
- Un movimento iniziale superiore a 10 pixel annulla la pressione prolungata e lascia scorrere normalmente la pagina.
- Il clic successivo a un trascinamento viene ignorato, quindi non apre per errore la ricetta.

## Dati e compatibilità

L'ordine è memorizzato nell'array `recipeOrder` del normale archivio ricette. Durante caricamento, salvataggio e importazione l'array viene normalizzato: ID sconosciuti o duplicati sono eliminati e le ricette mancanti vengono aggiunte in fondo. I backup vecchi senza `recipeOrder` sono quindi compatibili.

## Controlli

- sintassi JavaScript;
- presenza degli elementi e degli stili di riordino;
- migrazione di un archivio precedente;
- normalizzazione di ID duplicati, sconosciuti e mancanti;
- inclusione dell'ordine nei backup;
- integrità del pacchetto PWA e del file HTML autonomo.
