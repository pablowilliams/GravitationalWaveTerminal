# GravitationalWaveTerminal

Terminal-style chirp-mass posterior Monte Carlo dashboard for LIGO-Virgo-KAGRA gravitational-wave events, with Q-transform spectrograms, 4D posterior corner plots, and PE-pipeline sentiment.

## Features

- **Monte Carlo simulation** — Geometric Brownian Motion engine, configurable paths (100 / 1k / 10k) and horizons (5 / 30 / 90 / 252 periods).
- **Event watchlist** — 12 events (GW150914, GW170817, GW190521, GW200115, GW230529…).
- **Live tick simulation** — synthetic ticks every few seconds with deterministic seed for reproducibility.
- **Strategy signals** — DETECTION / GLITCH / MARGINAL derived from SNR MA Cross, FAR MR, Pipeline Momentum, Tail Skew, Collaboration Notes.
- **GWT chatter panel** — positive / neutral / negative sentiment with sample posts per event.
- **Event KPIs** — aggregate value, P&L, expected return, 95% VaR, Sharpe, sentiment.
- **Custom panel** — domain-specific panel.
- **Accessible by default** — WCAG 2.2 AA: keyboard nav, ARIA live regions, screen-reader chart alternatives, 4.5:1 contrast in dark mode.

## Running

No build step. Live at https://pablowilliams.github.io/GravitationalWaveTerminal/.

For local development, any static server works:

```bash
python3 -m http.server 8000
# then visit http://localhost:8000
```

## Data pipeline

The dashboard reads `data/quotes.json` on load and on each tick. A scheduled GitHub Action (`.github/workflows/refresh-data.yml`) regenerates synthetic close histories every hour so the visible data evolves. Replace the generator with a real data source to go live.

## Architecture

- `index.html` — semantic layout, landmarks, headings
- `app.js` — data, Monte Carlo engine, sentiment, signal logic, rendering
- `styles.css` — dark terminal theme with AA-contrast tokens

## License

Private. All rights reserved.
