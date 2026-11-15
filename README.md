# 🚗 Smart Car Rental Reservation & Dynamic Pricing Optimization

A Python-based revenue optimization engine that models a dynamic car rental pricing system and solves the reservation scheduling problem using **Weighted Interval Scheduling (Dynamic Programming)** benchmarked against a **Greedy (Earliest Finish Time)** baseline.

## 🚀 Key Features
- **Dynamic Pricing Engine:** Calculates net rental revenue using vehicle segment multipliers (`Economy`: 1.0x, `Comfort`: 1.5x, `Luxury`: 2.5x), long-term rental discounts (10% off for 5+ days), and peak demand surcharges (+20% between Days 3–7).
- **Data Validation & Edge Case Handling:** Parses `DD.MM.YYYY` date strings into relative integer day offsets and filters invalid date ranges or non-positive base rates using `Pandas`.
- **Algorithm Comparison:**
  - **Greedy Algorithm ($O(n \log n)$):** Selects earliest-ending requests; fast but prone to local optima.
  - **Original Dynamic Programming ($O(n \log n)$):** Uses binary search (`get_latest_non_overlapping`) and list copying to guarantee the global revenue optimum.
  - **Optimized Dynamic Programming ($O(n \log n)$):** Replaces list copying during state transitions with `previous` and `take` pointer arrays for backward path reconstruction, achieving a **~5.7x runtime speedup** at $N = 10,000$ requests.
- **Interactive & Benchmark Modes:** Supports both live manual CLI entry and automated 10,000-request scalability benchmarking with `Matplotlib` visualizations.

## 🛠️ Tech Stack
- **Language:** Python 3
- **Libraries:** `NumPy`, `Pandas`, `Matplotlib`, `Graphviz`

## 📊 Usage
1. Install dependencies:
   ```bash
   pip install numpy pandas matplotlib graphviz
