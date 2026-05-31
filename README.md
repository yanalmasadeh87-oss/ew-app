# EW Strategy V6 Dashboard

HTML dashboard for visualizing EW Strategy V6 signals with hard market filters.

## Features

- **Live Market Bar** - BTC.D, TOTAL, TOTAL3, Fear & Greed with color status
- **Hard Ceiling Scoring Table** - Visible at top, all 10 structure types
- **Signal vs WATCH vs BLOCKED** - Green = trade, Orange = watch, Red = blocked
- **EW-Validated Border** - Purple for EW_W2/W4/ABC/WXYXZ
- **Trend-Only Border** - Blue for TREND_CONTINUATION (capped at 55)
- **Score Breakdown** - Ceiling, Raw score, Capped score under each bar
- **TP Hit Tracking** - Green highlight on TP1-TP4 when hit
- **Backtest Results** - Upload CSV/JSON to see win rate, avg return, best coin
- **Filters** - All / Signals / Watches / Blocked / EW / Trend / Tier 1-3

## Market Bar Colors

| Status | Color | Meaning |
|--------|-------|---------|
| OK | Green | Market healthy, signals allowed |
| CAUTION | Orange | Fear zone or falling total - reduced positions |
| BLOCKED | Red | Extreme fear or alt bloodbath - no entries |

## How to Use

1. **Export from bot** - The bot auto-saves `signals.json` every scan cycle
2. **Upload to dashboard** - Drag & drop `signals.json` or click upload area
3. **View signals** - Filter by type, tier, or blocked status
4. **Check market** - Top bar shows live market conditions from bot

## Files

- `index.html` - Main dashboard (this file)
- `signals.json` - Exported from bot (auto-generated)

## Demo

The dashboard loads with 6 demo signals showing:
- BTC EW_W4 at 88/100 (full signal)
- ETH ABC_ZIGZAG at 72/100 (full signal)
- SOL TREND at 50/100 (WATCH, ceiling 55)
- XRP EARLY_TREND at 45/100 (WATCH, ceiling 50)
- BTC Double Top (loss)
- SOL BLOCKED by BTC.D=58% (hard filter)

Upload your real `signals.json` to replace demos.
