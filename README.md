# 📖 Flipbook interattivo

Un flipbook (libro sfogliabile) realizzato con HTML, CSS e JavaScript. Mostra le tue
immagini come un vero libro: copertina singola, pagine affiancate e retro copertina.

---

## 📁 Cosa contiene questa cartella

| File | Descrizione |
|------|-------------|
| `index.html` | La pagina principale del flipbook (qui si modifica tutto). |
| `page-flip.browser.js` | La libreria "StPageFlip" che fa funzionare lo sfoglio (**non modificarla**). |
| `page-flip-leggibile.txt` | Codice sorgente leggibile della libreria, solo a scopo di studio (**non usato dalla pagina**). |
| `img/Immagine1.jpg` | Copertina (pagina singola). |
| `img/Immagine2.jpg` … `img/Immagine6.jpg` | Le altre pagine del libro. |
| `img/ImmagineSfondo.jpg` | Immagine di sfondo dietro al libro. |

---

## 🚀 Come farlo partire da zero (locale)

### Prima cosa da sapere: NON serve installare nulla

Il progetto è **statico**: non richiede Node.js, Python, database o altri programmi.
Tutto ciò che serve è già nella cartella:

- un browser (Chrome, Edge, Firefox, Safari…);
- i 3 tipi di file qui sopra (HTML + JavaScript + immagini).

### Metodo 1 — Il più semplice: doppio clic

1. Apri la cartella del progetto.
2. Fai **doppio clic su `index.html`**.
3. Il flipbook si apre nel browser.

> ⚠️ In rari casi, a seconda del browser e delle impostazioni di sicurezza, il
> doppio clic potrebbe non caricare correttamente le immagini. Se vedi il libro ma
> le pagine sono vuote, usa il Metodo 2 qui sotto.

### Metodo 2 — Server locale (consigliato, sempre funzionante)

Un piccolo server locale è il modo più affidabile per testare il flipbook. Scegli una
delle due opzioni seguenti.

#### Opzione A — Con Python (se è installato)

Apri il terminale nella cartella del progetto e digita:

```bash
python -m http.server 8000
```

Poi apri il browser e vai su: **http://localhost:8000**

Per fermare il server: premi `Ctrl + C` nel terminale.

#### Opzione B — Con Visual Studio Code (estensione "Live Server")

1. Apri la cartella del progetto in Visual Studio Code.
2. Installa l'estensione **Live Server** (di Ritwick Dey).
3. Clicca con il tasto destro su `index.html` → **Open with Live Server**.
4. Il flipbook si apre nel browser.

---

## 🌍 Come metterlo online (deploy)

Il progetto è auto-contenuto: non dipende da nessun servizio esterno. Per pubblicarlo
basta **caricare l'intera cartella** su un qualsiasi hosting (Aruba, Netlify, Vercel,
GitHub Pages, WordPress, ecc.).

Requisiti: devono esserci tutti questi file insieme, nello stesso percorso:

```
flipbook/
├── index.html
├── page-flip.browser.js
├── page-flip-leggibile.txt   (facoltativo, solo lettura)
├── README.md
└── img/
    ├── Immagine1.jpg
    ├── Immagine2.jpg
    ├── Immagine3.jpg
    ├── Immagine4.jpg
    ├── Immagine5.jpg
    ├── Immagine6.jpg
    └── ImmagineSfondo.jpg
```

### Collegarlo da un'altra pagina (bottone/link)

Non servono librerie nella pagina che ospita il bottone: basta un normale link HTML.

```html
<a href="flipbook/index.html">📖 Apri il flipbook</a>
```

Oppure, sotto forma di bottone:

```html
<a href="flipbook/index.html">
  <button>Apri il flipbook</button>
</a>
```

> Assicurati che il percorso `href` punti correttamente alla posizione del file
> `index.html` sul tuo hosting.

---

## 🖼️ Come cambiare le immagini

Apri `index.html` con un editor di testo (Blocco note, VS Code, ecc.) e cerca la
sezione evidenziata dal commento:

```html
<!-- ============================================================
     LIBRO: QUI CI SONO LE PAGINE
     ...
     ============================================================ -->
```

Lì troverai i blocchi delle pagine, uno per ogni immagine:

```html
<!-- PAGINA 1 — COPERTINA (da sola) -->
<div class="page">
    <img src="img/Immagine1.jpg" alt="Copertina">
</div>
```

### Metodo A — Modificare il nome nel file HTML (consigliato)

Sostituisci solo il nome del file dentro `src="..."`.

