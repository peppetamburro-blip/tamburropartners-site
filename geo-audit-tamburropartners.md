# GEO Audit - tamburropartners.com
Generato 2026-06-04 su branch feat/geo-setup
## Stack
- Sito statico HTML puro (no framework, no build).
- Tailwind via CDN.
- Rendering: gia statico SSG → tutto il contenuto e nell'HTML grezzo (no JS-dependent). Ottimo per LLM/crawler GEO.
- Hosting: GitHub Pages dietro Cloudflare proxy.

## CF bot test (eseguito 04/06)
GPTBot, ClaudeBot, PerplexityBot, OAI-SearchBot, Google-Extended → tutti HTTP 200. Cloudflare NON blocca. OK.

## robots.txt
Aggiornato con allow espliciti per GPTBot, OAI-SearchBot, ChatGPT-User, ClaudeBot, Claude-Web, PerplexityBot, Perplexity-User, Google-Extended, Applebot-Extended, CCBot. Disallow esistenti (/assets/hero/, /CNAME) preservati.

## llms.txt
Creato in root con summary brand, materie, 3 articoli reali con URL canonici, identita studio (PIVA, sede, contatti).

## JSON-LD coverage
| Pagina | h1 | LegalService | Article | meta desc | canonical | OG | testo chars |
|---|---|---|---|---|---|---|---|
| articolo-cadute-scale-bagnate-il-condominio-paga-anche-con-appalto.html | 1 | ✓ | ✓ | ✓ | ✗ | ✗ | 6090 |
| articolo-composizione-negoziata-novita-del-decreto-attuativo-2026.html | 1 | ✓ | ✓ | ✓ | ✗ | ✗ | 8790 |
| articolo-scale-bagnate.html | 1 | ✓ | ✓ | ✓ | ✗ | ✗ | 8241 |
| articolo-trasparenza-retributiva-ue-2026-obblighi-per-le-aziende.html | 1 | ✓ | ✓ | ✓ | ✗ | ✗ | 8413 |
| articolo.html | 1 | ✗ | - | ✗ | ✗ | ✗ | 5714 |
| contatti.html | 1 | ✓ | - | ✗ | ✓ | ✓ | 1581 |
| index.html | 1 | ✓ | - | ✓ | ✓ | ✓ | 7304 |
| insights.html | 1 | ✓ | - | ✓ | ✓ | ✓ | 5315 |
| materie.html | 1 | ✓ | - | ✗ | ✓ | ✓ | 3276 |
| professionisti.html | 1 | ✓ | - | ✗ | ✓ | ✓ | 1101 |
| studio.html | 1 | ✓ | - | ✗ | ✓ | ✓ | 2034 |

## Problemi rilevati
- **articolo-cadute-scale-bagnate-il-condominio-paga-anche-con-appalto.html**: manca link canonical
- **articolo-cadute-scale-bagnate-il-condominio-paga-anche-con-appalto.html**: mancano OG tags
- **articolo-composizione-negoziata-novita-del-decreto-attuativo-2026.html**: manca link canonical
- **articolo-composizione-negoziata-novita-del-decreto-attuativo-2026.html**: mancano OG tags
- **articolo-scale-bagnate.html**: manca link canonical
- **articolo-scale-bagnate.html**: mancano OG tags
- **articolo-trasparenza-retributiva-ue-2026-obblighi-per-le-aziende.html**: manca link canonical
- **articolo-trasparenza-retributiva-ue-2026-obblighi-per-le-aziende.html**: mancano OG tags
- **articolo.html**: manca link canonical
- **articolo.html**: mancano OG tags

## Pagine thin / candidate a diventare pagine-risposta
- **materie.html** (8KB): elenco materie. Candidato a pagine dedicate per materia con FAQ schema (es. /terzo-settore.html, /lavoro.html, /condominio.html, /contrattualistica.html).
- **professionisti.html** (4KB): bio reali ancora mancanti (TODO progetto).
- **contatti.html** (5KB): non thin, ma puo beneficiare di FAQ schema (orari, modalita consulenza, materie trattate).

## SSR / contenuto chiave
Test no-JS (curl + strip tag) su index.html, articoli, materie: contenuto PRESENTE nell'HTML server-rendered. Nessun problema GEO da JavaScript.

## TODO post-merge (non bloccanti)
- FAQPage schema su contatti.html + ogni articolo (3-5 Q&A pratiche)
- OG image dedicate per articoli (oggi solo hero generico)
- link canonical su articoli (alcuni mancano)
- pagine-risposta per materia con BLUF + FAQ + JSON-LD specifico
- monitorare in GA4 referrer: chat.openai.com, chatgpt.com, perplexity.ai, claude.ai, gemini.google.com, copilot.microsoft.com
