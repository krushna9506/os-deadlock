# Deadlock Lab

An interactive operating systems laboratory dashboard for visualizing and analyzing deadlock avoidance, detection, prevention, and recovery.

🌐 **Live Demo:** [https://os-deadlock-dashboard-d4vh.onrender.com](https://os-deadlock-dashboard-d4vh.onrender.com)

---

## Overview & How It Works

Deadlock Lab provides a hands-on environment to inspect and interact with classic operating system resource allocation algorithms:

1. **Deadlock Avoidance (Banker’s Algorithm)**
   - Configurable dimensions: dynamically adjust process count (2–8) and resource types (1–5).
   - Real-time calculation of the `Need` matrix ($\text{Need} = \text{Maximum} - \text{Allocation}$).
   - Step-by-step interactive execution of the safety algorithm with forward/back controls, autoplay, and Work-vector timeline charts.
   - Resource-request validation: tests whether a request can be granted safely or must be deferred or denied with automatic trial rollback.

2. **Deadlock Detection & Recovery**
   - Implements the multiple-instance resource detection algorithm.
   - Renders a live, interactive directed **Resource-Allocation Graph (RAG)** displaying assignment edges, request edges, and node states.
   - Distinct visual highlighting of deadlocked process sets.
   - Interactive process termination recovery: abort a process to release its held resources back to `Available` and break the cycle.

3. **Deadlock Prevention**
   - Demonstrates the elimination of the **Circular Wait** Coffman condition using Havender’s linear resource ordering rule ($R_0 < R_1 < R_2 < \dots$).
   - Interactive policy toggle testing whether out-of-order acquisitions are permitted or rejected.

4. **Shared Kitchen Simulation**
   - An everyday physical metaphor (roommates sharing stove spaces and blenders to cook breakfast) demonstrating how Banker's algorithm schedules finite shared resources without deadlock.

---

## Tech Stack

- **Frontend:** React 18, TypeScript, Vite, React Flow (`@xyflow/react`), Recharts, Lucide Icons
- **Backend:** Python 3, FastAPI, Uvicorn, Pydantic
- **Styling:** Custom accessible theme compliant with WCAG 2.2 contrast requirements and reduced-motion preferences

---

## Local Installation & Setup

### Prerequisites
- [Node.js](https://nodejs.org/) (v18 or higher)
- [Python](https://www.python.org/) (v3.10 or higher)
- Git

### 1. Clone the Repository
```bash
git clone https://github.com/krushna9506/os-deadlock.git
cd os-deadlock
```

### 2. Backend Setup
Create a virtual environment and install dependencies:

```powershell
# Windows
py -m venv .venv
.venv\Scripts\pip install -r backend\requirements.txt
```

```bash
# macOS / Linux
python3 -m venv .venv
source .venv/bin/activate
pip install -r backend/requirements.txt
```

### 3. Frontend Setup
Install npm dependencies for the client:

```bash
cd frontend
npm install
cd ..
```

---

## Running the Dashboard Locally

### Option A: One-Click Launcher (Recommended)
On Windows, simply double-click `run_dashboard.bat`, or run:
```bash
py start.py
```
This launcher starts both the FastAPI backend and Vite frontend and opens your default browser automatically.

### Option B: Manual Execution

1. **Start the Backend API:**
   ```bash
   # From the project root
   .venv\Scripts\python -m uvicorn main:app --app-dir backend --host 127.0.0.1 --port 8000
   ```
   API health endpoint: [http://127.0.0.1:8000/api/health](http://127.0.0.1:8000/api/health)

2. **Start the Frontend Development Server:**
   ```bash
   cd frontend
   npm run dev
   ```
   Open your browser at: [http://127.0.0.1:5173](http://127.0.0.1:5173)

---

## Deployment (Render)

This repository includes a `render.yaml` blueprint configuring:
- A static web service for the React/Vite dashboard.
- A Python web service running FastAPI via Uvicorn.

To deploy your own instance, connect this repository to [Render](https://render.com) using **New + > Blueprint**.
