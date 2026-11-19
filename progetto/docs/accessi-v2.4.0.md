# Accessi pubblici, operatori e master — 2.4.0

## Specifica e matrice dei permessi
Una sola applicazione con modalità pubblica all'avvio, operatore dopo password e proprietario (Lorenzo) dopo master password. Ricette e variazioni del menù giornaliero sono modificabili da tutti. Le altre funzioni di spesa restano disponibili come prima.

| Funzione | Pubblico | Operatore | Lorenzo/master |
| --- | --- | --- | --- |
| Leggere, stampare ed esportare il menù | Sì | Sì | Sì |
| Modificare o copiare il menù di una singola data | Sì | Sì | Sì |
| Modificare schema stagionale e impostazioni generali | No | Sì | Sì |
| Importare un calendario completo | No | Sì | Sì |
| Consultare turni correnti e archiviati | Sì | Sì | Sì |
| Gestire persone, regole, generazione e modifiche turni | No | Sì | Sì |
| Importare turni o ripristinare un backup completo | No | Sì | Sì |
| Aggiungere, modificare e importare ricette | Sì | Sì | Sì |
| Scegliere/reimpostare password operatori | No | No | Sì |
| Salvare o aprire il file accessi cifrato | No | No | Sì |

## Uso
1. Aprire l'app: modalità Pubblico.
2. Lorenzo apre **Accesso operatori** e inserisce la master consegnata separatamente.
3. Sceglie e ripete la password degli operatori, almeno 10 caratteri, poi preme **Salva password operatori**.
4. Per il file esterno reinserisce la master nel campo dedicato e preme **Salva file accessi cifrato**: viene scaricato `Accessi_cucina_cifrati.json`.
5. Su un altro dispositivo, Lorenzo accede con la master e usa **Apri file accessi cifrato**, inserendo nuovamente la master nel campo dedicato. La password operatori diventa disponibile su quel browser.
6. Gli operatori accedono con la propria password. **Torna pubblico**, ricaricamento e 15 minuti di inattività chiudono la sessione. L'attività nella gestione turni conta come attività.

Le modifiche del singolo menù diventano persistenti con Salva menù anche in modalità pubblica; il semplice accesso non salva variazioni. La sessione non viene memorizzata. Solo Lorenzo può reimpostare una password operatori dimenticata. La master resta indipendente dalla password operatori.

## File cifrato e persistenza
- Password operatori: impronta PBKDF2-SHA256, 600.000 iterazioni, salt casuale di 16 byte e derivato di 32 byte. Nel browser non è salvata la password in chiaro.
- Master: generata con 192 bit di casualità, consegnata in un file separato. Nell'app è distribuita soltanto la sua impronta PBKDF2 con salt.
- File esterno: AES-256-GCM, IV casuale di 12 byte per ogni salvataggio, tag di autenticazione a 128 bit e dati associati fissi che identificano il formato. La chiave viene derivata dalla master con PBKDF2-SHA256, 600.000 iterazioni e un salt casuale nuovo per ogni file. Il contenuto cifrato è il verificatore degli operatori, non la password originale.
- La master non viene conservata in memoria di sessione dall'app: viene richiesta per cifrare/decifrare il file, e i campi vengono svuotati. Il gestore password del browser resta sotto il controllo dell'utente.
- File alterati, master errata e formati non riconosciuti vengono rifiutati prima di sostituire la configurazione locale.
- Le credenziali non entrano nei backup ordinari, nei recuperi originali né negli archivi ricette. Il file accessi non contiene menù, ricette o turni.
- L'archivio cifrato non contiene la master: se la master è persa non è possibile recuperarla dal file. Conservare il file riservato di Lorenzo.

## Confini della protezione
È un'app statica e offline. I controlli evitano modifiche dall'interfaccia pubblica e dai normali percorsi dell'app; non impediscono al proprietario del dispositivo di modificare JavaScript, LocalStorage o i file dell'app. Il contenuto di menù e turni non è cifrato, poiché deve essere consultabile da tutti. La cifratura autentica il file degli accessi, non rende inviolabili i permessi nel client.

Per permessi effettivi fra utenti su dispositivi diversi servono autenticazione e autorizzazioni verificate da un server. Non sono presenti sincronizzazione, utenti nominali o revoca centralizzata: aggiornare la password su un dispositivo non aggiorna gli altri. Il sito pubblicato include l'app e i dati iniziali; i dati salvati su un browser restano locali. Trasferire i contenuti con backup e ripristino autorizzato e gli accessi con il file cifrato.

## Piano e attività completate
- Modulo accessi e configurazione master separati dai dati.
- Avvio pubblico; controlli degli schemi, dei turni e delle importazioni complete nascosti o disabilitati, con verifiche prima delle scritture protette.
- Turni pubblici renderizzati senza montare il motore di gestione; nessun accesso diretto al motore da turni.html senza il programma principale sbloccato.
- Logout: chiusura dell'editor dello schema protetto, rimozione iframe di gestione e ritorno alla tabella pubblica; l'editor della singola giornata resta utilizzabile.
- Backup completo accessibile in esportazione; ripristino completo e import Turni riservati agli operatori. Import ricette resta pubblico.
- Archivio cifrato portabile riservato alla master; nessuna dipendenza nuova nell'app.
- Cache 2.4.0 con moduli accessi inclusi; stessi dati applicativi e chiavi locali delle versioni precedenti.

## Verifica e limiti di collaudo
La versione 2.4.0 è stata verificata automaticamente con DOM jsdom e Web Crypto reale per accessi, cifratura, turni e permessi originari. La regressione 2.5.1 verifica inoltre: pulsanti giornalieri pubblici, scrittura reale di una variazione nel LocalStorage senza sessione operatore, separazione dagli schemi, permanenza dei controlli su schema, impostazioni generali e import completo, parsing degli script e integrità del pacchetto PWA.

Regressione menù superata: portate, dosi, separazione dallo schema, copia come bozza, rilettura dati, annullamento, quota esaurita e ripristino stagionale.

Non verificati con browser reale in questo ambiente: resa visiva, download/import su Android e iPhone, aggiornamento reale PWA e apertura offline. Verificare su dispositivi reali. Gli accessi usano Web Crypto: per la PWA pubblicata usare HTTPS e un browser aggiornato; senza supporto l'accesso fallisce mantenendo la modalità pubblica.

Fonti tecniche: https://www.w3.org/TR/webcrypto/ e https://developer.mozilla.org/en-US/docs/Web/API/SubtleCrypto/deriveBits .

## Aggiornamento
Esportare un backup completo prima dell'aggiornamento. Sostituire i file pubblicati allo stesso indirizzo. Conservare l'accesso master fuori dal pacchetto pubblico. Chiudere le schede dell'app per consentire l'attivazione dell'aggiornamento. Non pubblicare il file riservato di Lorenzo.
