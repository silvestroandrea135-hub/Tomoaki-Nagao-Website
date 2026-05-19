# Nigo Collezioni Moda

Piattaforma web dinamica dedicata alla catalogazione e alla gestione strutturata delle collezioni di moda di **Tomoaki Nagao (Nigo)**, celebre designer giapponese e fondatore di *A Bathing Ape*. 

Il progetto è stato sviluppato con l'obiettivo di implementare un'applicazione modulare che rispetti i criteri di separazione delle responsabilità, la gestione sicura delle sessioni utente e l'interazione dinamica con database relazionali.

---

## 🚀 Architettura e Funzionalità

L'applicazione si basa su un'architettura a tre livelli (**3-Tier Architecture**) che separa nettamente la logica di presentazione, la logica di business e la persistenza dei dati.

### 1. Area Pubblica e Utente Standard
Offre un'interfaccia fluida per la consultazione pubblica del catalogo storico:
* **Autenticazione di Sessione:** Sistema di registrazione e login sicuro gestito interamente lato server tramite sessioni PHP nativizzate.
* **Catalogo e Filtri Avanzati:** Gli utenti possono esplorare l'archivio delle collezioni utilizzando un sistema di ricerca testuale e filtri dinamici per *Brand* e *Stagione*.
* **Area Personale:** Sezione profilo personalizzata con la possibilità di salvare le collezioni tra i propri *Preferiti*.

### 2. Pannello Amministrativo (Back-Office)
Una dashboard protetta e riservata agli amministratori di sistema per il controllo dei contenuti:
* **Gestione CRUD Integrata:** Interfaccia grafica dedicata per creare, leggere, aggiornare e cancellare le collezioni direttamente nel database.
* **Controllo Utenti:** Strumenti per monitorare gli iscritti alla piattaforma e gestirne i ruoli di accesso.

---

## 🛠️ Stack Tecnologico e Database

* **Backend:** **PHP 8.2+** – Gestisce la logica di business, il routing delle richieste HTTP (GET/POST), la validazione dei dati e il controllo degli accessi su ogni pagina protetta.
* **Database:** **MySQL / MariaDB** – Struttura relazionale ottimizzata composta da due entità principali:
  * `utente`: Memorizza credenziali e livello di privilegio (`0` per utente standard, `1` per amministratore).
  * `collezioni`: Cataloga i manufatti con dettagli su titolo, brand, stagione e link di riferimento.
* **Frontend:** **HTML5 Semantico & CSS3** – Layout pulito e responsivo, arricchito da una scelta tipografica accurata basata sui caratteri custom *Bodoni* e *Futura*.
* **Web Server:** Supporto nativo per ambienti **Apache** o **Nginx**.

---

## 🔒 Approccio alla Sicurezza e Sviluppi Futuri

Attualmente il progetto implementa controlli preventivi sulla validazione degli input e sulla gestione delle sessioni. Per una futura transizione in ambienti di produzione reali, la roadmap prevede i seguenti upgrade architetturali:
1. **Prepared Statements:** Migrazione del livello di accesso ai dati (DAL) verso costrutti PDO per l'azzeramento strutturale del rischio di SQL Injection.
2. **Password Hashing:** Integrazione dell'algoritmo crittografico `bcrypt` (tramite la funzione nativa `password_hash()`) per l'archiviazione sicura delle credenziali.
3. **Protezione CSRF:** Implementazione di token univoci per la messa in sicurezza dei form transazionali.
