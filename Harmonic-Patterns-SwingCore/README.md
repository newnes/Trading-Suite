# Harmonic Patterns SwingCore — Harmonic pattern detector for MetaTrader 5

A technical-analysis tool for detecting and visualizing harmonic patterns on the chart, with Fibonacci level projection and a configurable alert system.

---

## What this indicator is

It is a **visual analysis tool**. Its job is to identify structures on the chart that satisfy the geometric relationships of six classic harmonic patterns — Gartley, Bat, Butterfly, Crab, Cypher, and Shark — in both bullish and bearish variants, and to display them clearly along with their projection levels.

The indicator draws the pattern legs, labels the completion point, projects Fibonacci retracement and extension levels from the most recent pattern, and can raise a terminal alert when a new one is detected.

## What this indicator is NOT

- **It is not an automated trading system.** It does not open, close, or manage positions.
- **It does not generate buy or sell signals.** It displays geometric structures; interpretation and any decision rest entirely with the user.
- **It does not predict price.** Fibonacci levels are geometric projection references, not forecasts.
- **It does not guarantee that a detected pattern will resolve in any particular way.** A harmonic pattern is a technical-analysis figure, and its appearance does not imply an outcome.

---

## The real problem: detecting the structure, not measuring the pattern

It is worth being transparent about where the real technical difficulty of this kind of indicator lies.

Measuring a harmonic pattern — checking whether the proportions between its legs are close to the Fibonacci ratios — is, at bottom, straightforward arithmetic. That is **not** the hard part.

The hard part, and where most detectors fail, is the step before it: **identifying what is a genuinely relevant peak and valley in real time**, especially on low timeframes such as M1, where price noise is considerable.

Here there is no single, objective answer. Detecting significant highs and lows depends on several parameters (sensitivity, observation window, minimum prominence, separation between extremes) and can be approached with different mathematical models, each with its own trade-offs:

- If the detector is **too sensitive**, it marks noise as if it were real turning points and produces spurious patterns.
- If it is **too coarse**, it misses valid structures.

The central question — *how much smoothing is enough and how much is too much* — has no universally correct solution. It is an inherently subjective problem, and any honest detector is really a position taken on that balance.

## The approach behind this indicator

This indicator addresses that difficulty with an **empirical and alternative** method of identifying price structure: empirical because its configuration is derived from observation on real data, and alternative because it is one of several possible paths to solve a problem that, as explained, admits no single solution.

Building it required integrating several disciplines:

- **Signal processing**, to treat the price series before searching for extremes and reduce the impact of noise.
- **Analytic geometry**, since each pattern is a set of spatial relationships between five points.
- **Proportions and metric relationships** (the Fibonacci ratios) as the validation criterion between legs.
- **Combinatorial validation logic**: strict peak-valley alternation, and verification of the geometric inequalities specific to each pattern.

The result is a pipeline that first resolves the swing structure and only then applies pattern measurement on that already-refined structure.

---

## Brief historical context

Harmonic patterns have a long tradition in technical analysis. Their origin is usually traced to the work of H. M. Gartley (1935), and they were later formalized with Fibonacci proportions by subsequent authors, among them Scott Carney, who systematized several of the patterns now considered standard (such as the Bat, Crab, and Shark). The technique, therefore, has decades of history.

What has changed in recent years is the attempt to automate this reading on low timeframes, where — as described above — reliable detection of price structure becomes the true bottleneck.

---

## Features

- Detection of 6 harmonic patterns (Gartley, Bat, Butterfly, Crab, Cypher, Shark), bullish and bearish.
- Drawing of the pattern legs and a label at the completion point.
- Projection of Fibonacci levels (retracements and extensions) for the most recent pattern.
- Two selectable validation methods: classic ratios or geometric rules.
- Terminal alert system, with a configurable number of repetitions.
- Visualization of the swing structure on the chart.

## Main parameters

- Enable/disable pattern detection and validation method.
- Ratio tolerance.
- Scan window (number of bars back).
- Structure-detection parameters (prominence, separation between extremes).
- Show/hide percentages, horizontal lines, and Fibonacci levels.
- Alert configuration (enable and number of repetitions).

> *Shark pattern uses X-A-B-C-D notation instead of O-X-A-B-C.*

---

## Versions

- **Lite (free):** classic method, single most-recent pattern locked per session.
- **Pro (paid):** all 6 patterns, geometric engine, direct and inverse Fibonacci targets, alerts.

---

## Disclaimer

This indicator is provided **for informational and demonstrative purposes only**, as a technical-analysis support tool.

It does not constitute financial or investment advice, nor any trading recommendation. Pattern detection is the result of a geometric calculation and does not represent a prediction of future market behavior.

Past performance does not guarantee future results. Trading financial markets carries a high risk of loss.

**You assume the entire risk of any decision you make based on this indicator.** The author is not responsible for any losses, damages, or harm of any kind resulting from its use.
