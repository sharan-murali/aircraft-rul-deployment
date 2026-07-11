# Engine Fleet Health Monitor — frontend (mock-data build)

A single-page dashboard for the predictive-maintenance project. Runs entirely on
fixed sample data drawn from the real test set, so it works with no backend yet.
The trained model is wired in later by swapping one function.

## Files
- `index.html`  — the whole app (layout, styles, logic)
- `fleet-data.js` — real sample rows: engine id, recorded life, true RUL, sensor trajectory

## Features
- Monitoring strip (predictions served, latency, healthy/critical counts) — always on
- Operations: fleet replay (press Play to age the engines) + click any engine for detail
- Test bench: manual predict + synthetic stream (clearly labelled simulated)

## Wiring in the real model later
Everything routes through one function, `predictRUL()`, near the top of the
script in `index.html`. Right now it's a mock that uses each engine's true RUL.
At deployment, replace its body with a `fetch()` call to the FastAPI `/predict`
endpoint. The return shape must stay the same: `{ rul, status }`.
A commented template for the real version sits directly below the mock.

## Note for the report
The fleet/detail views REPLAY recorded test engines (not a live feed); the
synthetic stream is clearly labelled simulated. Manual predict is genuine live
inference once the backend is connected.
