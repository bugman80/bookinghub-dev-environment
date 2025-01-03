# Configurazione dell'Ambiente di Sviluppo

Questo repository funge da configurazione per l'ambiente di sviluppo del progetto bookinghub con backend (Django + DRF) e frontend (React) separati. Utilizza Docker Compose per orchestrare i servizi, garantendo un workflow di sviluppo coerente ed efficiente.

---

## Prerequisiti

Prima di iniziare, assicurati di avere installato:

- [Docker](https://www.docker.com/)
- [Docker Compose](https://docs.docker.com/compose/install/)
- Git

---

## Struttura del Repository

Questo repository ha la seguente struttura:

```
/bookinghub-dev-environment/        # Questo repository
|
├── docker-compose.yml   # File di configurazione di Docker Compose
├── .env                 # Variabili di ambiente per i servizi
└── README.md            # Documentazione (questo file)

/bookinghub-backend/           # Clone del repository backend
/bookinghub-frontend/          # Clone del repository frontend
```

---

## Istruzioni di Configurazione

### 1. Clona i Repository

Clona i repository backend e frontend nella stessa directory di questo repository:

```bash
git clone https://github.com/bugman80/bookinghub-backend
git clone https://github.com/bugman80/bookinghub-frontend
```

alla fine la directory che hai scelto per clonare i 3 repositories dovrebbe avere questa struttura:

```
/bookinghub-dev-environment/        # Questo repository
|
├── docker-compose.yml   # File di configurazione di Docker Compose
├── .env                 # Variabili di ambiente per i servizi
└── README.md            # Documentazione (questo file)

/bookinghub-backend/           # Clone del repository backend
/bookinghub-frontend/          # Clone del repository frontend
```

### 2. Configura le Variabili di Ambiente

Crea un file `.env` nella root di questo repository (rifacendoti a `.env.example`) per definire le variabili di ambiente:

### 3. Costruisci e Avvia i Servizi

Esegui il seguente comando per costruire e avviare i servizi:

```bash
docker-compose up --build
```

Questo comando:
- Costruirà le immagini per backend e frontend
- Avvierà i servizi backend, frontend e database PostgreSQL

### 4. Accedi ai Servizi

- **Frontend**: [http://localhost:3000](http://localhost:3000)
- **Backend (API)**: [http://localhost:8000](http://localhost:8000)
- **PostgreSQL**: Accessibile sulla porta `5432`

---

## Workflow di Sviluppo

### Hot Reload

I repository backend e frontend sono montati come volumi nei rispettivi container. Qualsiasi modifica al codice sorgente attiverà l'hot reload sia per Django che per React.

### Arrestare i Servizi

Per arrestare i servizi, premi `Ctrl+C` o esegui:

```bash
docker-compose down
```

### Ricostruire i Servizi

Se apporti modifiche al `Dockerfile` o alle dipendenze, ricostruisci i servizi con:

```bash
docker-compose up --build
```

---

## Risoluzione dei Problemi

### Problemi Comuni

- **Conflitti di Porta**: Assicurati che le porte `3000`, `8000` e `5432` non siano utilizzate da altri processi.
- **Errori nelle Variabili di Ambiente**: Verifica che tutte le variabili richieste siano definite nel file `.env`.
- **Persistenza del Database**: I dati di PostgreSQL sono memorizzati in un volume Docker (`postgres_data`). Per resettare il database, rimuovi il volume:

  ```bash
  docker-compose down -v
  ```

### Visualizzare i Log

Per visualizzare i log di un servizio specifico:

```bash
docker-compose logs <nome-servizio>
```

Sostituisci `<nome-servizio>` con `backend`, `frontend` o `db`.

---

## Licenza

Nessuna licenza e' associata alla applicazione.