**Esempio:** vuoi usare `foto_mia.jpg` come copertina? Cambia questo:

```html
<img src="img/Immagine1.jpg" alt="Copertina">
```

in questo:

```html
<img src="img/foto_mia.jpg" alt="Copertina">
```

Il file `foto_mia.jpg` **deve trovarsi dentro la cartella `img/`**.

### Metodo B — Tenere gli stessi nomi (più rapido)

Sostituisci i file originali mantenendo lo stesso nome:

- elimina (o rinomina) `img/Immagine1.jpg`;
- copia la tua nuova immagine nella cartella `img/`;
- rinominala `Immagine1.jpg`.

In questo modo non devi toccare il codice HTML.

### Cambiare l'immagine di sfondo

Lo sfondo della pagina (dietro al libro) usa `ImmagineSfondo.jpg`. Per cambiarlo:

1. Apri `index.html`.
2. Cerca in alto nel CSS questa variabile:
   ```css
   :root {
       --sfondo: url("img/ImmagineSfondo.jpg");
   }
   ```
3. Sostituisci `ImmagineSfondo.jpg` con il nome del tuo file (es. `mare.jpg`).
4. Copia il file dentro la cartella `img/`.

Consiglio: usa un'immagine orizzontale ad alta risoluzione (es. 1920×1080 px) per
coprire bene lo schermo.

### Formati e dimensioni consigliate

- **Formati supportati:** JPG, PNG, WebP, GIF (consigliati: JPG o WebP).
- **Consiglio dimensioni:** le tue foto sono molto grandi (2000–5500 px). Vanno bene,
  ma per un caricamento più veloce online conviene ridurle a circa **800×1200 px**
  (larghezza × altezza). Il flipbook funziona comunque anche con foto grandi.
- Le immagini vengono ridimensionate automaticamente per riempire la pagina senza
  deformarsi (`object-fit: cover`).

---

## ➕ Come aggiungere pagine

Le pagine si aggiungono **sempre a coppie (due per volta)** per mantenere il formato
"libro aperto": copertina singola → pagine a due a due → retro copertina singola.

### Passaggi

1. Apri `index.html`.
2. Trova il commento `<!-- FINE LIBRO: aggiungi qui sopra eventuali nuove pagine -->`.
3. Copia e incolla **due** nuovi blocchi pagina **prima** di quel commento, ad esempio:

```html
<!-- NUOVA PAGINA -->
<div class="page">
    <img src="img/Immagine7.jpg" alt="Pagina 7">
</div>

<!-- NUOVA PAGINA -->
<div class="page">
    <img src="img/Immagine8.jpg" alt="Pagina 8">
</div>
```

4. Salva il file.

Il numero di pagine viene calcolato automaticamente: **non devi aggiornare nessun
conteggio a mano**.

### Ordine delle pagine nel libro

Con `showCover: true`, la libreria interpreta così l'ordine:

| Posizione nel libro | Pagina |
|---------------------|--------|
| Copertina | 1ª pagina del codice |
| Doppia pagina | 2ª + 3ª pagina |
| Doppia pagina | 4ª + 5ª pagina |
| … | continua a coppie |
| Retro copertina | ultima pagina del codice |

---

## ➖ Come rimuovere pagine

1. Apri `index.html`.
2. Elimina i blocchi `<div class="page"> ... </div>` che vuoi togliere.
3. Salva.

Ricorda di rimuovere le pagine **a coppie** (tranne copertina e retro copertina) per
mantenere il formato corretto.

---

## 🔧 Opzioni di configurazione (facoltativo)

Nella parte JavaScript di `index.html` trovi le impostazioni del flipbook:

```js
const pageFlip = new St.PageFlip(document.getElementById("flipbook"), {
    width: 750,          // larghezza di una pagina (proporzione)
    height: 1000,        // altezza di una pagina (proporzione)
    showCover: true,     // copertina e retro copertina singole
    flippingTime: 800,   // durata animazione in millisecondi
    // ...
});
```

Le più utili da cambiare:

| Opzione | Valore di default | Cosa fa |
|---------|-------------------|---------|
| `width` / `height` | `750` / `1000` | Proporzioni della pagina (rapporto 3:4 verticale). |
| `showCover` | `true` | Se `true`: copertina e retro copertina singole. Se `false`: tutte pagine affiancate. |
| `flippingTime` | `800` | Velocità dello sfoglio (millisecondi). Valori più bassi = più veloce. |
| `drawShadow` | `true` | Ombre realistiche durante lo sfoglio. |
| `usePortrait` | `true` | Su schermi stretti mostra una pagina alla volta; su schermi larghi due pagine affiancate. |

