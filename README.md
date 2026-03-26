📊 A/B Clients RCA Dashboard
A real-time performance analytics dashboard that compares Shopify vs Tectonic metrics across multiple D2C e-commerce clients. Built to automate Root Cause Analysis (RCA) and A/B experiment reporting.

🚀 Features

Multi-client support — Switch between 13+ D2C brand dashboards from a single interface
Summary Tab — Side-by-side Shopify vs Tectonic metrics with delta analysis and executive summary
Landing Page Analysis — Top pages ranked by sessions, with per-page conversion, ATC, RPS, AOV comparison
UTM Source Breakdown — Traffic and conversion performance by UTM source
Hourly Trends — Hour-by-hour performance charts for intraday analysis
Daily Performance Trends — Bar/line toggle charts with period totals
Exclude Landing Pages — LIKE-pattern based LP exclusions saved to browser storage
Time Period Filters — Today, Yesterday, Last 7 Days, Last 30 Days
Executive Summary — Auto-generated verdict on Tectonic vs Shopify performance


🛠️ Tech Stack
LayerToolsData StorageClickHouseData ProcessingPython, Pandas, NumPyFrontendHTML, CSS, JavaScript, Chart.jsData SourceShopify Analytics CSV + ClickHouse queriesNotebookJupyter Notebook

📁 Project Structure
rca-dashboard/
├── RCA_Dashboard_v8_COMPLETE.ipynb   # Main notebook
├── config/
│   ├── clients_config.json           # Client display names, CSV paths, currency
│   └── queries.py                    # ClickHouse SQL queries per client
├── credentials/
│   └── clickhouse_secret.json        # ClickHouse connection details (not committed)
├── data/
│   └── <client>/
│       └── sessions.csv              # Shopify session exports per client
├── output/
│   └── rca_dashboard.html            # Generated dashboard (auto-created)
├── requirements.txt
└── README.md

⚙️ Setup & Installation
1. Clone the repository
bashgit clone https://github.com/Jadhav-Yashwant/rca-dashboard.git
cd rca-dashboard
2. Install dependencies
bashpip install -r requirements.txt
3. Configure credentials
Create credentials/clickhouse_secret.json:
json{
  "host": "your-clickhouse-host",
  "port": 8443,
  "username": "your-username",
  "password": "your-password",
  "database": "your-database",
  "secure": true
}
4. Configure clients
Create config/clients_config.json:
json{
  "ClientKey": {
    "display_name": "Brand Name",
    "sessions_csv": "data/clientkey/sessions.csv",
    "currency": "₹"
  }
}
5. Add Shopify session CSVs
Export session data from Shopify Analytics and place at the path defined in clients_config.json.
Required columns:

Day, Sessions, Sessions with cart additions, Sessions that reached checkout
Bounce rate, Landing page path, Hour of day, UTM source, UTM campaign

6. Run the notebook
Open RCA_Dashboard_v8_COMPLETE.ipynb in Jupyter and run all cells in order:
CellPurposeCell 1Imports & config loadingCell 2ClickHouse connectionCell 3Helper functionsCell 4Load all client dataCell 5Date filtersCell 6Analysis functionsCell 7Generate analysis for all clientsCell 8HTML dashboard generatorCell 9Save HTML to output/Cell 10Launch local server & open in browser
The dashboard will open automatically at http://localhost:8080/rca_dashboard.html

📊 Metrics Tracked
MetricDescriptionSessionsTotal visitsBounce Rate% of single-page sessionsATC Rate% of sessions with cart additionsConversion Rate% of sessions resulting in ordersOrdersTotal number of ordersRevenueTotal revenueRPSRevenue per sessionAOVAverage order value
Delta values show Tectonic vs Shopify percentage change for each metric.

🔒 Security Notes

Never commit credentials/clickhouse_secret.json — it is listed in .gitignore
Never commit data/ CSVs if they contain client PII
The output/ folder is also excluded from version control


📌 Requirements

Python 3.8+
Jupyter Notebook / JupyterLab
ClickHouse instance with relevant tables
Shopify session CSV exports


👤 Author
Yashwant Jadhav
LinkedIn · GitHub
