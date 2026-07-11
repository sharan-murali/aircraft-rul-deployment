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
- 
- ## Design overview
See [docs/deployment-dashboard-overview.pdf] for a walkthrough of each dashboard section and its purpose.

## Live dashboard

**https://aircraft-rul.netlify.app/**

A working fleet health monitor running on sample data from the test set.
The trained model is wired in at the backend stage; predictions currently
route through a mock function (`predictRUL()`) designed as a single swap point.

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
