# Introduzione e dedica — 2.5.2

## Obiettivo

Riunire nella stessa pagina i due testi editoriali originali del ricettario, mostrando prima l'introduzione e poi la dedica.

## Requisiti

1. La voce di navigazione e il richiamo in prima pagina indicano “Introduzione e dedica”.
2. L'introduzione è riportata integralmente e precede la dedica.
3. I due testi sono separati visivamente e restano leggibili su telefono e in tema scuro.
4. I contenuti vengono letti da `state.editorial`, quindi seguono backup e importazioni.
5. Se un testo manca nello stato importato viene usata la copia incorporata in `RECIPE_SEED`.
6. Nessuna ricetta, fonte, turno, menù o dato salvato viene modificato.

## Verifica

- presenza dei due contenitori nella pagina;
- estrazione completa dei testi originali e rimozione delle sole intestazioni;
- fallback ai dati incorporati;
- sintassi JavaScript;
- versione e cache PWA 2.5.2;
- integrità dell'HTML autonomo e dello ZIP completo.
