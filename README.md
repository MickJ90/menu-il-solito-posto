# Menù digitale · Il Solito Posto

Sito statico ospitato su GitHub Pages: il QR Code sui tavoli apre il menù in PDF.

- **URL pubblico (codificato nel QR Code):** https://ilsolitoposto.github.io/menu-il-solito-posto/
- Il QR punta alla pagina `index.html`, non direttamente al PDF. La pagina reindirizza subito a `menu.pdf` e mostra un link manuale se il reindirizzamento non parte.

## File

| File | Scopo |
|---|---|
| `index.html` | Pagina di reindirizzamento al PDF |
| `menu.pdf` | Menù corrente |
| `qr-code.svg` / `qr-code.png` | QR Code da stampare |
| `.nojekyll` | Pubblica i file così come sono, senza build Jekyll |

## Aggiornare il menù (il QR Code non cambia)

Il nuovo file deve chiamarsi esattamente `menu.pdf`, tutto minuscolo.

**Dal sito GitHub:** apri il repository → *Add file* → *Upload files* → trascina il nuovo `menu.pdf` → *Commit changes*.

**Da terminale:**

```bash
git add menu.pdf
git commit -m "Update menu"
git push
```

Dopo il push, GitHub Pages pubblica la nuova versione in 1–2 minuti (tab *Actions* del repository). Chi aveva già aperto il menù potrebbe vedere quello vecchio per qualche minuto a causa della cache: basta ricaricare.

## QR Code

Generato in locale con [segno](https://github.com/heuer/segno), libreria Python open source (BSD), senza servizi esterni né redirect di terze parti. QR versione 5, correzione d'errore Q (fino a circa 25% di area danneggiata), bordo di 4 moduli.

- `qr-code.svg`: vettoriale, scalabile senza perdita di qualità. È il formato da dare alla tipografia.
- `qr-code.png`: 1800 × 1800 px a 300 dpi, cioè circa 15 cm di lato senza perdita di qualità.

Per la stampa: almeno 3 cm di lato (consigliati 4–5 cm), nero su bianco e senza tagliare il bordo bianco.

Il QR Code non va rigenerato quando cambia il menù. Serve solo se cambia l'URL pubblico (su Mac usa `python3` al posto di `py`):

```bash
py -m pip install segno
py -m segno.cli --error Q --border 4 --scale 10 --no-size --dark "#000000" --light "#ffffff" --title "Menù Il Solito Posto" --output qr-code.svg "https://ilsolitoposto.github.io/menu-il-solito-posto/"
py -m segno.cli --error Q --border 4 --scale 40 --dpi 300 --dark "#000000" --light "#ffffff" --output qr-code.png "https://ilsolitoposto.github.io/menu-il-solito-posto/"
```

## Da non fare

- Non rinominare il repository e non rinominare né eliminare l'organizzazione `ilsolitoposto`: l'URL del QR Code smetterebbe di funzionare.
- Non rinominare `index.html` e non spostarlo in una sottocartella.
- Non rendere privato il repository: GitHub Pages gratuito funziona solo su repository pubblici.
- Non caricare file riservati: tutto il contenuto del repository è pubblico.
