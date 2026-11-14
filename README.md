# CarePulse — AI Healthcare Appointment & Risk Analytics

CarePulse is an educational full-stack demonstration that estimates the likelihood of an appointment no-show, explores attendance patterns, and presents an appointment risk queue.

## Features
- Synthetic appointment dataset generator
- Scikit-learn Random Forest classification pipeline
- No-show risk probability and Low / Moderate / High bands
- Individual appointment risk assessment API
- Dashboard with appointment queue and model evaluation metrics
- FastAPI backend and React + Vite frontend

## Important data and safety notice
This repository currently uses **synthetic demonstration data generated in code**. The target labels are created using an illustrative probability formula. Metrics are therefore demonstration metrics only and must not be interpreted as evidence of real-world predictive performance. The app does not use real patient records, make diagnoses, or provide medical advice. Risk scores must not be used to deny, delay, or deprioritise care. Any real deployment would require validated, representative data, privacy/security review, fairness evaluation, clinical and operational governance, and human oversight.

## Requirements
- Python 3.11 or 3.12 recommended
- Node.js 20+ recommended

## Run the backend (PowerShell)
```powershell
cd backend
py -3.12 -m venv .venv
.\.venv\Scripts\Activate.ps1
python -m pip install --upgrade pip
python -m pip install -r requirements.txt
python -m uvicorn app.main:app --reload
```
If the Python launcher cannot find Python 3.12, use the full path to your installed Python executable to create `.venv`.

API docs: http://127.0.0.1:8000/docs

## Run the frontend
Open a second terminal:
```powershell
cd frontend
npm.cmd install
npm.cmd run dev
```
Open the local URL printed by Vite, usually http://localhost:5173.

## API
- `GET /api/health`
- `GET /api/metrics`
- `GET /api/overview`
- `GET /api/appointments`
- `POST /api/assess`

Example request:
```json
{
  "age": 42,
  "lead_days": 18,
  "previous_no_shows": 2,
  "previous_appointments": 8,
  "distance_km": 12,
  "hour": 10,
  "day_of_week": 1,
  "sms_received": 0,
  "appointment_type": "General"
}
```

## Suggested next research-grade upgrades
1. Replace synthetic data with a documented, appropriately licensed real dataset.
2. Use a time-aware train/test split and prevent target leakage.
3. Evaluate calibration, precision, recall, F1, PR-AUC, ROC-AUC, and subgroup performance.
4. Add explainability, audit logs, secure authentication, database persistence, and consent-aware data handling.
5. Validate any reminder workflow with stakeholders and ensure it supports access to care rather than restricting it.
