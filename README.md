Absolutely — I'd keep the initial README fairly simple and let it evolve as the project does. You can copy this directly into `README.md`.

# Garmin Dashboard

A personal fitness dashboard that connects to Garmin Connect, stores Garmin data in a personal database, and presents it through a custom dashboard.

The long-term goal is to build a personal fitness data platform that gives me more control over how my Garmin data is displayed and analysed than Garmin Connect itself.

## Project Goals

* Connect to Garmin Connect
* Import historical Garmin data
* Store Garmin data in PostgreSQL
* Build a custom dashboard for viewing fitness and health data
* Create custom metrics and analytics
* Automatically synchronise new Garmin data
* Eventually expose the data through an MCP server for AI-powered analysis

## Planned Architecture

```text
                    Garmin Connect
                          │
                          ▼
                 Garmin Data Client
                          │
                          ▼
                    PostgreSQL
                    /        \
                   /          \
                  ▼            ▼
              FastAPI          MCP
                 │               │
                 ▼               ▼
             Dashboard           AI
             (React)          Assistant
```

## Planned Features

### Activities

* Running
* Walking
* Cycling
* Golf
* Other Garmin activities
* Distance
* Duration
* Pace
* Heart rate
* Calories
* Elevation
* Cadence
* GPS data
* Training effect
* Training load

### Health

* Resting heart rate
* Heart rate
* HRV
* Stress
* Body Battery
* Steps
* Calories
* Respiration
* Other available Garmin health metrics

### Sleep

* Total sleep
* Sleep score
* Sleep stages
* Sleep consistency
* Sleep trends

### Running Analytics

* Weekly mileage
* Monthly mileage
* Pace trends
* Heart-rate trends
* Personal bests
* Training volume
* Training load
* Custom running metrics

### Dashboard

The dashboard will eventually provide:

* Overview
* Activities
* Activity details
* Running
* Health
* Sleep
* Training
* Historical trends
* Custom analytics

## Technology

### Backend

* Python
* FastAPI
* SQLAlchemy
* Alembic

### Database

* PostgreSQL

### Frontend

* React
* TypeScript
* Vite
* Recharts
* MapLibre / Leaflet

### AI

* Model Context Protocol (MCP)

### Infrastructure

* Docker
* Git / GitHub

## Project Structure

```text
garmin-dashboard/
│
├── backend/
│   ├── app/
│   │   ├── api/
│   │   ├── db/
│   │   ├── garmin/
│   │   ├── models/
│   │   └── services/
│   │
│   ├── tests/
│   ├── requirements.txt
│   └── Dockerfile
│
├── frontend/
│   ├── src/
│   │   ├── components/
│   │   ├── pages/
│   │   ├── charts/
│   │   └── api/
│   │
│   ├── package.json
│   └── Dockerfile
│
├── database/
│   └── migrations/
│
├── docker-compose.yml
├── .env.example
├── .gitignore
└── README.md
```

## Development Roadmap

### Phase 1 — Garmin Connection

* [ ] Create Python environment
* [ ] Install Garmin Connect library
* [ ] Authenticate with Garmin Connect
* [ ] Retrieve Garmin profile
* [ ] Retrieve recent activities
* [ ] Inspect Garmin data structures

### Phase 2 — Garmin Data Layer

* [ ] Create Garmin client wrapper
* [ ] Retrieve activities
* [ ] Retrieve activity details
* [ ] Retrieve daily health data
* [ ] Retrieve sleep data
* [ ] Retrieve HRV data
* [ ] Retrieve Body Battery data
* [ ] Retrieve training data
* [ ] Implement authentication/token persistence

### Phase 3 — Database

* [ ] Set up PostgreSQL
* [ ] Create SQLAlchemy models
* [ ] Configure Alembic
* [ ] Create activity tables
* [ ] Create health tables
* [ ] Create sleep tables
* [ ] Create training tables
* [ ] Implement Garmin → PostgreSQL sync
* [ ] Implement duplicate detection

### Phase 4 — Historical Data

* [ ] Import historical activities
* [ ] Import historical health data
* [ ] Import historical sleep data
* [ ] Import historical training data
* [ ] Verify data completeness
* [ ] Implement incremental synchronisation

### Phase 5 — API

* [ ] Set up FastAPI
* [ ] Activity endpoints
* [ ] Health endpoints
* [ ] Sleep endpoints
* [ ] Running endpoints
* [ ] Training endpoints
* [ ] Dashboard endpoints

### Phase 6 — Dashboard

* [ ] Create React application
* [ ] Create dashboard layout
* [ ] Overview page
* [ ] Activities page
* [ ] Activity detail page
* [ ] Running page
* [ ] Health page
* [ ] Sleep page
* [ ] Training page
* [ ] Historical charts
* [ ] Activity maps

### Phase 7 — Custom Analytics

* [ ] Running performance metrics
* [ ] Training load analysis
* [ ] Recovery metrics
* [ ] Sleep trends
* [ ] Personal records
* [ ] Period comparisons
* [ ] Custom fitness statistics

### Phase 8 — MCP

* [ ] Create MCP server
* [ ] Connect MCP to database
* [ ] Add activity tools
* [ ] Add health tools
* [ ] Add running analysis tools
* [ ] Add training analysis tools
* [ ] Test AI queries

### Phase 9 — Automation

* [ ] Scheduled Garmin synchronisation
* [ ] Automatic data processing
* [ ] Error handling
* [ ] Logging
* [ ] Database backups
* [ ] Docker deployment

## Getting Started

### Prerequisites

* Python 3.10+
* Git
* PostgreSQL *(not required for the initial Garmin connection test)*
* A Garmin Connect account

### Clone the repository

```bash
git clone <repository-url>
cd garmin-dashboard
```

### Create the Python environment

```bash
cd backend

python -m venv .venv
```

Windows:

```powershell
.\.venv\Scripts\Activate.ps1
```

### Install dependencies

```bash
pip install -r requirements.txt
```

### Environment Variables

Create a `.env` file in the `backend` directory.

```env
GARMIN_EMAIL=your_email@example.com
GARMIN_PASSWORD=your_password
```

**Never commit `.env` or Garmin authentication tokens to Git.**

## Current Status

🚧 **Early development**

The current priority is establishing a reliable connection to Garmin Connect and understanding the data available through the Garmin integration.

The first milestone is:

```text
Garmin Connect
      ↓
Python
      ↓
Retrieve Garmin profile
      ↓
Retrieve recent activities
```

Once this is working reliably, the database and dashboard will be developed around the actual Garmin data available.

## Disclaimer

This is a personal project and is not affiliated with or endorsed by Garmin.

Garmin data access may rely on unofficial Garmin Connect integrations and could change if Garmin changes its authentication or APIs.
