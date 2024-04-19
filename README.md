# BoolFlix (vite-boolflix)

Questo progetto è una web-app sviluppata con Vue.js che replica la logica di siti di streaming di film e serie TV come Netflix. L'applicazione utilizza l'API di The Movie Database (TMDB) per effettuare ricerche e visualizzare i risultati relativi a film e serie TV.

## Descrizione

BoolFlix consente agli utenti di cercare film e serie TV tramite una barra di ricerca. I risultati vengono recuperati dall'API di TMDB e visualizzati in un layout simile a Netflix, con un elenco di card contenenti informazioni come titolo, titolo originale, lingua, voto e copertina del film/serie.

L'applicazione offre diverse funzionalità, tra cui:

- Ricerca di film e serie TV tramite una barra di ricerca
- Visualizzazione dei risultati in un layout simile a Netflix
- Rappresentazione della lingua con bandiere dei paesi corrispondenti
- Conversione del voto da un valore decimale a un numero di stelle piene da 1 a 5
- Visualizzazione dell'anteprima del film/serie TV al passaggio del mouse sulla relativa card
- Gestione dei casi in cui non sono disponibili alcune informazioni o immagini

## Tecnologie utilizzate

- Vue.js
- Axios (o altra libreria per le chiamate AJAX)
- The Movie Database API

## Installazione

1. Clonare il repository
2. Eseguire `npm install` per installare le dipendenze
3. Eseguire `npm run dev` per avviare l'applicazione in modalità di sviluppo
4. Aprire l'URL specificato dal server di sviluppo nel browser

## Struttura del progetto

- `src/App.vue`: Componente principale dell'applicazione che contiene le funzioni per effettuare le chiamate all'API di TMDB
- `src/components/AppHeader.vue`: Componente per la barra di ricerca
- `src/components/AppMain.vue`: Componente dove vengono create le card di un film/serie TV

## Note

- Per poter utilizzare l'API di TMDB, è necessario iscriversi al sito https://www.themoviedb.org e ottenere una chiave API personale.
- La web-app è stata progettata seguendo le linee guida fornite durante l'esercizio, con particolare attenzione alla progettazione del global state e all'implementazione graduale delle funzionalità.