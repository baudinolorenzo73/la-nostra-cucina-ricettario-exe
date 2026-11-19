# Elenco persone turni — 2.4.1

## Risultato richiesto

Precaricare nei turni i nomi letti dal prospetto di novembre 2026, includendo le correzioni manoscritte, senza perdere dati locali esistenti.

## Requisiti

1. Inserire: Ana, Valerio, Robi, Monica, Elena, Dario, Brian, Thierry, Max, Paolo, Valentina, Alessandra ed Edo.
2. Confrontare i nomi senza distinguere maiuscole o spazi, evitando duplicati.
3. Nelle installazioni esistenti aggiungere solo i nomi mancanti e conservare eventuali altri nomi.
4. Nei nuovi avvii mostrare subito l'elenco completo.
5. Prima di invalidare un piano attivo coerente, conservarlo nello storico del mese.
6. Applicare la migrazione una sola volta; una successiva eliminazione volontaria non deve essere annullata a ogni apertura.
7. Conservare accessi, ricette, menù, spesa, colori, stampe, backup e funzionamento offline.

## Verifica

- Controllo sintattico dello script dei turni.
- Test statico dell'elenco esatto di 13 nomi e della versione della migrazione.
- Test della migrazione su un archivio precedente con nomi parziali e duplicati equivalenti.
- Controllo del pacchetto PWA, dei percorsi relativi, della cache 2.4.1 e della radice ZIP.
- Controllo dell'HTML autonomo con dati, moduli e documento turni incorporati.
