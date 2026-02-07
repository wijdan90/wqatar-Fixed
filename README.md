# WQatar Projectile Motion Virtual Lab (RO1 Data Collection)

This repository contains a **React + TypeScript** virtual laboratory for **Projectile Motion** with **research-grade temporal interaction logging**.

## Why this exists (PhD Methodology Context)
Phase 1 of the methodology focuses on **data acquisition and preparation** for **sequential learner modelling (RO1)**.
The lab logs **millisecond timestamps**, **state snapshots**, **temporal gaps**, and **derived behaviour codes** to support:
- sequence modelling (LSTM / Transformer),
- clustering by inquiry strategy,
- process-based assessment (RO2) and adaptive feedback (RO3) in later phases.

## Quick start
### Prerequisites
- Node.js 18+ and npm

### Install & run
```bash
npm install
npm run dev
```

## Data captured
Each learner action is logged as an event with:
- `timestamp_ms` (ms precision)
- `sequenceNumber`
- `actionType` (slider changes, fire, hint, task switch, etc.)
- `derivedCode` (Explore / Test / Adjust / Confirm / Idle / Help / Attempt)
- `state` snapshot (velocity, angle, projectile position, current task, attempts, hint count)
- `temporal` features (gap from previous, session time, challenge time)

Events are stored in Firebase Realtime DB under:
- `/sessions/{sessionId}/metadata`
- `/sessions/{sessionId}/events`
- `/sessions/{sessionId}/temporalMetrics`
- `/sessions/{sessionId}/challenges/{challengeId}`

## Export
Use the **Export panel** in the UI to download:
- CSV: `session_{sessionId}_events.csv`
- JSON: `session_{sessionId}_events.json`

These files are suitable for downstream preprocessing, clustering, and sequential modelling.

## Notes
- The lab does **not** collect personal identifiers by default.
- If you add a `student_id`, keep it **pseudonymous**.

