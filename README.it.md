# Claude Token Saver

[English](README.md) | **Italiano**

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Version](https://img.shields.io/badge/version-1.2.1-green)](#)
[![Platform](https://img.shields.io/badge/platform-claude.ai%20%7C%20Claude%20Code-lightgrey)](#)

**Consuma meno token nelle tue conversazioni con Claude.** Una skill per claude.ai e un set di regole da incollare in Claude Code che fanno rispondere Claude in modo più stringato, con meno ripetizioni e una migliore gestione delle chat lunghe.

Progetto gemello di [Claude-Token-Meter](https://github.com/MrGodLink/Claude-Token-Meter): il Meter mostra quanto contesto resta, il Saver ti aiuta a farlo durare di più.

---

## Panoramica

| | Dove | Cosa cambia |
|---|---|---|
| **Skill** (`skill/token-saver/`) | claude.ai e le app | come Claude scrive le risposte e usa gli strumenti |
| **Regole** (`claude-code/`) | Claude Code | stesse regole, da incollare in `CLAUDE.md` |

## Funzionalità

- **Tre modalità** — *Risparmio* (default), *Ultra* (solo il risultato, senza spiegazioni), *Normale* (stile standard). Si cambia semplicemente chiedendolo.
- **Risposte più strette** — niente saluti, niente riformulazione della domanda, niente riassunto finale, lunghezza proporzionata.
- **Niente contenuti ripetuti** — codice o testo invariati non vengono ristampati; si mostrano solo le parti modificate.
- **Meno chiamate agli strumenti** — niente ricerche web o letture di file per cose che Claude sa già o ha in contesto.
- **Meno domande di chiarimento** — al massimo una, solo se indispensabile.
- **Gestione chat lunghe** — con meno di ~30% di contesto rimasto, Claude suggerisce una nuova chat e scrive un riassunto di passaggio (max 150 parole).
- **Consigli per l'utente** — una breve lista di abitudini che risparmiano token dal tuo lato (`references/consigli-utente.md`).

## Requisiti

- **Skill:** un account claude.ai con le Skill abilitate (Impostazioni → Capacità).
- **Regole:** Claude Code. Nient'altro da installare.

## Installazione

```
git clone https://github.com/MrGodLink/Claude-Token-Saver.git
cd Claude-Token-Saver
```

### 1. Skill per claude.ai

1. Carica [`releases/token-saver.skill`](releases/token-saver.skill) in Impostazioni → Capacità → Skill (oppure comprimi la cartella `skill/token-saver/` e carica lo `.zip`).
2. Apri una nuova chat e scrivi "risparmia token" o "risposte brevi".

**Per tenere la modalità sempre attiva**, Claude carica le skill solo quando le ritiene utili. Incolla questo testo in Impostazioni → Profilo → preferenze personali (vale solo per le nuove chat):

```
Risparmia sempre token: rispondi direttamente, senza saluti, senza riformulare la mia domanda e senza riassunto finale. Lunghezza proporzionata alla domanda. Formattazione minima. Non ristampare codice o testo invariati, mostra solo ciò che cambia. Al massimo una domanda di chiarimento, solo se indispensabile. Non usare strumenti per cose che già sai. Se scrivo "ultra", dammi solo il risultato.
```

### 2. Regole per Claude Code

Copia il contenuto di [`claude-code/token-saver-CLAUDE.md`](claude-code/token-saver-CLAUDE.md) nel `CLAUDE.md` del progetto (o in `~/.claude/CLAUDE.md` per tutti i progetti).

## Utilizzo

| Tu dici | Risultato |
|---|---|
| "risparmia token" | modalità Risparmio attiva |
| "ultra" / "solo il risultato" | modalità Ultra: risposte telegrafiche |
| "normale" / "spiegami meglio" | torna allo stile standard |
| "come risparmio token?" | 2-3 consigli pertinenti per il tuo lato |

### Personalizzazione

| Cosa | Dove |
|---|---|
| Regole e modalità | `skill/token-saver/SKILL.md` |
| Soglia contesto basso (30%) | sezione "Gestione del contesto" di `SKILL.md` |
| Lunghezza riassunto (150 parole) | stessa sezione |
| Consigli utente | `skill/token-saver/references/consigli-utente.md` |

## Architettura

```
Claude-Token-Saver/
├── skill/
│   └── token-saver/
│       ├── SKILL.md                    # la skill (istruzioni per Claude)
│       └── references/
│           └── consigli-utente.md      # consigli per l'utente, caricati su richiesta
├── claude-code/
│   └── token-saver-CLAUDE.md           # regole per CLAUDE.md
├── releases/
│   └── token-saver.skill               # pacchetto pronto da caricare
├── LICENSE
├── README.md
└── README.it.md
```

## Limiti

- Riduce soprattutto l'**output di Claude** e l'uso degli strumenti. Ciò che è già nella chat continua a contare finché non apri una nuova conversazione.
- La skill occupa a sua volta un po' di contesto quando si attiva: conviene su chat lunghe o ripetitive, meno su una domanda singola.
- Le stime di token sono approssimative (circa 4 caratteri = 1 token).
- Risposte più brevi sono un compromesso: se ti serve approfondimento, scrivi "normale" o "spiegami meglio".
- Non testata in modo approfondito: feedback e segnalazioni sono benvenuti.

## Privacy e uso responsabile

- Sono istruzioni in testo semplice: questo progetto non invia nulla da nessuna parte e non c'è codice da eseguire.
- Progetto indipendente della community, non affiliato né approvato da Anthropic.

## Crediti

Creato da **Raffaele Catapano** — [github.com/MrGodLink](https://github.com/MrGodLink)

Se riutilizzi, modifichi o ridistribuisci questo progetto, mantieni la nota di copyright e cita l'autore originale, come richiesto dalla licenza MIT.

Segnalazioni di bug e idee sono benvenute nell'[issue tracker](https://github.com/MrGodLink/Claude-Token-Saver/issues).

## Licenza

Rilasciato con licenza MIT — vedi [LICENSE](LICENSE).
