# AURACHAT

## Descrizione del progetto
AURACHAT è un semplice sistema di chat **client-server** sviluppato in **Python**, basato sull’uso dei **socket di rete**.  
Il progetto utilizza **UDP** per la discovery automatica del server e **TCP** per la comunicazione affidabile tra i client.

Il server non partecipa attivamente alla chat, ma gestisce le connessioni e inoltra i messaggi tra i client.

---

## Struttura del progetto

AURACHAT/
├── server.py
├── client.py
└── util/
├── config.json
└── log.xml


## Funzionamento

1. Il server viene avviato e resta in attesa:
   - UDP per la discovery
   - TCP per le connessioni

2. Il client:
   - invia un messaggio UDP di discovery
   - riceve l’IP del server
   - si connette via TCP

3. I client possono comunicare tra loro tramite il server.

4. Il server:
   - gestisce più client contemporaneamente
   - chiude un client dopo **2 minuti di inattività**
   - salva le attività nel file `log.xml`

---

## Protocolli utilizzati

- **UDP**
  - utilizzato per la discovery automatica del server

- **TCP**
  - utilizzato per la comunicazione principale tra client

---

## Comandi supportati

- `TIME` → restituisce l’ora corrente del server  
- `EXIT` → disconnette il client  
- `CHAT <ID> <messaggio>` → invia un messaggio a un altro client  
