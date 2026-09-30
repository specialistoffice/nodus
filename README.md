# nodus — Engineering MEP Supports

Web app per il dimensionamento di staffaggi MEP (tubazioni, passerelle/canaline, canali aria):
pesi lineari e puntuali, catalogo staffaggi (produttori industriali + profili Eurocodice EN 10025),
verifiche NTC 2018 / EC3, verifica sismica, diagrammi M/V/w, distinta materiali ed export.

## Pubblicazione su GitHub Pages

1. Crea (o apri) la repository su GitHub, anche dentro la tua organizzazione.
2. Carica in questa repo i 5 file di questa cartella: `index.html`, `manifest.webmanifest`,
   `apple-touch-icon.png`, `icon-192.png`, `icon-512.png` (tutti nella **radice** della repo,
   non in una sottocartella).
3. Vai su **Settings → Pages**. In "Source" scegli "Deploy from a branch", branch `main`,
   cartella `/ (root)`. Salva.
4. Dopo un paio di minuti il sito è online su:
   `https://<nome-organizzazione>.github.io/<nome-repo>/`

Il nome della repository può essere qualunque cosa: non serve più rinominarla o farla
coincidere col nome del progetto (vedi nota sotto).

## Perché l'icona sulla Home falliva con 404

Su GitHub Pages con un progetto dentro un'organizzazione, l'indirizzo del sito include
il nome della repository (`.../nome-repo/`), non solo il dominio. Il `manifest.webmanifest`
generato in precedenza aveva `"start_url": "/"`: un percorso assoluto, che punta sempre e solo
alla radice del dominio (`org.github.io/`), ignorando il nome della repo. Aprendo il sito da
Safari funzionava (Safari segue l'indirizzo che hai digitato), ma l'icona in Home Screen usa lo
`start_url` del manifest per aprire l'app, finendo sulla pagina 404 della radice.

In questo pacchetto `start_url` e `scope` sono impostati su `"./"` (percorso relativo): puntano
sempre alla cartella in cui si trova il manifest stesso, qualunque sia il nome della repo o
dell'organizzazione. Se in futuro crei un altro progetto in una repo diversa, funzionerà allo
stesso modo senza bisogno di rinominare nulla.

## Aggiornare l'icona sull'iPhone dopo questa modifica

Il manifest viene letto quando aggiungi l'app alla Home la prima volta; se l'avevi già
aggiunta con la versione precedente, rimuovi l'icona dalla Home e ripeti "Aggiungi a Home"
da Safari dopo aver pubblicato questi file aggiornati, altrimenti continuerà a usare la
configurazione vecchia salvata sul telefono.

## Struttura dei file

- `index.html` — l'intera applicazione (HTML + CSS + JS in un unico file, nessuna build necessaria)
- `manifest.webmanifest` — nome, icone, `start_url`/`scope` relativi e modalità "standalone"
- `apple-touch-icon.png`, `icon-192.png`, `icon-512.png` — icone generate dal logo "n"

## Nota

L'app richiede connessione internet: carica Tailwind CSS, Font Awesome e i font Google da CDN.
Il motore di calcolo è interamente lato client (nessun server, nessun dato inviato altrove).
