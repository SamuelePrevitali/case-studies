# 2 · Pipeline editoriale multi-agente per un blog tecnico B2B

**Cliente:** azienda industriale B2B · **Stack:** Claude Agent Skills, NeuronWriter via MCP, SEO

## Il problema

Il blog doveva parlare a responsabili di stabilimento e uffici tecnici: lettori competenti che si accorgono subito di un testo generico o "scritto dall'AI". Servivano tanti articoli, ma ognuno doveva sembrare scritto da un tecnico esperto.

## Cosa ho costruito

Quattro skill che si dividono il lavoro come una piccola redazione:

| Skill | Ruolo |
|---|---|
| **editor** | Direttore editoriale: analizza i contenuti esistenti, trova i gap SEO (volume, difficoltà, intento), costruisce il piano, assegna il lavoro e traccia lo stato degli articoli |
| **writer** | Scrive con la voce di un tecnico senior con 20+ anni di esperienza: spiega la logica progettuale, non vende |
| **reviewer** | Rilegge e corregge chirurgicamente ciò che suona artificiale, generico o promozionale, senza toccare il contenuto tecnico |
| **kw-writer** | Pipeline veloce: da una lista di keyword ad articoli scritti, revisionati e salvati, **senza domande intermedie**. Pensata per batch di 20+ articoli |

```mermaid
flowchart LR
    K[Lista keyword] --> E[editor<br/>piano + priorità]
    E --> W[writer]
    W --> R["reviewer<br/>anti-#quot;testo AI#quot;"]
    R --> N[NeuronWriter via MCP<br/>ottimizzazione SEO]
    N --> O[Articolo pronto<br/>+ stato aggiornato]
```

### Dettagli

- **Knowledge base del cliente** (servizi, partner, URL interni, glossario tecnico) letta da tutte le skill: link interni e terminologia sempre corretti.
- **Checklist "humanizer" adattata all'italiano tecnico-industriale** nel reviewer.
- **NeuronWriter collegato tramite MCP** (server `mcp-remote`): Claude legge i brief SEO e controlla i termini direttamente, senza copia-incolla.
- Lo stesso schema (writer → reviewer, più una pipeline veloce da keyword) è stato replicato per un **e-commerce di nicchia** su blog, newsletter e social.

## Risultati

- Da **una keyword a un articolo revisionato** in un solo comando.
- Produzione in batch mantenendo tono e regole del brand.
- **Meno di un'ora per articolo** da 1.200–1.400 parole, già revisionato e ottimizzato SEO.
- **8–10 articoli al giorno** in produzione, invece di giorni di lavoro per pochi pezzi.

## Cosa ho imparato

Dividere il lavoro tra agenti con un solo compito ciascuno funziona meglio di un unico prompt che deve fare tutto: il reviewer trova errori che il writer, per come è impostato, non vede.
