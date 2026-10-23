# Bank Customer Segmentation — DWDM Analytics

A responsive local analytics dashboard for customer-level banking data. The Node.js backend serves the dashboard and computes dataset summaries, warehouse-based OLAP operations, pivots, and association rules.

## Start locally

1. Install Node.js 18 or newer.
2. From this project folder, run `node backend/server.js` (or double-click `start.bat`).
3. Open the localhost URL printed by the server. It tries port 8000 first and advances automatically if that port is occupied.

Open the dashboard through the localhost URL. Opening `frontend/index.html` as a `file://` page displays a startup instruction because browser file pages cannot call local APIs. No npm packages, external database, or API key are required.

## Data

- `data/bank_customer_segmentation_20000_clean.csv`: 20,000 customer rows × 21 actual headers. This is the customer-level analytical dataset.
- `data/bank_transactions.csv.zip`: the original source, 1,048,567 transaction rows × 9 fields. It is processed by the backend and never loaded into the browser.
- `data/etl_metadata.json`: raw-source date coverage and last transaction date for each of the 20,000 matching analytical customers.
- `data/project_outputs.json`: established project results and model evaluation outputs.
- `frontend/assets/project/`: evaluation figures used in the dashboard.

The delivered cleaned CSV has 21 actual headers, which is the count shown in the dashboard.

## Results and limitations

Benchmark scores, confusion matrices, ROC results, permutation-importance plots, K-selection charts, PCA, and cluster-profile visuals are recorded project outputs, not results newly trained by this application. Random Forest benchmark metrics are exact. Values estimated from unlabeled model-comparison and feature-importance chart bars are marked approximate. No fitted customer-level model or probability artifact was supplied; customer lookup therefore shows the recorded analytical target label instead of claiming a new prediction.

OLAP aggregations and association rules are calculated from the analytical CSV and source-derived date metadata. Product ownership, Product Fit, and Next Product Uptake are derived customer-level attributes, not fields from the raw transaction file. Association rules indicate co-occurrence, not causation.

## Structure

- `backend/server.js` — API, CSV loading, summaries, OLAP, association rules, static files
- `frontend/` — responsive pages, SVG charts, interactions, styles, and figures
- `data/` — datasets and analytical outputs
