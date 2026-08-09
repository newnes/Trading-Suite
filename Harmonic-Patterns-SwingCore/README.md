# Harmonic Patterns SwingCore — Harmonic Pattern Detector for MetaTrader 5

A technical-analysis tool for detecting and visualizing harmonic patterns on the chart, with Fibonacci level projection and a configurable alert system.

---

## Table of Contents

- [What This Indicator Is](#-what-this-indicator-is)
- [What This Indicator Is NOT](#-what-this-indicator-is-not)
- [The Real Problem](#-the-real-problem)
- [The Approach Behind This Indicator](#-the-approach-behind-this-indicator)
- [Brief Historical Context](#-brief-historical-context)
- [Pattern Reference Table](#-pattern-reference-table)
- [Pattern Structure](#-pattern-structure)
- [Features](#-features)
- [Technical Features](#-technical-features)
- [Alert System](#-alert-system-5-channels)
- [Main Parameters](#-main-parameters)
- [Installation](#-installation)
- [Versions](#-versions)
- [Disclaimer](#-disclaimer)
- [Contact](#-contact)

---

## What This Indicator Is

It is a **visual analysis tool**. Its job is to identify structures on the chart that satisfy the geometric relationships of six classic harmonic patterns — **Gartley, Bat, Butterfly, Crab, Cypher, and Shark** — in both bullish and bearish variants, and to display them clearly along with their projection levels.

The indicator draws the pattern legs, labels the completion point, projects Fibonacci retracement and extension levels from the most recent pattern, and can raise a terminal alert when a new one is detected.

---

## What This Indicator Is NOT

| **NOT** | Explanation |
|---------|-------------|
| ❌ **Automated Trading System** | Does not open, close, or manage positions |
| ❌ **Buy/Sell Signal Generator** | Displays geometric structures; interpretation and decisions rest entirely with the user |
| ❌ **Price Predictor** | Fibonacci levels are geometric projection references, not forecasts |
| ❌ **Guaranteed Outcome** | A harmonic pattern is a technical-analysis figure; its appearance does not imply a particular resolution |

> **⚠️ Important:** This indicator is a **support tool**, not a decision-making system. The user retains full responsibility for all trading decisions.

---

## The Real Problem

It is worth being transparent about where the real technical difficulty of this kind of indicator lies.

### The Easy Part: Measuring the Pattern

Measuring a harmonic pattern — checking whether the proportions between its legs are close to the Fibonacci ratios — is, at bottom, **straightforward arithmetic**. That is **not** the hard part.

### The Hard Part: Identifying Relevant Peaks and Valleys

The hard part, and where most detectors fail, is the step before it: **identifying what is a genuinely relevant peak and valley in real time**, especially on low timeframes such as M1, where price noise is considerable.

> **Here there is no single, objective answer.**

Detecting significant highs and lows depends on several parameters:

| Parameter | Impact |
|-----------|--------|
| **Sensitivity** | How easily a point is considered a turning point |
| **Observation Window** | How many bars are analyzed |
| **Minimum Prominence** | How significant a move must be |
| **Separation Between Extremes** | Minimum distance between consecutive highs/lows |

### The Trade-off:

| If the detector is... | Problem |
|----------------------|---------|
| **Too sensitive** | Marks noise as real turning points → produces **spurious patterns** |
| **Too coarse** | Misses valid structures → **false negatives** |

> **The central question** — *how much smoothing is enough and how much is too much* — has no universally correct solution. It is an inherently **subjective problem**, and any honest detector is really a position taken on that balance.

---

## The Approach Behind This Indicator

This indicator addresses that difficulty with an **empirical and alternative** method of identifying price structure:

| Aspect | Description |
|--------|-------------|
| **Empirical** | Configuration derived from observation on real data |
| **Alternative** | One of several possible paths to solve a problem that admits no single solution |

### Disciplines Integrated:

| Discipline | Application |
|------------|-------------|
| **Signal Processing** | Treating the price series before searching for extremes to reduce noise impact (Savitzky-Golay 7/3) |
| **Analytic Geometry** | Each pattern is a set of spatial relationships between five points |
| **Metric Relationships** | Fibonacci ratios as validation criteria between legs |
| **Combinatorial Logic** | Strict peak-valley alternation and pattern-specific geometric inequalities |

> **Result:** A pipeline that first resolves the swing structure and only then applies pattern measurement on that already-refined structure.

---

## Brief Historical Context

Harmonic patterns have a long tradition in technical analysis:

| Era | Development |
|-----|-------------|
| **1935** | H. M. Gartley publishes his work describing the original figure |
| **Late 20th Century** | Fibonacci proportions formalized by subsequent authors |
| **Early 21st Century** | Scott Carney systematizes patterns (Bat, Crab, Shark) |
| **Present** | Automation attempts on low timeframes |

> **The technique has decades of history.** What has changed recently is the attempt to automate this reading on low timeframes, where reliable detection of price structure becomes the true bottleneck.

---

## Pattern Reference Table

| Pattern | AB/XA | XD/XA | Characteristic |
|---------|-------|-------|----------------|
| **GARTLEY** | 61.8% | 78.6% | Classic, moderate retracement |
| **BAT** | 38.2-50% | 88.6% | Deep retracement at D |
| **BUTTERFLY** | 78.6% | 127.2-161.8% | Extreme extension |
| **CRAB** | 38.2-61.8% | 161.8% | Maximum extension |
| **CYPHER** | BC/XA: 1.13-1.414 | CD/XC: 78.6% | C > A (C surpasses A) |
| **SHARK** | XD/XA: 88.6% | CD/BC: 1.13-1.618 | D <= X (Bull) / D >= X (Bear) |

**Note:** The **Shark** pattern uses **X-A-B-C-D** notation instead of O-X-A-B-C, as used in other implementations.

---

## Pattern Structure

### Bullish Pattern (X=Valley):
