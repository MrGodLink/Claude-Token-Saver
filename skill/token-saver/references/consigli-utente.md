# Consigli per risparmiare token (lato utente)

- **Una richiesta chiara per messaggio**, con il formato atteso ("in 5 righe", "solo il codice", "solo il diff").
- **Non incollare tutto**: allega solo la parte rilevante; per file lunghi indica righe o sezione.
- **Una chat per argomento**: ogni turno rimanda in contesto l'intera conversazione.
- **Riassunto di passaggio** quando la chat è lunga: obiettivo, decisioni, stato, prossimi passi, poi riparti in una chat nuova.
- **Chiedi modifiche mirate** ("cambia solo X", "mostra solo le righe cambiate") invece di rigenerare il file intero.
- **Fissa le istruzioni una volta**: iniziali in basso a sinistra → Settings → Your Claude (Account nel layout precedente) → Instructions (Instructions for Claude nel layout precedente). Valgono su tutte le chat; per un progetto usa le istruzioni di progetto.
- **Evita messaggi di solo ringraziamento o conferma**: costano un turno intero di contesto.
- **Attiva ricerca web, ricerca approfondita e connettori solo quando servono**: i risultati entrano in contesto.
- **Non disattivare code execution per risparmiare**: su claude.ai le skill lo richiedono, quindi si spengono anche loro.
- **Misura, non stimare**: i token dipendono da modello e lingua; per conteggi esatti usa l'endpoint API /v1/messages/count_tokens (gratuito).