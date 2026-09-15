# LINK — Cross-Market Correlation Agent

> When markets move together, LINK finds it.

LINK is a quantitative cross-market research and trading workflow designed to detect unusual changes in relationships between crypto, tokenized stocks, equities, and other market instruments.

Instead of simply displaying correlation values, LINK continuously analyzes historical relationships, identifies statistically unusual divergences, generates structured trading hypotheses, validates them through backtesting, applies risk controls, and supports paper trading.

## The Problem

Cross-market relationships can contain useful information.

BTC may historically move with technology equities. Crypto assets may develop relationships with tokenized stocks. Gold, USD, oil, and other macro assets can also exhibit changing relationships with risk assets.

The problem is that most trading workflows stop at charts or basic correlation indicators.

A trader still has to:

1. Find relevant asset pairs.
2. Measure historical relationships.
3. Detect unusual changes.
4. Decide whether the change is statistically meaningful.
5. Formulate a strategy.
6. Backtest it.
7. Evaluate risk.
8. Monitor the resulting position.

LINK combines this process into a single workflow.

## Core Workflow

```text
MARKET DATA
     ↓
CORRELATION ENGINE
     ↓
REGIME DETECTION
     ↓
ANOMALY DETECTION
     ↓
AI INTERPRETATION
     ↓
STRATEGY GENERATION
     ↓
BACKTEST
     ↓
RISK CHECK
     ↓
PAPER TRADE
     ↓
DECISION JOURNAL
```

## How LINK Works

### 1. Measure Relationships

LINK calculates relationships between selected assets using rolling correlation analysis.

Example:

```text
BTC ↔ NASDAQ

Historical Correlation: 0.72
Current Correlation:    0.18
Deviation:             -0.54
Z-Score:               -2.7σ
```

The system does not treat correlation as causation. Instead, it identifies when the current relationship differs materially from its historical behavior.

### 2. Detect Correlation Breaks

LINK compares current rolling correlation against a historical baseline.

Possible relationship states include:

```text
STABLE
STRENGTHENING
WEAKENING
INVERTING
DIVERGENCE
BREAKOUT
```

Large statistical deviations are ranked as potential anomalies.

### 3. Discover Opportunities

LINK scans the configured market universe and ranks unusual relationships.

Example:

```text
3 ANOMALIES FOUND

BTC / NASDAQ
Deviation: -2.7σ

ETH / TECHNOLOGY
Deviation: -2.2σ

SOL / GROWTH
Deviation: +3.1σ
```

### 4. Generate Strategies

Users can describe a research idea in natural language.

Example:

```text
"Find a strategy where BTC and Nasdaq diverge."
```

LINK converts the request into structured strategy rules.

```text
ASSET A: BTC
ASSET B: NASDAQ

LOOKBACK: 30D

ENTRY:
|Z| > 2.0

EXIT:
|Z| < 0.5

STOP:
|Z| > 3.0

STRATEGY:
MEAN REVERSION
```

### 5. Backtest

The strategy is tested on historical data using deterministic calculations.

LINK calculates:

```text
Total Return
Annualized Return
Sharpe Ratio
Sortino Ratio
Maximum Drawdown
Win Rate
Profit Factor
Trade Count
Turnover
Rolling 30D Sharpe
Out-of-Sample Sharpe Decay
```

The backtest can also include:

```text
Transaction Fees
Slippage
Funding / Carrying Costs
```

The system is designed to avoid look-ahead bias by processing historical data chronologically.

### 6. Risk Check

Before a strategy moves into paper trading, LINK evaluates:

```text
Drawdown
Position Concentration
Sample Size
Relationship Stability
Liquidity Assumptions
Execution Costs
```

The result can be:

```text
PASS
CONDITIONAL
BLOCKED
```

### 7. Paper Trading

LINK supports simulated execution so strategies can be monitored without using real funds.

Every simulated trade is recorded with:

```text
Timestamp
Instrument
Direction
Entry Price
Exit Price
Quantity
Balance Before
Balance After
P&L
Strategy
Signal
Status
```

## AI Layer

AI is used as the research and strategy-construction layer.

The LLM can:

* Interpret natural-language research requests.
* Select relevant market relationships.
* Explain detected anomalies.
* Convert trading ideas into structured strategy parameters.
* Generate strategy hypotheses.
* Summarize quantitative results.
* Orchestrate the research workflow.

The LLM does not calculate financial metrics directly.

Deterministic code is responsible for:

```text
Correlation
Rolling Correlation
Z-Score
Returns
Hedge Ratio
P&L
Sharpe
Sortino
Drawdown
Backtest Results
Risk Calculations
```

This separation improves reproducibility and reduces unsupported AI-generated financial calculations.

