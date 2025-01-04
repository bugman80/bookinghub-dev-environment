# Configurazione dell'Ambiente di Sviluppo

Questo repository ha lo scopo di facilitare l'orchestrazione dei servizi frontend, backend e database necessari al funzionamento del progetto BookingHub

---

## Indice

- [Introduzione](#introduzione)
- [Caratteristiche](#caratteristiche)
- [Prerequisiti](#prerequisiti)
- [Installazione](#installazione)
- [Deployment](#deployment)
- [Licenza](#licenza)

---

## Introduzione

**BookingHub-Dev-Environment** rappresenta l'orchestratore di un progetto composto da backend (https://github.com/bugman80/bookinghub-backend) e frontend (https://github.com/bugman80/bookinghub-frontend), questo repository e' nato per facilitare il setup e run dell'ambiente di sviluppo tramite un docker-compose che consente di orchestrare entrambi i layer ed il database PostgreSQL

## Caratteristiche

- docker-compose file per il build e run dei servizi frontend, backend e database
- .env.example file per facilitare la creazione di un file con le variabili di ambiente necessarie

## Prerequisiti

- **Git**
- **Docker**
- **Docker-Compose**

## Installazione

Segui questi passaggi per configurare l'applicazione in locale, questo comportera' clonare il repository backend, il repository frontend ed il repository contenente l'orchestratore dei servizi. I tre repository devono essere clonati nella stessa directory che avra' quindi la seguente struttura finale:

```
/bookinghub-dev-environment/   # Clone del repository di orchestrazione
|
├── docker-compose.yml
├── .env
└── README.md

/bookinghub-backend/           # Clone del repository backend
/bookinghub-frontend/          # Clone del repository frontend
```

### 1. Entra nella directory che hai scelto per contenere i tre repository di progetto

```bash
cd CartellaDiPreferenza
```

### 2. Clona il repository backend

```bash
git clone https://github.com/bugman80/bookinghub-backend.git
```

### 3. Clona il repository frontend

```bash
git clone https://github.com/bugman80/bookinghub-frontend.git
```

### 4. Clona il repository di orchestrazione e configura le variabili di ambiente

```bash
git clone https://github.com/bugman80/bookinghub-dev-environment.git
cd bookinghub-dev-environment
```
Crea un file `.env` nella root di questo repository (rifacendoti a `.env.example`) per definire le variabili di ambiente

### 5. Costruisci e Avvia i Servizi

Esegui il seguente comando per costruire e avviare i servizi:

```bash
docker-compose up
```

Questo comando:
- Costruirà le immagini per backend e frontend
- Avvierà i servizi backend, frontend e il database PostgreSQL

### 6. Accedi ai Servizi

- **Frontend**: [http://localhost:3000](http://localhost:3000)
- **Backend (API)**: [http://localhost:8000](http://localhost:8000)
- **PostgreSQL**: Accessibile sulla porta `5432`

### 7. Arrestare i Servizi

Per arrestare i servizi, premi `Ctrl+C` o esegui:

```bash
docker-compose down
```

## Deployment

L'applicazione e' attualmente rilasciata automaticamente su Railway (https://railway.app/).

## Licenza

Nessuna licenza e' associata alla applicazione.