# ew-app

**EW Strategy V7 Dashboard**

Real-time web dashboard for the Hal-coins-bot V7 trading strategy.

## Features

- **Live Market Context**: Fear & Greed Index, BTC Dominance, Market Cap trends
- **V7 Engine Status**: Real-time status of all 6 new engines
- **Active Signals**: Full signal cards with V7 engine data overlay
  - MTF Alignment (1D/4H/1H) — lazy-loaded, only shown when available
  - Candlestick Patterns — hammer, engulfing, morning star, etc.
  - Extended Wave Detection — W3/W5 extended labels
  - Liquidity BOS/CHoCH — break of structure indicators
- **Watch List**: Coins being monitored
- **Trade Stats**: Active trades, signals sent, scan count
- **Auto-refresh**: Updates every 30 seconds

## Setup

### Serve the dashboard

Option 1: Python HTTP server
```bash
python -m http.server 3000
# Open http://localhost:3000
```

Option 2: Node.js
```bash
npx serve .
```

Option 3: Any static file server

### API Connection

The dashboard connects to the bot's API server at `http://localhost:8080`.

Make sure the bot is running with the API server enabled:
```bash
python signal_bot.py  # API starts automatically on port 8080
```

### CORS

The bot's API server includes `Access-Control-Allow-Origin: *` headers, so the dashboard can run on any port/domain.

## API Endpoints

| Endpoint | Description |
|----------|-------------|
| `GET /api/status` | Bot version, market context, engine status, counts |
| `GET /api/signals` | Active signals, watches, trade stats |

## Dashboard Data Flow

```
┌─────────────┐     ┌─────────────┐     ┌─────────────┐
│  Bot API    │────▶│  Dashboard  │────▶│  Browser    │
│  :8080      │     │  index.html │     │  Render     │
└─────────────┘     └─────────────┘     └─────────────┘
```

## V7 Engine Data Display

The dashboard reads underscore-prefixed engine data from the API:

| Field | Source | Display |
|-------|--------|---------|
| `_mtf_alignment` | Lazy-loaded 1H data | 1D/4H/1H trend grid |
| `_candlestick_patterns` | Local candlestick engine | Pattern tags |
| `_extended_wave` | Extended wave detection | W3/W5 label |
| `_liquidity_info` | BOS/CHoCH engine | CHoCH/BOS badge |

These fields are only present when the coin passed all filters and the engines were activated.

## License
MIT