---

## 🎬 Comportamento del libro (apertura e centraggio)

La pagina è composta solo dal libro, senza riquadro bianco, titolo, pulsanti o
contatore. Lo sfondo è un'immagine (vedi "Cambiare l'immagine di sfondo").

**Come si sfoglia:**
- su **smartphone**: con il dito (swipe o tocco sulla pagina);
- su **desktop**: click/trascinamento sulla pagina oppure **frecce della tastiera** (← →).

Il libro ha un **centraggio dinamico**:

- **Su desktop/tablet orizzontale (due pagine affiancate):**
  - **Libro chiuso (copertina):** la copertina è centrata da sola al centro dello
    schermo.
  - **Prima apertura:** quando apri la prima pagina, il libro scorre dolcemente per
    portare al centro la rilegatura (il punto tra le due pagine).
  - **Ultima pagina (retro copertina):** il libro scorre per centrare la retro
    copertina da sola.

- **Su smartphone (una pagina alla volta):** la pagina è già centrata dalla libreria,
  senza spostamenti laterali. La modalità viene scelta automaticamente grazie a
  `usePortrait: true`.

### 📱 Ottimizzazioni mobile

Su schermi piccoli (`max-width: 600px`) il progetto applica alcune rifiniture:
- il libro **occupa tutto lo schermo** (padding azzerato);
- niente lampeggio blu al tocco (`-webkit-tap-highlight-color`);
- niente selezione accidentale del testo durante lo sfoglio (`user-select: none`);
- altezza gestita con `100dvh` per la barra del browser dei telefoni.

Questo effetto è gestito dal JavaScript nel blocco "CENTRAGGIO DINAMICO DEL LIBRO"
di `index.html` e dalla transizione CSS:

```css
#book-wrapper {
    transition: transform 0.7s ease;
}
```

**Come regolarlo:**

| Valore | Dove | Cosa fa |
|--------|------|---------|
| `0.7s` | CSS `#book-wrapper` | Durata dello scorrimento del libro. |

### Sfogliata animata delle pagine (già inclusa)

L'animazione di piegamento e rotazione delle pagine è già fornita dalla libreria
StPageFlip e non richiede modifiche. La velocità si controlla con l'opzione
`flippingTime` (in millisecondi) tra le impostazioni del flipbook: valori più bassi =
sfogliata più veloce.

---

## ❓ Risoluzione problemi (FAQ)

### Le immagini non si vedono (pagine bianche/icone rotte)

- Controlla che il nome nel `src="..."` sia **identico** al nome del file
  (attenzione a maiuscole/minuscole, spazi e accenti).
- Controlla che le immagini siano **dentro la cartella `img/`** e che il
  percorso nel `src` inizi con `img/`.
- Se hai aperto il file con doppio clic e le pagine sono vuote, prova il **Metodo 2**
  (server locale) descritto sopra.

### Il libro non sfoglia

- Controlla che `page-flip.browser.js` sia presente nella stessa cartella.
- Assicurati di non aver modificato il tag:
  ```html
  <script src="page-flip.browser.js"></script>
  ```

### Ho aggiunto una pagina singola e il formato è sbagliato

- Ricorda: le pagine vanno aggiunte **a coppie**. Se aggiungi un numero dispari di
  pagine centrali, l'ultima resterà "da sola" e il libro non sarà ben bilanciato.

### Voglio cambiare lo sfondo della pagina

- Vedi la sezione "Cambiare l'immagine di sfondo": modifica il nome del file
  nella variabile `--sfondo` in cima al CSS di `index.html`.

---

## 🔗 Riferimenti

- Libreria **StPageFlip**: https://github.com/Nodlik/StPageFlip
- Documentazione: https://nodlik.github.io/StPageFlip/

---

## 📝 Riepilogo rapido

1. **Avviare:** doppio clic su `index.html` (o server locale).
2. **Cambiare immagini:** modifica `src="..."` oppure sostituisci i file mantenendo
   gli stessi nomi.
3. **Cambiare sfondo:** modifica il nome dentro `--sfondo: url("...")` nel CSS.
4. **Aggiungere pagine:** incolla due nuovi blocchi `<div class="page">...</div>`
   prima del commento "FINE LIBRO".
5. **Mettere online:** carica l'intera cartella su qualsiasi hosting.
6. **Non serve installare nulla.**
