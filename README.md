# Pagina di presentazione di Nautilus DiveKit

Questa cartella è il sito di presentazione dell'app **Nautilus DiveKit**: una
pagina sola, nelle sei lingue dell'app (italiano, inglese, spagnolo, francese,
tedesco e portoghese), con i due pulsanti per scaricarla.

Indirizzo una volta pubblicata:
**https://sgambaroapps.github.io/nautilusdivekit/**

È lo stesso indirizzo che l'app usa nella voce «Consiglia l'app»: chi lo riceve
apre la pagina e trova il pulsante giusto per il proprio telefono, che sia
Android o iPhone.

> Le pagine di **privacy** e **assistenza** restano dove sono
> (repository `nautilus-privacy`): quegli indirizzi sono dichiarati a Google
> Play e ad Apple e non vanno toccati. Questa pagina li richiama in fondo.

---

## 1. Pubblicarla su GitHub Pages (una volta sola)

1. Su GitHub, con l'account `sgambaroapps`, crea un repository **pubblico**
   chiamato esattamente `nautilusdivekit` (senza spazi, tutto minuscolo).
2. Carica il contenuto di questa cartella: `index.html`, la cartella `assets`
   e questo README. Si può fare trascinando i file nella pagina del repository
   ("Add file" → "Upload files"), oppure da riga di comando.
3. Nel repository: **Settings** → **Pages** → in *Build and deployment*
   scegli *Deploy from a branch*, ramo `main`, cartella `/ (root)` → **Save**.
4. Dopo un minuto o due la pagina è online all'indirizzo qui sopra. Provalo
   anche dal telefono.

Per aggiornarla in futuro basta ricaricare i file cambiati.

---

## 2. Mettere i banner ufficiali degli store

I due pulsanti funzionano già anche senza banner (compare un pulsante bianco con
scritto *Google Play* / *App Store*). Per usare i banner ufficiali, mettili in
`assets/badge/` con **questi nomi esatti**:

| File da creare                   | Dove si scarica                                        |
| -------------------------------- | ------------------------------------------------------ |
| `assets/badge/google-play-it.png` | https://play.google.com/intl/it/badges/ (generatore)  |
| `assets/badge/google-play-en.png` | stesso generatore, lingua inglese                     |
| `assets/badge/google-play-es.png` | stesso generatore, lingua spagnola                    |
| `assets/badge/google-play-fr.png` | stesso generatore, lingua francese                    |
| `assets/badge/google-play-de.png` | stesso generatore, lingua tedesca                     |
| `assets/badge/google-play-pt.png` | stesso generatore, lingua portoghese                  |
| `assets/badge/app-store-it.svg`   | https://developer.apple.com/app-store/marketing/guidelines/ |
| `assets/badge/app-store-en.svg`   | idem, lingua inglese                                   |
| `assets/badge/app-store-es.svg`   | idem, lingua spagnola                                  |
| `assets/badge/app-store-fr.svg`   | idem, lingua francese                                  |
| `assets/badge/app-store-de.svg`   | idem, lingua tedesca                                   |
| `assets/badge/app-store-pt.svg`   | idem, lingua portoghese                                |

Se di una lingua non hai il banner, quella lingua mostra il pulsante bianco di
riserva: non si rompe niente. Se il banner di Apple che scarichi è un `.png` e
non un `.svg`, **non** rinominarlo: dimmelo e cambio io il riferimento nella
pagina (rinominare un PNG in SVG lo rende illeggibile al browser).

---

## 3. Accendere i pulsanti quando l'app esce davvero

Finché gli store non sono pubblici la pagina scrive *«In arrivo su Google
Play»* e *«In arrivo su App Store»*: è voluto, così si può già far girare
l'indirizzo senza mandare nessuno su una pagina che non esiste.

Quando uno store va in linea, apri `index.html` con il Blocco note, cerca
questa riga (è quasi in fondo, dentro `<script>`):

```js
var STORE_VIVI = { android: false, ios: false };
```

e metti `true` a quello pubblicato. Per esempio, quando esce solo iOS:

```js
var STORE_VIVI = { android: false, ios: true };
```

Salva, ricarica il file su GitHub, ricarica la pagina nel browser: al posto
della scritta compare il pulsante che porta alla scheda. Non serve altro.

Gli indirizzi delle schede sono già scritti nella pagina:

- Google Play → `https://play.google.com/store/apps/details?id=com.sgambaroapps.nautilus`
- App Store → `https://apps.apple.com/app/id6811002242`

---

## 4. Com'è fatta

- **Un file solo** (`index.html`, circa 60 KB) con dentro tutte e sei le
  lingue: la pagina mostra quella del browser e si cambia con i pulsantini in
  alto a destra. Senza JavaScript si vedono tutte le lingue una sotto l'altra,
  quindi si legge comunque.
- `assets/shots/` contiene 5 schermate per lingua, già rimpicciolite per il
  web; `assets/icona.png` è l'icona dell'app; `assets/og.jpg` è l'immagine che
  compare quando il link viene mandato su WhatsApp o pubblicato su Facebook.
- **Nessun tracciamento**: niente cookie, niente statistiche, nessuna chiamata a
  servizi esterni. Coerente con quello che l'app promette. Quanta gente arriva
  agli store lo dicono già Play Console e App Store Connect.
- Per sapere quale lingua è arrivata da dove puoi usare indirizzi come
  `.../nautilusdivekit/#fr`: la pagina si apre direttamente in francese.

## 5. Se vuoi cambiare i testi

La pagina è generata da uno script che tiene allineate le sei lingue:
`D:\APP Nautilus ALTRO\materiali-lancio\sorgenti\genera_sito.py`.
Si modificano i testi là dentro e si rigenera tutto. Modificare `index.html` a
mano funziona lo stesso, ma poi il testo cambiato va ripetuto in ognuna delle
sei sezioni.
