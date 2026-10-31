# OWASP NodeGoat — Web Security Assessment & Remediation

**Focus:** Web Application Security | OWASP Top 10 | Secure Coding | Vulnerability Assessment

## Overview

Progetto universitario di **Software Security** dedicato all'analisi di [OWASP NodeGoat](https://github.com/OWASP/NodeGoat), un'applicazione web Node.js intenzionalmente vulnerabile, progettata per esercitazioni pratiche di sicurezza applicativa.

L'obiettivo è stato analizzare le vulnerabilità dal punto di vista **offensivo e difensivo**, identificando i problemi di sicurezza, verificandone l'impatto e implementando o proponendo misure di remediation.

Il laboratorio segue la classificazione OWASP Top 10 utilizzata nel progetto NodeGoat, basata su una versione precedente delle categorie OWASP.

## Methodology

L'attività è stata organizzata in cinque fasi:

1. **Code Review** — identificazione delle vulnerabilità attraverso l'analisi del codice sorgente.
2. **Vulnerability Validation** — verifica pratica delle vulnerabilità nell'ambiente controllato.
3. **Impact Analysis** — valutazione degli effetti su riservatezza, integrità e disponibilità.
4. **Remediation** — implementazione di correzioni e individuazione di contromisure.
5. **Security Retesting** — verifica dell'efficacia delle modifiche, dove documentata.

## Vulnerabilities Analyzed

| Categoria | Analisi e remediation |
|---|---|
| **A1 — Injection** | Server-Side JavaScript Injection, NoSQL Injection e Log Injection. Validazione degli input, rimozione di esecuzione dinamica non sicura e sanitizzazione dei log. |
| **A2 — Broken Authentication** | Hashing con bcrypt, gestione sicura delle sessioni, protezione dei cookie, rigenerazione del session ID e mitigazione del password guessing. |
| **A3 — Cross-Site Scripting** | Stored XSS nei campi del profilo. Input validation, output encoding, auto-escaping e protezione dei cookie. |
| **A4 — IDOR** | Accesso non autorizzato alle allocazioni modificando identificativi URL. Controllo dell'identità tramite sessione autenticata. |
| **A5 — Security Misconfiguration** | Riduzione dell'information disclosure attraverso header HTTP, configurazione Express e Helmet. |
| **A6 — Sensitive Data Exposure** | Configurazione HTTPS/TLS in laboratorio e crittografia dei dati sensibili mediante il modulo crypto di Node.js. |
| **A7 — Missing Function Level Access Control** | Accesso alle funzionalità amministrative tramite richieste dirette. Implementazione del middleware isAdmin. |
| **A8 — CSRF** | Dimostrazione di modifiche non autorizzate al profilo e introduzione della validazione di token anti-CSRF. |
| **A9 — Insecure Components** | Analisi della libreria Marked vulnerabile a XSS, valutazione delle dipendenze e raccomandazioni di aggiornamento. |
| **A10 — Unvalidated Redirects** | Reindirizzamenti arbitrari tramite parametri URL. Implementazione di una allowlist di destinazioni consentite. |

## Technical Highlights

### Authentication & Session Security

L'analisi ha evidenziato l'importanza della gestione dell'intero ciclo di vita dell'autenticazione.

Sono state studiate e applicate misure quali hashing delle password con **bcrypt**, rigenerazione degli identificativi di sessione, scadenza delle sessioni, cookie `HttpOnly` e `Secure`, politiche di password e messaggi di errore generici.

### Access Control

Gli esercizi su **IDOR** e **Missing Function Level Access Control** hanno dimostrato che nascondere funzionalità nell'interfaccia utente non equivale a proteggerle.

È necessario effettuare controlli di autorizzazione lato server, sia sull'accesso agli oggetti sia sull'utilizzo delle funzionalità privilegiate.

### Input Validation & Output Encoding

Gli esercizi di Injection e XSS hanno evidenziato l'importanza di trattare gli input dell'utente come non attendibili.

Tra le contromisure analizzate figurano la validazione dei dati lato server, l'eliminazione di funzioni di esecuzione dinamica insicure e l'encoding dell'output specifico per il contesto di destinazione.

### Security Hardening & Dependencies

Il laboratorio ha incluso la revisione della configurazione di Express.js, l'utilizzo di **Helmet**, la protezione dei dati durante il trasporto e l'analisi di dipendenze JavaScript vulnerabili.

## Technologies & Tools

- **Node.js / Express.js** — applicazione e middleware.
- **MongoDB** — database e analisi delle query NoSQL.
- **JavaScript / HTML** — analisi e modifica del codice.
- **Docker / Docker Compose** — ambiente di laboratorio.
- **OpenSSL / HTTPS** — test di comunicazione cifrata.
- **bcrypt / Helmet / crypto** — sicurezza applicativa.
- **npm audit** — analisi delle dipendenze e vulnerabilità note.

## Lab Setup

Il laboratorio si basa sul repository ufficiale di OWASP NodeGoat.

```bash
git clone https://github.com/OWASP/NodeGoat.git
cd NodeGoat
npm install
docker compose build
docker compose up -d
```

La configurazione può variare a seconda della versione del progetto. Consultare la documentazione ufficiale per database, credenziali dimostrative e variabili d'ambiente.

**Security notice:** NodeGoat è intenzionalmente vulnerabile. Tutti i test devono essere effettuati esclusivamente in ambienti isolati e autorizzati. Non esporre l'applicazione vulnerabile a Internet né pubblicare credenziali e chiavi private.


## Skills Gained

- Web Application Security Assessment
- Manual Code Review
- Vulnerability Analysis
- OWASP Top 10
- Authentication & Authorization Testing
- Secure Coding & Remediation
- Application Hardening
- Technical Security Documentation

## Authors & References

**Academic group project:** Pierluigi Iacono, Rocco Marotta, Daniele Caputo.

**Course:** Software Security — Università degli Studi di Napoli Federico II, 2024/2025.

**References:** [OWASP NodeGoat](https://github.com/OWASP/NodeGoat) | [OWASP Top 10](https://owasp.org/www-project-top-ten/)
