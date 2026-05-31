# EW Strategy V6 — Adaptive Structure-Aware Trading Bot

> **Signal-only bot** for cryptocurrency swing and scalp trading using Elliott Wave analysis, adaptive pivot detection, and multi-timeframe trend validation.

---

## ⚡ Features

| Feature | Description |
|---------|-------------|
| **Adaptive Analysis** | Each chart gets its own method — no fixed rules |
| **Trend Continuation** | Detects Wave 3 / parabolic moves even without 5 complete pivots |
| **Structure Memory** | Locks impulse structures for 30 days — prevents flip-flopping |
| **Phase Override** | HTF bullish context overrides LTF "correction" labels |
| **Dynamic Position Sizing** | Based on score, volatility regime, and trend strength |
| **Multi-Timeframe** | Daily (swing) + 4H (scalp) + Weekly (HTF validation) |
| **Market Context** | Fear & Greed, BTC dominance, total market cap trends |
| **Risk Management** | ATR-based SL with EW-specific invalidation levels |
| **Price Alerts** | Auto TP1-TP4 alerts with trailing SL updates |
| **Watch Monitor** | Watches can promote to signals when conditions mature |

---

## 🚀 Quick Start

### 1. Get Telegram Credentials

- **Bot Token**: Message [@BotFather](https://t.me/botfather) → `/newbot`
- **Chat ID**: Message [@userinfobot](https://t.me/userinfobot) or run:
  ```
  curl https://api.telegram.org/bot<TOKEN>/getUpdates
  ```

### 2. Set Environment Variables

**Linux/Mac:**
```bash
export TELEGRAM_BOT_TOKEN="your_token_here"
export TELEGRAM_CHAT_ID="your_chat_id_here"
```

**Windows:**
```cmd
set TELEGRAM_BOT_TOKEN=your_token_here
set TELEGRAM_CHAT_ID=your_chat_id_here
```

**Replit:**
- Go to Secrets (lock icon) → Add `TELEGRAM_BOT_TOKEN` and `TELEGRAM_CHAT_ID`

### 3. Run

```bash
pip install requests
python EW_Strategy_V6_GitHub_Safe.py
```

---

## 📊 How It Works

```
┌─────────────────┐     ┌──────────────────┐     ┌─────────────────┐
│  Fetch Data     │────▶│  Detect Pivots   │────▶│  Classify       │
│  (Binance API)  │     │  (Adaptive)      │     │  Structure      │
└─────────────────┘     └──────────────────┘     └─────────────────┘
                                                        │
        ┌───────────────────────────────────────────────┘
        ▼
┌─────────────────┐     ┌──────────────────┐     ┌─────────────────┐
│  Score & Risk   │◄────│  Trend + Context  │◄────│  Memory Check   │
│  (Position Size)│     │  (HTF/ADX/F&G)   │     │  (Anti-Flip)    │
└─────────────────┘     └──────────────────┘     └─────────────────┘
        │
        ▼
┌─────────────────┐     ┌──────────────────┐
│  Signal/BUY     │────▶│  Telegram Alert  │
│  or WATCH       │     │  + Price Monitor │
└─────────────────┘     └──────────────────┘
```

---

## 🎯 Signal Types

| Type | Timeframe | Min Score | Hold Time |
|------|-----------|-----------|-----------|
| **SWING** | 1D | 50/100 | Days to weeks |
| **SCALP** | 4H | 45/100 | 1-3 days |

### Structure Types Detected

- `TREND_CONTINUATION` — Wave 3 / parabolic / early trend
- `EW_W2` — Elliott Wave 2 pullback entry
- `EW_W4` — Elliott Wave 4 correction entry
- `ABC_ZIGZAG` — Classic zigzag correction
- `EXPANDED_FLAT` — Expanded flat correction
- `RUNNING_CORRECTION` — Running correction (bullish)
- `WXYXZ` — Triple combination
- `DOUBLE_BOTTOM` — Classical pattern
- `FALLING_WEDGE` — Classical pattern

---

## ⚙️ Configuration

Edit the `HALAL_WATCHLIST` in the script to customize coins:

```python
HALAL_WATCHLIST = [
    {"sym":"BTC","tier":1},   # Tier 1: Highest priority
    {"sym":"ETH","tier":1},
    {"sym":"XRP","tier":1},
    # ... add your coins
]
```

**Tiers:**
- ⭐⭐⭐ Tier 1: Scanned first, wider signal thresholds
- ⭐⭐ Tier 2: Standard scanning
- ⭐ Tier 3: Lower priority, stricter thresholds

---

## 🔒 Security

- **Never commit real API keys** — use environment variables
- **Signal-only bot** — does NOT execute trades automatically
- **No private keys or exchange API secrets** required

---

## 📁 Files

| File | Description |
|------|-------------|
| `EW_Strategy_V6_GitHub_Safe.py` | Main bot (use this) |
| `EW_Strategy_V6_Corrected.py` | Original with placeholders |
| `EW_Strategy_V5_Adaptive.html` | HTML dashboard (visual backtesting) |

---

## ⚠️ Disclaimer

**For educational purposes only. Not financial advice.**

- Always do your own research
- Test on paper trading first
- Past performance does not guarantee future results
- Cryptocurrency trading carries significant risk

---

## 🛠️ Built With

- Python 3.8+
- `requests` (Binance API + Telegram API)
- Binance Public API (no API key needed)
- Alternative.me (Fear & Greed + market context)

---

## 📜 License

MIT — Use at your own risk.
