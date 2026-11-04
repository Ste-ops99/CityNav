# CityNav

Sistema di navigazione urbana da terminale, scritto in C. Modella una città come grafo orientato pesato: i nodi sono punti di interesse (POI), gli archi sono strade a senso unico con una lunghezza in metri. Calcola il percorso minimo tra due POI con l'algoritmo di Dijkstra.

All'avvio carica una mappa di esempio di Bologna con 6 POI e 9 strade.

## Funzionalità

- Aggiunta di POI con nome e categoria (trasporti, cultura, ospedali, ristorazione, verde)
- Aggiunta di strade orientate con distanza in metri
- Calcolo del percorso minimo tra due POI, con costo totale e sequenza di tappe
- Rimozione di un POI, con eliminazione di tutte le strade in entrata e in uscita
- Visualizzazione della mappa completa

## Come funziona

- **Grafo**: liste di adiacenza (`Edge* adj_list[]`), un arco per ogni strada
- **Grafo orientato**: le strade sono sensi unici, quindi il percorso A → B può esistere anche se B → A non esiste
- **Percorso minimo**: Dijkstra con array `dist[]`, `prev[]` e `visited[]`; il percorso viene ricostruito risalendo `prev[]` dalla destinazione
- **Memoria**: archi allocati dinamicamente e liberati alla rimozione dei POI e all'uscita

## Struttura

```
main.c   menu interattivo e mappa di esempio
map.h    strutture dati (POI, Edge, Map) e prototipi
map.c    gestione del grafo e algoritmo di Dijkstra
```

## Compilazione ed esecuzione

```bash
gcc -Wall -o citynav main.c map.c
./citynav
```

## Esempio

Percorso da Stazione AV (1) a Mercato delle Erbe (5):

```
=== PERCORSO TROVATO ===
Da: Stazione AV (ID 1)
A: Mercato delle Erbe (ID 5)
Costo totale: 1000.00
Percorso: Stazione AV -> Parco della Montagnola -> Mercato delle Erbe
```

## Contesto

Progetto del corso di Cybersecurity Specialist, ITS Academy Olivetti, marzo 2026.
