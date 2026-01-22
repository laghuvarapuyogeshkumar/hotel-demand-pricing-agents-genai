# Hotel Room Demand & Pricing Intelligence (AI Agents + GenAI)

## Objective
Build a demand and pricing intelligence solution using the Kaggle Hotel Booking Demand dataset.  
Focus: Multi-agent design + GenAI explanations (business language), not model complexity.

## Dataset
Hotel Booking Demand (Kaggle): City Hotel + Resort Hotel bookings (2015–2017)

## Agent Architecture
### 1) DataPrepAgent
- Loads raw CSV
- Cleans missing values
- Creates features: arrival_date, stay_nights, adj_room_nights
- Handles ADR outliers
- Outputs: `data/curated_bookings.parquet`, `outputs/data_quality.json`

### 2) DemandAgent
- Computes demand per arrival_date and hotel
- Creates rolling demand index (28-day rolling median)
- Output: `outputs/demand_by_date.csv`

### 3) PricingAgent
- Calculates baseline ADR (median ADR per hotel)
- Adjusts ADR using demand index with safe caps
- Output: `outputs/price_recommendations.csv`

### 4) ExplainAgent (GenAI-style)
- Converts numeric recommendations into business explanations
- Output: `outputs/genai_explanations.md`

### 5) OrchestratorAgent
- Runs all agents end-to-end
- Output: `outputs/run_log.json`

## Outputs
- `outputs/demand_by_date.csv`
- `outputs/price_recommendations.csv`
- `outputs/genai_explanations.md`
- `outputs/data_quality.json`
- `outputs/run_log.json`

## How to Run (Google Colab)
1. Upload `kaggle.json` (Kaggle API token) in Colab Files panel
2. Run the notebook top-to-bottom
3. Review outputs in `/outputs`

## Sample GenAI Explanation
Example from `outputs/genai_explanations.md`:

- **2015-07-08 | City Hotel**: Recommended ADR = **$124.88** (baseline **$99.90**). Demand index = **2.92**, so price is **adjusted higher** due to increased booking pressure.

## Notes
- Raw/curated datasets are not committed to GitHub (kept local/Colab).

--yogesh---

