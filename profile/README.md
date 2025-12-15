# SkillTrade

SkillTrade is a community marketplace for exchanging services using an internal digital currency and a reputation system that keeps trades fair and accountable.

---

## Project Documentation
- Full process, diagrams, and system details: https://medium.com/@ctovar_77925/this-is-a-test-1474b35bc5fc

---

## Table of Contents
- Overview
- Services
- Local Deployment
- Cloud Deployment
- Team

---

## Overview
SkillTrade connects people who can offer help with those who need it. Members publish offers, hire services, pay with in-app credits, and rate each other so the community can identify trustworthy providers. The platform is composed of independent FastAPI microservices backed by MongoDB, plus a mobile client.

---

## Services
**usuarios-api**  
FastAPI + MongoDB service for user management. Handles registration with encrypted passwords, profile updates, deletions, individual and bulk queries, and exposes Swagger docs at `/docs`. Default port: `8001`. Repo: https://github.com/p1-SwEng2-2025i-Ornitorrinco/usuarios-api.git

**ServicioPublicarOferta**  
FastAPI + MongoDB service for publishing and browsing offers. Supports CRUD for offers (title, description, category, location, keywords, cost, schedule, client info), image upload/serving, categories CRUD, filtering, pagination, and CORS. Swagger available at `/docs`. Default port: `8002`. Repo: https://github.com/p1-SwEng2-2025i-Ornitorrinco/SevicioPublicarOferta.git

**transacciones-api**  
FastAPI + MongoDB service that manages the internal currency, balances, and transfers. Provides JWT-based auth helpers, role checks for admin operations, transaction history endpoints, and Prometheus metrics instrumentation. Default port: `8000` (configurable via `PORT`). Repo: https://github.com/p1-SwEng2-2025i-Ornitorrinco/transacciones-api.git

**reviews-service**  
FastAPI + MongoDB service for reviews and reputation. Creates, lists, and deletes reviews, recalculates aggregate reputation, and can call `usuarios-api` to persist updated scores. Exposes health/metrics endpoints and Swagger at `/docs`. Default port: `8003`. Repo: https://github.com/p1-SwEng2-2025i-Ornitorrinco/reviews-service.git

**SkilltradeMovil**  
Flutter mobile client that consumes the microservices above. Repo: https://github.com/Dacosta99/SkilltradeMovil.git

---

## Local Deployment
These steps spin up all backend services locally. Run each service in its own terminal.

### Prerequisites
- Python 3.9+ and `pip`
- Git
- MongoDB running locally (e.g., `mongodb://localhost:27017`)
- Optional: Flutter SDK if you want to run the mobile client

### 1) Clone the repos
```bash
# Backend services
git clone https://github.com/p1-SwEng2-2025i-Ornitorrinco/usuarios-api.git
git clone https://github.com/p1-SwEng2-2025i-Ornitorrinco/SevicioPublicarOferta.git
git clone https://github.com/p1-SwEng2-2025i-Ornitorrinco/transacciones-api.git
git clone https://github.com/p1-SwEng2-2025i-Ornitorrinco/reviews-service.git

# Mobile app
git clone https://github.com/Dacosta99/SkilltradeMovil.git
```

### 2) Environment variables (examples)
Create a `.env` in each service folder with values for your setup:

- **usuarios-api**
  ```env
  MONGODB_URI=mongodb://localhost:27017
  PORT=8001
  ```

- **ServicioPublicarOferta**
  ```env
  MONGODB_URI=mongodb://localhost:27017
  PORT=8002
  ```

- **transacciones-api**
  ```env
  MONGODB_URI=mongodb://localhost:27017
  SECRET_KEY=super-secret-key
  PORT=8000
  ```

- **reviews-service**
  ```env
  MONGO_URI=mongodb://localhost:27017/servicios_app
  PORT=8003
  USUARIOS_API_URL=http://localhost:8001
  ```

### 3) Install dependencies and run
Repeat per service (example for `usuarios-api`—adjust the path and port for each one):
```bash
cd usuarios-api
python -m venv .venv
source .venv/bin/activate  # Windows: .venv\Scripts\activate
pip install -r requirements.txt
uvicorn app.main:app --reload --port 8001
```

- `ServicioPublicarOferta`: ensure an `images/` folder exists; run `uvicorn app.main:app --reload --port 8002`.
- `transacciones-api`: run `uvicorn app.main:app --reload --port 8000` (uses JWT helpers and Prometheus metrics at `/metrics`).
- `reviews-service`: run `uvicorn app.main:app --reload --port 8003`.

Each service exposes interactive docs at `http://localhost:<port>/docs`.

### 4) (Optional) Run the mobile app
```bash
cd SkilltradeMovil
flutter pub get
flutter run
```
Update API base URLs in the app config to point at your local ports.

---

## Cloud Deployment
- **Frontend (Vercel):** deployed at https://skilltrade-movil.vercel.app/
- **Backend (Heroku):** FastAPI services are hosted on Heroku dynos. Set each service's config vars (`MONGODB_URI`, `PORT`, `SECRET_KEY`, `USUARIOS_API_URL`, etc.) in the Heroku dashboard. The `PORT` is provided by Heroku at runtime; start commands should read it (e.g., `uvicorn app.main:app --host 0.0.0.0 --port $PORT`).
- **Database (MongoDB Atlas):** each service points to an Atlas cluster via its Mongo URI. Store the Atlas connection string in the corresponding env var (`MONGODB_URI` or `MONGO_URI`). Ensure IP allowlisting and credentials are configured in Atlas. If using multiple databases/collections, keep consistent names across services (e.g., `intercambio_servicios` for users/transactions, `servicios_app` for offers/reviews).

Deployment tips:
- Configure CORS to allow the Vercel domain and any custom domains used by the APIs.
- Keep secrets out of repos; use Heroku config vars and Atlas users.
- Verify each service's `/health` or root endpoint after deploy, then check `/docs`.
- Update the mobile/SPA base URLs to point at the Heroku app URLs.

---

## Team
- Tatiana Acelas
- Nicolás Quezada
- Esteban Rodríguez
- Edinson Sánchez
- Cristian Tovar
- Danny Yaluzán
