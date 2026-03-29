# Deploy su GitHub Pages — SESTO Event Project Management

## Struttura del repository

Il sito è una applicazione HTML/CSS/JS statica, pronta per GitHub Pages senza alcuna configurazione aggiuntiva.

```
/
├── index.html            ← selettore lingua (home)
├── .nojekyll             ← disabilita Jekyll (obbligatorio)
├── CNAME                 ← dominio custom: sestoeventi.it
├── css/
│   └── style.css
├── img/
├── favicon.ico / .svg / .png
├── it/
│   ├── index.html
│   ├── chi-siamo.html
│   ├── servizi.html
│   ├── ...
│   ├── privacy-policy.html
│   └── cookie-policy.html
└── en/
    ├── index.html
    ├── about.html
    ├── services.html
    ├── ...
    ├── privacy-policy.html
    └── cookie-policy.html
```

---

## Prima pubblicazione — passo dopo passo

### 1. Crea un repository su GitHub

1. Vai su [github.com](https://github.com) e accedi al tuo account.
2. Clicca su **"New repository"**.
3. Nome consigliato: `sestoeventi` oppure `sesto-website`.
4. Imposta il repository come **Public** (necessario per GitHub Pages gratuito) oppure **Private** se hai GitHub Pro/Team.
5. Non aggiungere README né .gitignore — la cartella è già pronta.
6. Clicca **"Create repository"**.

### 2. Carica i file sul repository

**Opzione A — da terminale (consigliato):**

```bash
cd "AGENZIA SITO"          # entra nella cartella del sito

git init
git add .
git commit -m "Prima pubblicazione sito SESTO"

git remote add origin https://github.com/TUO-USERNAME/sestoeventi.git
git branch -M main
git push -u origin main
```

**Opzione B — tramite interfaccia web:**

1. Nel repository appena creato, clicca **"uploading an existing file"**.
2. Trascina tutti i file e le cartelle del sito.
3. Clicca **"Commit changes"**.

> ⚠️ Assicurati di caricare anche il file `.nojekyll` (inizia con punto, potrebbe essere nascosto).

### 3. Attiva GitHub Pages

1. Nel repository, vai su **Settings → Pages** (pannello a sinistra).
2. Alla voce **"Source"**, seleziona:
   - Branch: `main`
   - Cartella: `/ (root)`
3. Clicca **Save**.
4. GitHub mostrerà l'URL temporaneo: `https://tuo-username.github.io/sestoeventi/`

---

## Configurazione dominio custom (sestoeventi.it)

Il file `CNAME` nella root del sito contiene già `sestoeventi.it`.

### Configurazione DNS presso il tuo provider

Aggiungi questi record DNS nel pannello del tuo registrar/hosting:

| Tipo  | Nome (Host) | Valore                   |
|-------|-------------|--------------------------|
| A     | @           | 185.199.108.153          |
| A     | @           | 185.199.109.153          |
| A     | @           | 185.199.110.153          |
| A     | @           | 185.199.111.153          |
| CNAME | www         | tuo-username.github.io.  |

> I record A puntano ai server di GitHub Pages. Sostituisci `tuo-username` con il tuo username GitHub.

### Attiva HTTPS (obbligatorio per GDPR)

Dopo aver configurato il DNS (può richiedere fino a 48h):

1. Torna su **Settings → Pages** nel repository.
2. Alla voce **"Custom domain"**, inserisci `sestoeventi.it` e salva.
3. Spunta **"Enforce HTTPS"**.

---

## Aggiornamenti futuri

Per aggiornare il sito dopo le modifiche iniziali:

```bash
git add .
git commit -m "Descrizione della modifica"
git push
```

GitHub Pages aggiorna automaticamente il sito entro 1-2 minuti.

---

## Note tecniche

- **`.nojekyll`**: impedisce a GitHub di elaborare il sito con Jekyll, che potrebbe causare errori con certi nomi di file e cartelle.
- **Formspree**: il form di contatto usa Formspree (`formspree.io/f/mzdkezow`). Per ricevere le email, accedi al pannello Formspree e verifica l'indirizzo `info@sestoeventi.it`.
- **Google Fonts**: il font Cormorant Garamond è caricato esternamente da Google Fonts. Assicurati di avere connessione internet per visualizzarlo correttamente.
- **Tutti i percorsi sono relativi**: non ci sono percorsi assoluti nel codice, quindi il sito funziona sia su dominio root che su sottocartella.
