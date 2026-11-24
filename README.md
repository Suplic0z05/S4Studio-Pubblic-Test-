# S4Studio — Versione Pubblica Tester (Alpha & Beta)

Hub desktop per gestire un server S4 League: client, sorgenti, processi, database,
contenuti, pacchetti, plugin, assistente AI e dashboard web.

> **Questa repo contiene SOLO la build di test.** Il codice sorgente è privato (repo team).

## Come diventare tester

1. Ricevi una **chiave licenza** dal team (formato `S4T1.….…`) — è personale, a tempo
   (**1 settimana**) ed è tracciata: le chiavi sono in numero **limitato**.
2. Scarica `S4StudioSetup.exe` dalla sezione **Releases**.
3. Avvia l'installer → sceglie il percorso → scarica i runtime ufficiali (.NET, MariaDB)
   verificandone l'hash → estrae l'app e la **sigilla** (manifest di integrità).
4. Alla prima esecuzione inserisci la tua chiave: senza chiave valida (non scaduta, non
   revocata) **l'app non si avvia**.
5. Dopo la scadenza l'app si disattiva da sola: nessun file del progetto è recuperabile
   attraverso l'app. Rinnovo = nuova chiave dal team (o ingresso nel team, che sblocca
   l'accesso continuativo).

## Requisiti

- Windows 10/11 x64 (runtime .NET 10 e MariaDB sono scaricati dall'installer con hash verificato)
- Nessuna conoscenza richiesta: il wizard di primo avvio chiede solo le cartelle

## Cosa testare (priorità)

1. **Installazione** (installer, primo avvio, wizard) e **database.setup** (MariaDB con hash ufficiale)
2. **Database**: connessione, schema, giocatori, backup
3. **Shop Wizard** e `shop.check` (coerenza item client ↔ DB)
4. **Client**: apertura `resource.s4hd`, anteprima, estrazione, import
5. **Console Admin web**: login, TOTP, comandi
6. Problemi: apri una **Issue** qui con log (cartella dati → `Data/machine/logs`)

## Regole del tester

- La chiave è personale: non condividerla (è tracciata e può essere revocata)
- Nessun anti-cheat viene toccato: il progetto non fa cheat/inject
- Test solo su server/database di tua proprietà o autorizzati

## Licenza & integrità

- Build **sigillata**: `installation-manifest.json` con SHA-256 + digest protetto (l'installer
  verifica; l'app rifiuta file alterati)
- Le licenze sono **firmate crittograficamente** (RSA-3072): alterare o prolungare una chiave
  senza la chiave del team è matematicamente infeasible
- Limito dichiarato: l'app disconosce l'orologio di sistema — senza verifica online un utente
  esperto può spostare l'orologio; la verifica online è il passo successivo (il server del team
  sovrascrive la scadenza locale quando raggiungibile)

---
Progetto: S4Studio · canale alpha · © team S4Studio — riservato ai tester autorizzati
