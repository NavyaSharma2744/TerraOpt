# Sales Territory & Rep Effectiveness Optimization

An end-to-end decision analytics project that diagnoses underperforming sales territories/reps, predicts expected sales given activity levels, and prescribes a resource (call/budget) reallocation strategy with a quantified revenue impact.


## Problem Statement

A company (pharma/FMCG/retail) allocates a fixed sales force budget (rep calls, visits, marketing spend) across territories and customer segments. Not all territories respond equally to this effort. The business question:

> Given historical activity and sales data, which territories/reps are over- or under-resourced, and how should we reallocate effort to maximize total revenue?

## Objectives

1. Segment territories/customers by potential and current performance.
2. Quantify the relationship between sales activity (calls, spend) and sales outcomes (promotion response).
3. Build a predictive model of expected sales given activity level.
4. Flag reps/territories performing above or below their expected sales.
5. Recommend a reallocation of effort across territories, with an estimated revenue uplift.
6. Present findings in a stakeholder-facing dashboard.

## Tech Stack

- **Language**: Python (pandas, numpy, scikit-learn, xgboost)
- **Visualization**: matplotlib/seaborn for analysis, Power BI or Streamlit for the final dashboard
- **Notebook**: Jupyter for exploratory work
- **Optional**: SQL for data querying if using a relational data source

## Project Structure

```
sales-territory-optimization/
├── data/
│   ├── raw/                # original/simulated dataset
│   └── processed/          # cleaned data used for modeling
├── notebooks/
│   ├── 01_eda.ipynb
│   ├── 02_segmentation.ipynb
│   ├── 03_response_modeling.ipynb
│   └── 04_prescriptive_reallocation.ipynb
├── src/
│   ├── data_prep.py
│   ├── segmentation.py
│   ├── model.py
│   └── reallocation.py
├── dashboard/
│   └── app.py               # Streamlit app (or .pbix for Power BI)
├── reports/
│   └── final_recommendation.pdf
├── README.md
└── project_plan.md
```

## Dataset

Use a public pharma/FMCG sales dataset (e.g., Kaggle "Pharma Sales Data" or "FMCG Sales & Distribution") or simulate one with fields such as:

`rep_id, territory_id, product, month, calls_made, hcp_segment (high/medium/low potential), budget_spent, sales_units, sales_revenue`

If simulating, generate 12–24 months of data across ~20–30 territories so trends and seasonality are visible.

## Methodology Summary

| Stage | What it answers | Technique |
|---|---|---|
| EDA | What does the data look like, where are the gaps/outliers | pandas, seaborn |
| Segmentation | Which territories are high/medium/low potential | K-means / RFM-style scoring |
| Response modeling | How much does an extra call/₹ of spend move sales | Regression (log-log or marginal response curve) |
| Predictive model | What sales should we expect given activity | XGBoost / Random Forest regression |
| Prescriptive layer | Where should effort be reallocated | Constrained optimization on model output (e.g., linear programming or simple rule-based reallocation under a fixed budget) |
| Dashboard | How does a stakeholder consume this | Streamlit / Power BI |

## Key Deliverable

A recommendation such as: *"Reallocating 15% of call volume from low-response Tier-3 territories to high-response Tier-1 territories is projected to increase quarterly revenue by ~X%, with no increase in total budget."*

## How to Run

```bash
git clone <repo-url>
cd sales-territory-optimization
pip install -r requirements.txt
jupyter notebook notebooks/01_eda.ipynb
```

To launch the dashboard:
```bash
streamlit run dashboard/app.py
```

## Results (fill in after completion)

- Model performance (R² / RMSE on hold-out set)
- Number of territories flagged as under/over-resourced
- Projected revenue uplift from reallocation

## Future Scope
    - An LLM-powered "insight summarizer" that takes your model outputs (which territories are under/over-resourced, projected uplift) and auto-generates a plain-English executive summary or Q&A interface ("ask questions about the recommendation in natural language") inside Streamlit dashboard


## Author

[Your Name] — built as a portfolio project for Decision Analytics roles.
