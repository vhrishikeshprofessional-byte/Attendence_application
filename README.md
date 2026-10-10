# Attendance Management System

This is a full-stack Attendance Management System featuring a FastAPI backend, a React/Vite frontend, and a MongoDB database.

## Prerequisites

Ensure you have the following installed on your system:
- **Node.js** (v18+ recommended) & npm
- **Python** (v3.9+ recommended)
- **Docker** & **Docker Compose** (for running the MongoDB database)

## Project Structure

- `attendance-backend/`: FastAPI backend application.
- `attendance-frontend/`: React + Vite frontend application.
- `docker-compose.yml`: Docker configuration for the MongoDB replica set.

---

## 🚀 How to Start the Application (Manual Way)

To run the application locally for development, you need to start the database, the backend server, and the frontend server separately.

### 1. Start the Database (MongoDB)

The application uses MongoDB, configured as a replica set (`rs0`) in the `docker-compose.yml` file.

1. Open a terminal in the root directory.
2. Run the following command to start the MongoDB container in the background:
   ```bash
   docker-compose up -d
   ```
3. The database will be accessible at `localhost:27017`.

### 2. Start the Backend (FastAPI)

1. Open a new terminal and navigate to the backend directory:
   ```bash
   cd attendance-backend
   ```
2. Create and activate a Python virtual environment:
   - **Windows:**
     ```bash
     python -m venv .venv
     .venv\Scripts\Activate.ps1
     ```
   - **Mac/Linux:**
     ```bash
     python3 -m venv .venv
     source .venv/bin/activate
     ```
3. Install the required Python dependencies:
   ```bash
   pip install -r requirements.txt
   ```
4. Set up the environment variables:
   - Copy `.env.example` to a new file named `.env`:
     ```bash
     cp .env.example .env
     ```
     *(On Windows Command Prompt, use `copy .env.example .env`)*
   - *(Optional)* Update the `.env` file with your specific configurations.
5. Start the FastAPI server using Uvicorn:
   ```bash
   uvicorn app.main:app --reload
   ```
6. The backend server will be running at `http://localhost:8000`. You can access the interactive API documentation at `http://localhost:8000/docs`.

### 3. Start the Frontend (React + Vite)

1. Open a new terminal and navigate to the frontend directory:
   ```bash
   cd attendance-frontend
   ```
2. Install the Node.js dependencies:
   ```bash
   npm install
   ```
3. Set up the environment variables:
   - Copy `.env.example` to a new file named `.env`:
     ```bash
     cp .env.example .env
     ```
     *(On Windows Command Prompt, use `copy .env.example .env`)*
4. Start the frontend development server:
   ```bash
   npm run dev
   ```
5. The frontend will be accessible at the URL provided in the terminal (usually `http://localhost:5173`).

---

## 🐳 Docker Setup Review

As requested, I have reviewed the current Docker setup in the repository without making any changes:

- **Current State:** The repository currently has a `docker-compose.yml` file located at the root. This file is specifically configured to spin up a **MongoDB 7.0** instance.
- **Replica Set Configuration:** The MongoDB container is initiated with a command to run as a replica set (`rs0`). It also includes a robust healthcheck that automatically initiates the replica set using `mongosh`, ensuring the database is fully ready for transactions.
- **Backend/Frontend Dockerization:** Currently, there are no `Dockerfile`s present in either the `attendance-backend` or `attendance-frontend` directories. Therefore, a complete full-stack `docker-compose up` setup (where the backend and frontend are also containerized) is not yet implemented.
- **Conclusion:** The Docker setup is perfectly configured for local development of the backend/frontend (by providing an isolated MongoDB replica set). If a fully containerized deployment is desired in the future, Dockerfiles will need to be added for both the Node and Python apps.
