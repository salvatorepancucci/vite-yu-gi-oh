# Yu-Gi-Oh API Project

## Struttura del Progetto
- `App.vue`: Il componente principale che contiene l'intestazione (`AppHeader.vue`) e la griglia delle carte (`AppCard.vue`).
- `components/AppHeader.vue`: Il componente dell'intestazione che visualizza il titolo dell'applicazione.
- `components/AppCard.vue`: Il componente che gestisce il caricamento dei dati dall'API e visualizza le carte.

## Logica della Soluzione

1. **Componenti**:
   - `App.vue` include l'intestazione e la griglia delle carte.
   - `AppHeader.vue` visualizza il titolo dell'applicazione.
   - `AppCard.vue` gestisce la logica di chiamata all'API e visualizza le carte in un layout a griglia.

2. **Chiamata all'API**:
   - In `AppCard.vue`, viene effettuata una chiamata all'API di YGOPRODeck per ottenere un set di carte limitato utilizzando i parametri `num` e `offset`.
   - I dati delle carte vengono memorizzati nello stato del componente e vengono visualizzati.

3. **Visualizzazione delle Carte**:
   - `AppCard.vue` prende le proprietà della carta (immagine, nome, tipo) e le visualizza in un formato compatto.

4. **Stili**:
   - Viene utilizzato SCSS per la gestione degli stili.
