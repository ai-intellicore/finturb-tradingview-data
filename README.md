# FinTurb TradingView Data Feed

Daily composite risk score and regime classification for the
[FinTurb Risk Regime Overlay](https://www.finturb.com/mcp-access)
TradingView indicator.

## Data format

`data/FINTURB_REGIME/1D.csv` — daily OHLCV-convention:

| Column | Carries | Range |
|---|---|---|
| `time` | Unix timestamp | — |
| `open` | Composite risk score | 0–100 |
| `high` | Liquidity-adjusted 4-way score | 0–100 |
| `low` | Absorption Ratio percentile × 100 | 0–100 |
| `close` | Mahalanobis Distance percentile × 100 | 0–100 |
| `volume` | Regime code | 1=Normal, 2=Elevated, 3=Stress, 4=Crisis |

Updated daily at ~04:20 UTC by an automated pipeline.

History begins 2015-02-27.

## Usage in Pine Script

```pine
//@version=5
data = request.seed("ai-intellicore/finturb-tradingview-data", "FINTURB_REGIME", input.timeframe("1D"))
risk_score = data[0]   // open = composite risk score
regime_code = data[5]  // volume = regime (1-4)
```

## About

Produced by [AI IntelliCore Limited](https://www.finturb.com).
Not investment advice. See [full terms](https://www.finturb.com/terms).

© 2026 AI IntelliCore Limited.
