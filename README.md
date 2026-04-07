# Algorithmic Market Structure Tracker (MTF)

A high-performance algorithmic trading indicator built in Pine Script™ v5. This tool provides quantitative detection of market structure shifts (BOS), dynamic generation of high-probability entry zones, and a multi-timeframe (MTF) bias alignment engine.

Designed for traders and developers who require systematic, mathematically defined market mapping rather than subjective chart drawing.

## Core Features

* **Algorithmic Structure Detection:** Mathematically identifies true swing highs and lows based on strict consecutive retracement logic, eliminating false signals.
* **Dynamic Zone Generation (TJL 2 A+):** Automatically calculates pending, tapped, and breached entry zones based on the last valid pullback prior to a Break of Structure. Zone height is dynamically sized using wick and body percentages.
* **Multi-Timeframe Alignment Engine:** Aggregates rolling trend bias across 5M, 15M, 1H, 4H, and 1D timeframes. 
* **Live Dashboard:** On-chart HUD displaying real-time MTF alignment, active zone coordinates, and exact status tracking.
* **Webhook-Ready Automation:** Native alert conditions for zone approaches (distance calculated in pips) and multi-timeframe confirmation signals, ready to be routed to trading bots.

## Installation

1. Navigate to [TradingView](https://www.tradingview.com/).
2. Open the **Pine Editor** tab at the bottom of your chart.
3. Open the `src/tjl_tracker_v2.pine` file from this repository and copy the source code.
4. Paste the code into the Pine Editor.
5. Click **Add to Chart**.

## Technical Architecture & Logic

### Retracement Validation
The script does not rely on simple fractal logic. A swing high is only confirmed after a strict bearish retracement (two consecutive down candles where the second closes below the first's low). This ensures zones are only drawn on structurally significant pivots.

### Zone State Machine
Zones operate on a 3-state system, visually updating in real-time:
* **Pending (Fresh):** Box extends forward; price has not yet interacted with the zone parameters.
* **Tapped:** Price wicks into the calculated bounds. Box freezes its right edge.
* **Breached:** Price closes entirely through the opposite bound of the zone, invalidating the setup.

## Configuration Parameters

| Parameter Group | Description |
| :--- | :--- |
| **Structure Lookback** | Adjust the search period for extreme highs/lows prior to retracement validation. |
| **Zone Body %** | Fine-tune the structural depth of the entry zones (calculates Wick + X% of the candle body). |
| **Alert Distance** | Define the exact pip proximity required to trigger pre-emptive webhook alerts. |

## License

This project is licensed under the [Mozilla Public License 2.0](https://www.mozilla.org/en-US/MPL/2.0/).

## Contributing

Pull requests are welcome. For major changes (such as adding new zone variations or integrating volume-weighted confirmation), please open an issue first to discuss the proposed logic changes.
