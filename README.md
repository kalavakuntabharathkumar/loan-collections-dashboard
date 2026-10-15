# Loan Collections Dashboard (React + Node)

Responsive collections work queue with search, status filtering, follow-up notes, a binary min-heap priority queue, Express API, optional MongoDB persistence, Jest tests and GitHub Actions CI. Seed data is fictional. Resume metrics are not benchmarked by this demo.

## Run
Requires Node.js 20+. In the project folder:

```bash
npm install
npm run dev
```
Frontend: `http://localhost:5173` · API: `http://localhost:3001/api/accounts`

The UI works with in-memory demo data by default. For MongoDB persistence, set `MONGODB_URI` and optionally `MONGODB_DB=collections` before starting the server. For example in PowerShell: `$env:MONGODB_URI='mongodb://localhost:27017'; npm run dev`. Vite proxies are not configured, so the UI fetch currently targets `/api/accounts`; use a same-origin reverse proxy in deployment or add a Vite proxy for local split-port development.

## API
- `GET /api/health` — health status
- `GET /api/accounts` — list collection accounts
- `PATCH /api/accounts/:id` — update `status` and/or `lastNote`

## Tests and build
```bash
npm test
npm run build
```

## Notes
Priority score is a simple demo heuristic using overdue days and balance; validate business rules with collections stakeholders before production. Add authentication, authorization, audit logging, pagination, rate limiting, input schemas, observability, and proper secret handling before deployment. Cloud Run manifest is a template, not a complete deployment.
