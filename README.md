# Predictive Maintenance of Aircraft Engines — Deployment

Deployment work for the MLOps-based DataScience Process Model. Estimates the Remaining Useful Life (RUL) of turbofan
engines and serves predictions through a dashboard.

## Structure

    deployment/
      dashboard/    Frontend: fleet health monitor (HTML/JS + Chart.js)
      backend/      FastAPI prediction service (in progress)

## Dashboard (current state)

A single-page dashboard running on fixed sample data drawn from the real test
set, so it works with no backend yet. Features:
- Monitoring strip: predictions served, latency, healthy/critical counts
- Operations: fleet replay + click-through engine detail
- Test bench: manual predict + synthetic stream (labelled simulated)

Open `deployment/dashboard/index.html` in a browser to run it.

## Model integration

All predictions route through one function, `predictRUL()`, in
`dashboard/index.html`. It is currently a mock using recorded test data; at
deployment it is pointed at the backend `/predict` endpoint. Return shape stays
`{ rul, status }`.

## Status
- [x] Dashboard frontend (mock data)
- [ ] FastAPI backend
- [ ] Containerization (Docker)
- [ ] Cloud deployment