## Supported Strategy Concepts

LINK is designed to support several cross-market research approaches:

### Correlation Mean Reversion

Investigate whether an unusually large relationship deviation returns toward its historical range.

### Relationship Breakout

Investigate whether a newly broken relationship continues into a new regime.

### Relative Divergence

Compare normalized performance between two assets.

### Cross-Asset Rotation

Use changes in cross-market relationships as an allocation signal.

## Example Research Flow

```text
USER

"Find unusual relationships between crypto
and tokenized stocks."

        ↓

MARKET SCAN

        ↓

BTC / TOKENIZED EQUITY
Z-SCORE: -2.7σ

        ↓

ANOMALY ANALYSIS

Current Correlation: 0.18
Historical Baseline: 0.72

        ↓

STRATEGY

Mean Reversion

        ↓

BACKTEST

Historical + Out-of-Sample Validation

        ↓

RISK CHECK

CONDITIONAL PASS

        ↓

PAPER TRADE

        ↓

DECISION JOURNAL
```

## Architecture

LINK separates the quantitative engine, AI layer, market-data layer, and user interface.

```text
UI
│
├── Dashboard
├── Correlation Lab
├── Anomalies
├── Strategy Builder
├── Backtest
├── Risk
├── Paper Trading
└── Journal
        │
        ↓
Application Services
        │
        ├── Market Data
        ├── AI / LLM
        └── Persistence
        │
        ↓
Quantitative Engine
        │
        ├── Correlation
        ├── Regime Detection
        ├── Anomaly Detection
        ├── Strategy Engine
        ├── Backtest Engine
        └── Risk Engine
```

## Project Structure

```text
src/
├── components/
├── features/
├── services/
├── engine/
│   ├── correlation/
│   ├── regime/
│   ├── anomaly/
│   ├── strategy/
│   ├── backtest/
│   ├── risk/
│   └── paper-trading/
├── data/
├── hooks/
├── types/
├── lib/
└── app/
```

Adapt this structure to the actual repository implementation.

## Demo Mode

LINK includes a deterministic demo environment for reproducible demonstrations.

Demo mode can simulate cross-market relationships between assets such as:

```text
BTC
ETH
SOL
NASDAQ
Technology Equities
Gold
USD
```

The demo dataset is designed to demonstrate:

```text
NORMAL RELATIONSHIP
        ↓
CORRELATION BREAK
        ↓
ANOMALY DETECTION
        ↓
STRATEGY GENERATION
        ↓
BACKTEST
        ↓
PAPER TRADE
```

Demo data is clearly labeled and is not presented as live market data.

## Validation

LINK is designed for quantitative validation rather than cosmetic performance claims.

The Alpha Factory validation workflow uses:

```text
Historical Period: ≥ 60 Days
Out-of-Sample Period: ≥ 30 Days
```

Results should be reproducible from the submitted backtest code and dataset.

Performance figures shown in the application must be classified as:

```text
OBSERVED
ESTIMATED
TARGETED
```

No historical performance should be fabricated.

## Risk and Safety

LINK defaults to paper trading.

It does not automatically execute live trades.

The project does not present correlation as guaranteed predictive power and does not claim that backtested performance guarantees future results.

All simulated trades are explicitly marked as paper trades.

## Bitget Hackathon

LINK is developed for the **Bitget AI × Crypto Hackathon S2**.

Competition Track:

```text
Alpha Factory
```

Competition Sub-theme:

```text
Cross-Market Correlation Strategies
```

The project focuses on identifying cross-market correlation shifts and transforming statistically significant divergences into testable trading strategies.

## Technology

Update this section with the exact technologies used in the final implementation.

Example:

```text
Frontend:
Next.js
React
TypeScript
Tailwind CSS

Charts:
[ACTUAL LIBRARY]

AI:
[ACTUAL MODEL / API]

Market Data:
[ACTUAL PROVIDER / BITGET API]

Persistence:
[ACTUAL DATABASE / STORAGE]

Deployment:
[ACTUAL PLATFORM]
```

## Project Status

```text
Prototype / Hackathon Build
```

Current capabilities include:

```text
✓ Correlation Analysis
✓ Correlation Matrix
✓ Correlation Break Detection
✓ Anomaly Detection
✓ AI Strategy Generation
✓ Backtesting
✓ Risk Checks
✓ Paper Trading
✓ Trade Logging
✓ Decision Journal
✓ Responsive Swiss-style UI
```

## Important Note

LINK is a research and paper-trading prototype.

Backtest results are historical simulations and should not be interpreted as guarantees of future performance.

Market relationships can change, correlations can fail, and strategies can lose money.

## License

[ADD LICENSE]
