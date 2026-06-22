# TSMC Global Facility Network Design

This project uses a facility-network-design optimization model to study how TSMC could structure its advanced-node manufacturing footprint. Given a set of candidate fab locations and regional demand, the model chooses which fabs to open and how to route production so that total cost is minimized. Total cost combines four pieces: fixed facility investment, production, transportation, and a penalty for any demand left unfilled.

The analysis focuses on three leading-edge process nodes (roughly 2/3nm, 5nm, and 7nm), which make up the large majority of TSMC's wafer revenue. Demand is spread across six global hubs (Silicon Valley, Austin, Shenzhen, Seoul, Munich, and Tokyo), and production can be placed at six candidate sites (Hsinchu, Tainan, Kaohsiung, Arizona, Taichung, and Japan). The optimization runs as a linear program in Excel Solver.

A full write-up with all data sources, assumptions, and the complete model formulation lives in the executive summary PDF in this repository.

## What the model decides

The optimizer ended up concentrating production in Taiwan, opening Hsinchu, Tainan, and Taichung while leaving Kaohsiung, Arizona, and Japan closed under the baseline assumptions.

| Facility | Decision |
| --- | --- |
| Hsinchu | Open |
| Tainan | Open |
| Taichung | Open |
| Kaohsiung | Closed |
| Arizona | Closed |
| Japan | Closed |

## Headline numbers

| Metric | Value |
| --- | --- |
| Total demand | 12,580 units |
| Available capacity | 7,920 units |
| Unmet demand | ~7,180 units (about 57%) |
| Fixed facility cost | $36.0B |
| Production + transportation | $70.9B |
| Unmet-demand penalty | $215.4B |
| Total cost | $322.3B |

## Takeaways

The biggest story is capacity, not shipping. Because available capacity falls well short of demand, the unmet-demand penalty dominates total cost — far outweighing production and freight combined. That points to building advanced-node capacity as the highest-leverage move, rather than fine-tuning logistics.

Facility economics also outweigh location convenience. Arizona sits closer to North American customers but carries a much higher fixed cost, so the model passes on it; the freight savings simply aren't enough to justify the extra investment. Japan stands out as a sensible future option given how much demand goes unserved. Sensitivity testing on the shortage penalty (e.g. raising it from $30M to $50M per 1,000 wafers) left the open/close decisions unchanged, suggesting the chosen network is fairly robust.

## Possible extensions

The current model is a single-period snapshot. Natural next steps include multi-period capacity expansion, demand scenarios for different market conditions, technology migration between nodes, geopolitical and currency risk, customer-priority service levels, and ESG/resource constraints. These are discussed in more detail in the summary.

## Where to find the model

You can find and download the model and all supporting materials within this project — just browse the file list at the top of the repository. The Excel file contains the full Solver setup and all cost/capacity inputs, the 3-page executive summary PDF gives the complete narrative, methodology, and sources, and the working-data file holds the supporting tables and intermediate findings. Click any file in the project to open or download it.

## Sources

Key inputs were estimated from public information, including TSMC's reported fab capacity and its 1Q26 investor presentation, plus published references on semiconductor wafer costs and air-freight rates.
