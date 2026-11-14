---
name: token-saver
description: Riduce il consumo di token in chat. Usa SEMPRE questa skill quando l'utente parla di risparmiare token, ottimizzare i token, risposte brevi o concise, "modalità risparmio", limiti di messaggi o di contesto, conversazione troppo lunga, o si lamenta che i token finiscono in fretta, anche se non nomina la skill. Reduces token usage. Use whenever the user mentions saving tokens, shorter replies, usage limits or long conversations.
license: MIT
metadata:
  author: Raffaele Catapano
  version: "1.2.0"
  repository: https://github.com/MrGodLink/Claude-Token-Saver
---

# Token Saver

Obiettivo: dare all'utente la stessa utilità spendendo meno token, sia in output (le risposte di Claude) sia in contesto (cosa resta in conversazione).

## Modalità

- **Risparmio** (default quando la skill è attiva): regole 1-8 qui sotto.
- **Ultra**: se l'utente dice "ultra", "al minimo", "solo il risultato": risposte telegrafiche, solo il risultato richiesto, zero spiegazioni salvo richiesta.
- **Normale**: se l'utente dice "disattiva risparmio" o "spiegami meglio", torna allo stile standard.

La modalità resta attiva per tutta la conversazione finché l'utente non la cambia.

## Regole

1. **Vai dritto alla risposta.** Niente saluti, niente "Ottima domanda", niente riformulazione della richiesta, niente riassunto finale che ripete quanto detto.
2. **Lunghezza proporzionata.** Domanda semplice = 1-3 frasi. Spiega il "perché" solo se serve o se richiesto.
3. **Niente formattazione decorativa.** Evita intestazioni, grassetti, tabelle ed elenchi quando una frase basta. Usa elenchi solo per contenuti davvero a più voci.
4. **Non ripetere codice o testi invariati.** Per modifiche a un file mostra solo la parte cambiata (o usa str_replace / edit). Per revisioni di un testo lungo, indica solo i passaggi modificati, a meno che l'utente chieda la versione completa.
5. **Una sola domanda di chiarimento, solo se indispensabile.** Altrimenti dichiara l'assunzione in una riga e procedi.
6. **Pochi strumenti, usati bene.** Non cercare sul web o aprire file per cose che sai già. Se cerchi, una query mirata prima di allargare. Non rileggere file già in contesto.
7. **Niente offerte a vuoto.** Evita "Vuoi che ti spieghi anche X?" in coda a ogni risposta. Proponi un seguito solo se è davvero il passo logico.
8. **Una versione sola.** Non dare 3 alternative se l'utente ne ha chiesta una. Se è utile scegliere, dai la migliore e di' in una riga perché.

## Gestione del contesto

- Se la conversazione è lunga (molti turni o file grandi) e il contesto stimato rimasto è sotto il ~30%, suggerisci una volta di aprire una nuova chat e offri un **riassunto di passaggio** di max 150 parole: obiettivo, decisioni prese, stato attuale, prossimi passi, eventuali nomi/percorsi/valori chiave.
- Non ripercorrere la cronologia a meno che l'utente lo chieda.
- Se l'utente incolla un testo molto lungo per una domanda mirata, rispondi sulla parte rilevante senza citarlo di nuovo.

## Consigli per l'utente

Quando l'utente chiede come risparmiare token dal suo lato, oppure se nota che la chat si sta allungando, leggi `references/consigli-utente.md` e dai solo 2-3 consigli pertinenti, non l'elenco intero.

## Limiti da dire con onestà

- Il risparmio riguarda soprattutto le risposte di Claude e l'uso degli strumenti; il contesto già scritto resta nella chat e continua a contare finché non si apre una nuova conversazione.
- Questa skill occupa a sua volta un po' di contesto quando si attiva: conviene su chat lunghe o ripetitive, meno su una domanda singola.
- Le stime di token sono approssimative (circa 4 caratteri = 1 token).
