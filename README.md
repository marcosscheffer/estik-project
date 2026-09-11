# 🚀 Estik Project (Monorepo with Git Submodules)

This repository serves as the main orchestrator for the **Estik** application, integrating the **Backend** and **Frontend** git submodules using Docker Compose.

---

## 📁 Repository Structure

.
├── backend/             # Git Submodule (Spring Boot API)
├── frontend/            # Git Submodule (React + Vite Interface)
├── docker-compose.yml   # Docker services orchestrator
└── README.md

---

## ⚙️ Prerequisites

* Git
* Docker Desktop (including Docker Compose)

---

## 📥 1. Cloning the Repository

Since this repository relies on submodules, make sure to clone them along with the main project.

### Clone everything at once (Recommended):
git clone --recurse-submodules <MAIN-REPOSITORY-URL>
cd estik-project

### If you already cloned without the `--recurse-submodules` flag:
git submodule update --init --recursive

---

## 🔄 2. Managing Submodules

### Update all submodules to the latest remote commit:
git submodule update --remote --merge

### Update a specific submodule (e.g., backend):
git submodule update --remote --merge backend

---

## 🔑 3. Environment Variables Setup

Before running the containers, create the `.env` files based on the examples provided in each folder:

1. **Backend:** Create `backend/.env`
2. **Frontend:** Create `frontend/.env`

---

## 🐳 4. Running with Docker Compose

From the root directory, start all services (PostgreSQL, pgAdmin, Spring Boot API, and NGINX Frontend):

docker compose up --build -d

### 🌐 Running Services:

| Service      | URL                   | Description                            |
| :----------- | :-------------------- | :------------------------------------- |
| Frontend     | http://localhost:3000 | Web Application (React/Vite)           |
| Backend API  | http://localhost:8080 | REST API (Spring Boot)                 |
| pgAdmin      | http://localhost:5050 | Postgres Management Interface          |
| PostgreSQL   | localhost:5432        | Relational Database                    |

---

## 🛠️ Useful Docker Commands

* Stream logs for all running containers:
  docker compose logs -f

* Stream logs for a specific service (e.g., API):
  docker compose logs -f app-api

* Stop and remove containers:
  docker compose down

* Stop containers and wipe database volumes:
  docker compose down -v

---

## 📝 Updating and Saving Submodule Changes

If you make changes inside the `backend` or `frontend` folders:

1. Navigate to the submodule folder, commit, and push your changes:
   cd backend
   git add .
   git commit -m "feat: add new API endpoint"
   git push origin main
   cd ..

2. From the root directory, commit the updated submodule reference:
   git add backend
   git commit -m "chore: update backend submodule pointer"
   git push origin main