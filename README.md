# Menù digitale · Il Solito Posto

Sito statico ospitato su GitHub Pages: il QR Code sui tavoli apre il menù in PDF.

- **URL pubblico (codificato nel QR Code):** https://mickj90.github.io/menu-il-solito-posto/
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

## Da non fare

- Non rinominare il repository e non cambiare username GitHub: l'URL del QR Code smetterebbe di funzionare.
- Non rinominare `index.html` e non spostarlo in una sottocartella.
- Non rendere privato il repository: GitHub Pages gratuito funziona solo su repository pubblici.
- Non caricare file riservati: tutto il contenuto del repository è pubblico.
