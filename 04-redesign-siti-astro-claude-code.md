# 4 · Rifacimento di siti aziendali su Astro con Claude Code

**Progetti:** 3 siti aziendali B2B, di cui due da ~95 e ~101 pagine · **Stack:** Astro, Claude Code, Agent Skills

## Il problema

Rifare un sito da 100 pagine con l'AI è veloce, ma è facile sbagliare in modi costosi: contenuti inventati (offerte, promozioni, dati del cliente), pagine perse, redirect dimenticati, SEO rovinata al go-live.

## Cosa ho costruito

Ho creato un **metodo con controlli di verifica automatici**, nato come playbook di prompt in 10 fasi e poi trasformato in una **skill di Claude Code** (`redesign-sito-astro`, versione 3, 6 tappe). Descrizione completa: [redesign-siti-astro](https://github.com/SamuelePrevitali/redesign-siti-astro).

- **Si avvia con una frase**: *"rifacciamo il sito di [cliente]"*.
- **Capisce a che punto è il progetto** e riprende dalla fase giusta.
- **Lavora in una corsa sola**: le domande aperte non la bloccano, finiscono in un elenco unico nel referto finale insieme al registro delle differenze rispetto al sito originale, su cui si dà il via libera.
- Copre tutto il ciclo: riproduzione completa dei contenuti, restyling, revisione UX/UI, audit, alberatura, redirect, go-live, e le passate successive sulle segnalazioni del cliente.

### Il principio: "sostanza identica, forma di oggi"

Il lavoro ha due metà con criteri opposti: i **contenuti** del cliente vanno riprodotti fedelmente, senza inventare nulla; la **forma** (design, UX, performance) va rifatta da zero.

### Regole nate dagli errori

Ogni vincolo della skill esiste perché la sua assenza aveva prodotto un difetto reale. Le regole più importanti stanno nel `CLAUDE.md` del progetto, non nei prompt: *sei degli otto difetti più costosi del primo progetto sarebbero stati evitati da queste righe*.

### Organizzazione tecnica

- I tre siti girano insieme in locale su porte fisse (4321, 4322, 4323), configurate in `astro.config.mjs` e in `.claude/launch.json` per l'anteprima diretta in Claude Code.
- Sitemap attiva solo in produzione, `noindex` in anteprima.

## Risultati

- **3 siti** ricostruiti su Astro con lo stesso metodo.
- Un processo ripetibile che chiunque del team può avviare con una frase.

## Cosa ho imparato

Il valore non sta nel singolo sito, ma nel trasformare l'esperienza di un progetto in uno strumento che rende il successivo più veloce e con meno errori.
