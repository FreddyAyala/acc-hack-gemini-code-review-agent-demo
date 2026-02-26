# Technical Onboarding Guide: Modernized Retail App

Welcome to the modernized **Cymbal Retail User API**! This application has been refactored from a synchronous Flask app to a high-performance, asynchronous **FastAPI** microservice.

## 🚀 Tech Stack
- **Framework:** FastAPI (Asynchronous Python)
- **Database Driver:** `asyncpg` (Async PostgreSQL)
- **Backend:** AlloyDB for PostgreSQL
- **Containerization:** Docker
- **Deployment:** Cloud Run (Serverless)

## 🏗️ Architecture & Data Flow
1.  **Client Request:** A client sends an HTTP request to the Cloud Run service.
2.  **FastAPI Routing:** The request is handled by an asynchronous route in `app/main.py`.
3.  **Dependency Injection:** Database connections are managed via a connection pool in `app/database.py`, injected into routes using FastAPI's `Depends`.
4.  **Async Persistence:** Data is fetched/written asynchronously to **AlloyDB** using `asyncpg`.
5.  **JSON Response:** The API returns a structured JSON response validated by **Pydantic** models.

## 📂 Project Structure
- `app/`
    - `main.py`: Core API logic, routes, and logging.
    - `database.py`: Async connection pool management.
    - `models.py`: Pydantic data schemas for validation.
    - `config.py`: Environment configuration and settings management.
- `init/`: Database initialization scripts.
- `Dockerfile`: Multi-stage build for efficient containerization.
- `compose.yaml`: Local development and testing environment.

## 🛠️ Key Endpoints
- `GET /health`: Asynchronous database health check.
- `GET /api/users`: List all users (Asynchronous).
- `POST /api/users`: Create a new user with validation.
- `GET /api/users/{id}`: Fetch user by ID.
- `DELETE /api/users/{id}`: Secure asynchronous deletion.

## 🔐 Security & Operations
- **Asynchronous Execution:** Prevents blocking IO, improving throughput.
- **Structured Logging:** JSON-formatted logs for Cloud Logging integration.
- **Environment Driven:** Configuration via environment variables (`DB_HOST`, `DB_USER`, etc.).
