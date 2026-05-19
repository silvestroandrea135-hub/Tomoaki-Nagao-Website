# Nigo Collezioni Moda

Piattaforma web per la gestione e catalogazione di collezioni di moda di Tomoaki Nagao (Nigo), leggendario designer giapponese e fondatore di A Bathing Ape.

## Descrizione Progetto

L'applicazione consente di visualizzare, organizzare e gestire un catalogo di collezioni di moda. Gli utenti standard possono registrarsi, accedere al profilo, visualizzare collezioni e filtrarle per brand e stagione. Gli amministratori dispongono di un pannello di controllo per aggiungere, modificare ed eliminare collezioni, nonché gestire gli utenti della piattaforma.

## Architettura

Il progetto implementa un'architettura web tradizionale a tre livelli:

**Backend**: PHP 8.2+ che gestisce autenticazione, sessioni, validazione e operazioni CRUD sul database.

**Database**: MySQL/MariaDB con due tabelle relazionali (utente e collezioni) per la persistenza dei dati.

**Frontend**: HTML5 semantico con CSS3 per la presentazione dell'interfaccia utente nel browser.

La comunicazione tra i livelli avviene tramite HTTP/HTTPS, con PHP che elabora le richieste POST/GET e restituisce risposte HTML.

## Tecnologie Utilizzate

| Componente | Tecnologia |
|-----------|-----------|
| Backend | PHP 8.2+ |
| Database | MySQL/MariaDB 10.4+ |
| Frontend | HTML5, CSS3 |
| Typography | Font custom (Bodoni, Futura) |
| Server | Apache/Nginx |

## Funzionalità

**Utenti Standard**:
- Registrazione e login
- Visualizzazione catalogo collezioni
- Ricerca e filtri (brand, stagione)
- Profilo personalizzato
- Salvataggio preferiti

**Amministratori**:
- Pannello di controllo completo
- Gestione collezioni (CRUD)
- Gestione utenti
- Modifica contenuti

## Struttura Database

**Tabella utente**: Memorizza credenziali, dati profilo e ruolo (0 = utente, 1 = admin)

**Tabella collezioni**: Memorizza catalogo con titolo, brand, stagione e link di riferimento

## Installazione

### Prerequisiti
- PHP 8.2+
- MySQL/MariaDB
- Server web (Apache/Nginx)

### Setup

```bash
# Clona il repository
git clone https://github.com/andreasilvestro/nigo-collezioni-moda.git
cd nigo-collezioni-moda

# Importa il database
mysql -u root -p < moda.sql

# Configura connessione.php
# Modifica le credenziali del database

# Avvia l'applicazione
php -S localhost:8000
```

Accedi a http://localhost:8000

## Credenziali di Test

**Admin**:
- Username: silver
- Password: amministratore

**User**:
- Username: papera
- Password: paperone

## Pattern Implementativi

**Session Management**: Autenticazione basata su sessioni server-side con verifica dello stato su ogni pagina protetta.

**CRUD Operations**: Operazioni di creazione, lettura, aggiornamento e eliminazione distribute tra file PHP dedicati.

**Separazione Responsabilità**: Divisione tra livello presentazione (template HTML), logica applicativa (elaborazione dati) e accesso dati (query database).

**Input Validation**: Sanitizzazione input tramite mysqli_real_escape_string() per prevenire SQL injection.

## Note di Sicurezza

Il progetto utilizza mysqli_real_escape_string() per la protezione dalle SQL injection. Per ambienti production si consiglia:

- Prepared statements al posto di escape string
- Password hashing con bcrypt
- HTTPS
- CSRF tokens
- Validazione lato server rigorosa

## Struttura Progetto
