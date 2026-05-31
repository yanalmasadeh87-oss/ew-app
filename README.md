# EW Strategy V6 — Halal Crypto Trading Bot

Adaptive structure-aware trading bot for halal cryptocurrency pairs. Analyzes each chart based on its own price behavior and Elliott Wave structure, not fixed rules.

## Features

- **Adaptive Analysis** — Chart decides the method (EW, patterns, trend)
- **Hard Score Ceilings** — Trend signals capped at 55, EW structures up to 100
- **WATCH-Only Trend** — Trend continuation requires 3xHH/HL, ADX>30, HTF bullish
- **No EW/Fib Bonus for Trend** — Reserved for real EW structures only
- **Volatility Regime Detection** — Adjusts pivots and risk per market conditions
- **Structure Memory** — Anti flip-flop, locks valid structures for 30 days
- **HTF Weekly Validation** — Blocks signals against weekly trend
- **Position Sizing** — By score, volatility, and trend strength
- **Telegram Alerts** — Real-time signals, watches, TP/SL hits
- **70-Coin Watchlist** — Tier 1-3 halal coins

## Scoring Table (Hard Ceilings)

| Structure | Max Score | EW Bonus | Fib Bonus | Notes |
|-----------|-----------|----------|-----------|-------|
| TREND_CONTINUATION | 55 | 0 | 0 | Trend only, NO EW/Fib |
| IMPULSE_W3_LIKELY | 55 | 0 | 0 | WATCH only, 3xHH/HL, ADX>30 |
| EARLY_TREND | 50 | 0 | 0 | WATCH only, weakest signal |
| EW_W2 / EW_W4 | 100 | 25 | 15 | Full EW validation |
| ABC_ZIGZAG | 100 | 25 | 15 | Full EW validation |
| WXYXZ | 95 | 20 | 12 | Complex but validated |
| EXPANDED_FLAT | 90 | 18 | 10 | Validated correction |
| RUNNING_CORRECTION | 85 | 15 | 8 | Validated correction |
| DOUBLE_BOTTOM | 80 | 12 | 8 | Pattern only |
| FALLING_WEDGE | 75 | 10 | 5 | Pattern only |

## Setup

### 1. Environment Variables

```bash
export TELEGRAM_BOT_TOKEN="your_bot_token"
export TELEGRAM_CHAT_ID="your_chat_id"
```

### 2. Install Dependencies

```bash
pip install -r requirements.txt
```

### 3. Run

```bash
python signal_bot.py
```

## File Structure

```
Hal-coin/
├── signal_bot.py      # Main bot (V6 fixed)
├── requirements.txt   # Dependencies
└── README.md          # This file
```

## Security

- Bot token loaded from `os.getenv()` — never hardcoded
- Regenerate token if previously exposed
- No private keys or API secrets in code

## Disclaimer

This is for educational purposes only. Not financial advice. Trade at your own risk.
