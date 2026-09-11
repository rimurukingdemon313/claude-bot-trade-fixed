# Paper Trading Bot Dashboard (TradeLocker)

A trading dashboard and API server with a Python analysis, risk and TradeLocker
integration layer.

## Stack

- **Frontend** — React 19, Vite 7, Tailwind CSS v4, shadcn-style UI components (`src/`)
- **API server** — Express 5 with pino logging and a trading scheduler (`server/`)
- **Analysis / trading** — Python standard-library modules: `analysis_engine/`,
  `market_data.py`, `risk_engine.py`, `tradelocker_client.py`, `tradelocker_state.py`,
  `economic_calendar.py`
- **Tests** — `tests/` (pytest)

## Getting started

```sh
npm install
npm run build     # build the frontend
npm start         # bundles the server and serves the app
```

Type checking:

```sh
npm run typecheck
```

Python tests:

```sh
pytest
```

## Configuration

Copy `.env.example` to `.env` and fill in real values. Never commit real
credentials.

| Variable | Purpose |
| --- | --- |
| `TRADELOCKER_EMAIL` / `TRADELOCKER_PASSWORD` | TradeLocker account login |
| `TRADELOCKER_SERVER` / `TRADELOCKER_ACC_ID` / `TRADELOCKER_URL` | TradeLocker account and endpoint |
| `GEMINI_API_KEY` | Primary AI decision provider |
| `GROQ_API_KEY` | Fallback AI providers |
| `PORT` | Server port |

## Deployment

A `Dockerfile` is included (Node 20 + Python 3). The container builds the
frontend and starts the server:

```sh
docker build -t paper-trading-dashboard .
docker run -p 3000:3000 --env-file .env paper-trading-dashboard
```

Any host that supports Docker or Node 20 (Railway, Fly.io, Render) works.
Set the environment variables listed above on the host.

## Demo

```sh
python run_smc_demo.py
```
