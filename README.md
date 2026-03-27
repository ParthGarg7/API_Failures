# API Failure Simulation Lab

A hands-on repository designed to **understand, reproduce, and debug real-world API failures**.

Instead of just reading about errors like *rate limiting* or *timeouts*, this repo lets you **run them locally**, observe behavior, and learn how systems fail in practice.

---

##  Purpose

This project provides:

*  **Real-world API failure scenarios**
*  **Minimal reproducible backend simulations (FastAPI)**
*  **Frontend to trigger and visualize failures (React + Vite)**
*  **Dockerized setup (no virtual environments needed)**
*  **CI testing using GitHub Actions**

The goal is simple:

> If you understand how something breaks, you can design better systems.

---

## Project Structure

```
.
│   .gitignore
│   README.md
│
├── authentication/
│   ├── docker-compose.yml
│   ├── Dockerfile
│   ├── main.py
│   └── requirements.txt
│
├── rate-limiting/
│   ├── docker-compose.yml
│   ├── Dockerfile
│   ├── main.py
│   └── requirements.txt
│
├── timeout/
│   ├── docker-compose.yml
│   ├── Dockerfile
│   ├── main.py
│   └── requirements.txt
│
└── frontend/
    ├── .dockerignore
    ├── Dockerfile
    ├── index.html
    ├── package.json
    ├── tsconfig.json
    ├── tsconfig.node.json
    ├── vite.config.ts
    └── src/
        ├── App.tsx
        ├── main.tsx
        └── vite-env.d.ts
```

---

##  Tech Stack

### Backend

* FastAPI
* Python
* Docker

Each failure type has its **own isolated service**

### Frontend

* React (TypeScript)
* Vite

Used to:

* Trigger API calls
* Simulate load
* Visualize responses/errors

### DevOps

* Docker & Docker Compose
* GitHub Actions (CI testing)

---

##  Available Failure Simulations

| Folder           | Scenario Description                                         |
| ---------------- | ------------------------------------------------------------ |
| `rate-limiting`  | Simulates HTTP 429 errors under high request load            |
| `timeout`        | Simulates delayed responses leading to client/server timeout |
| `authentication` | Simulates auth failures (invalid tokens, missing headers)    |

More scenarios will be added:

* Circuit breaker failures
* Dependency failures
* Database connection drops
* Memory exhaustion

---

##  How to Run

### 1. Clone the Repo

```bash
git clone <your-repo-url>
cd <repo-name>
```

---

### 2. Run Any Failure Scenario

Example: Rate Limiting

```bash
cd rate-limiting
docker-compose up --build
```

---

### 3. Run Frontend

```bash
cd frontend
docker build -t api-failure-frontend .
docker run -p 5173:5173 api-failure-frontend
```

---

##  How to Use This Repo Effectively

1. Start a backend failure service (e.g. rate-limiting)
2. Trigger requests via:

   * Frontend UI
   * Postman
   * Curl / scripts
3. Observe:

   * Status codes (429, 408, etc.)
   * Response delays
   * Failure patterns
4. Modify code to:

   * Fix the issue
   * Improve resilience
   * Add retry mechanisms

---

##  Why Docker?

* No environment conflicts
* No need for virtual environments
* Reproducible setups across systems
* Easy isolation of each failure scenario

---

##  CI/CD (GitHub Actions)

This repo uses GitHub Actions to:

* Build Docker containers
* Run basic API tests
* Validate failure scenarios

You can extend workflows to:

* Load test APIs
* Validate error responses automatically

---

##  Design Philosophy

Each failure module is:

* Independent
* Minimal
* Reproducible
* Realistic

Every folder answers:

> "What does this failure look like in production?"

---

##  Future Improvements

* Add load testing scripts
* Add observability (logs, metrics)
* Add retry + fallback implementations
* Add distributed system failures
* Add frontend dashboards for error analytics

---

##  Contribution

Want to add a new failure scenario?

1. Create a new folder (e.g. `circuit-breaker/`)
2. Add:

   * `main.py`
   * `requirements.txt`
   * `Dockerfile`
   * `docker-compose.yml`
3. Keep it minimal and focused
4. Open a PR 🚀

---

##  License

MIT License

---

##  Final Thought

This repo is not about writing perfect code.

It is about **understanding imperfect systems**.

Because in real-world engineering:

> Systems don’t fail gracefully unless you design them to.
