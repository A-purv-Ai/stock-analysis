# 10-Year Stock Performance Analysis: Data-Backed Investment Insights

[![Python](https://img.shields.io/badge/Python-3.11+-blue?logo=python&logoColor=white)](https://www.python.org/)
[![SQLite](https://img.shields.io/badge/SQLite-3.x-lightgrey?logo=sqlite&logoColor=blue)](https://www.sqlite.org/index.html)
[![CustomTkinter](https://img.shields.io/badge/CustomTkinter-ModernGUI-orange)](https://github.com/TomSchimansky/CustomTkinter)
[![Tableau](https://img.shields.io/badge/Tableau-Dashboard-purple?logo=tableau&logoColor=white)](https://www.tableau.com/)
[![Pandas](https://img.shields.io/badge/Pandas-DataProcessing-lightblue?logo=pandas&logoColor=black)](https://pandas.pydata.org/)

---

## Overview

This project analyses **10 years of historical stock performance** (2014–2024) across four major equities — **MSFT, IBM, MS, and AAPL** — to answer a practical investment question:

> *Which stock offered the safest and most consistent long-term return over the past decade?*

The analysis pipeline covers end-to-end data work: automated data acquisition from Yahoo Finance, structured storage in SQLite, feature engineering (custom **Normalized Close** metric), and audience-specific **Tableau** dashboards for both executive and managerial views.

---

## The Analytical Question

Traditional stock comparison using raw closing prices is misleading — stocks trade at different price scales, making direct comparison impossible. This project addresses that by engineering a **Normalized Close** feature that rebases all stocks to a common starting value (2014 = 1.0), enabling true like-for-like performance comparison across the full decade.

---

## 📈 Results

### Normalised 10-Year Returns (2014 baseline = 1.0×)

| Stock | Final Normalised Return | Interpretation |
|:------|:------------------------|:---------------|
| **MSFT** | **15.03×** | ~15× its 2014 value |
| **AAPL** | **15.00×** | ~15× its 2014 value |
| **MS** | **5.77×** | ~5.8× its 2014 value |
| **IBM** | **2.12×** | ~2.1× its 2014 value — clear underperformer |

### Key Observations

- **AAPL and MSFT are near-tied on raw return** — MSFT edges AAPL by a marginal 0.03× (15.03 vs 15.00) over the full decade. On raw terminal return alone, neither stock is a clear winner.
- **AAPL's distinguishing edge lies elsewhere:** its pre-2020 growth trajectory was smoother and more consistent than MSFT's, it dominated trading volume throughout the decade (peak annual volumes up to ~60B shares), and its normalised price line showed lower relative drawdowns during the March 2020 COVID crash.
- **MSFT** matched AAPL's terminal return but with higher volatility in specific periods, reflecting the broader re-rating of its cloud business (Azure) post-2018.
- **Morgan Stanley (MS)** returned ~5.77× — respectable, but well behind the two tech leaders. Its trajectory shows cyclical patterns tied to financial sector macro movements.
- **IBM** was the clear underperformer at only 2.12× over 10 years — barely outpacing inflation and serving as a cautionary data point for long-hold equity selection.
- **March 2020 COVID Crash** is visible as a sharp dip across all four tickers, followed by a strong recovery — most pronounced in AAPL and MSFT, less so in IBM.
- **AAPL trading volume** declined over the period (from ~60B in 2014 to ~5–10B by 2024), reflecting price appreciation — fewer shares are needed to represent the same dollar value, a healthy sign of compounding value growth.

---

## 📊 Data Visualizations

🖼️ **Stocks' Relative Performance Over the Last Decade**
[![Stocks' Relative Performance Over the Last Decade](images/Stocks_Relative_Performance.png)](images/Stocks_Relative_Performance.png)
Normalised closing price evolution for MSFT, IBM, MS, and AAPL — rebased to 1.0 at start of 2014 for true same-scale comparison using the custom **Normalized Close** feature.

🖼️ **Stocks Daily Closing Price Trend**
[![Stocks Daily Closing Price Trend](images/Stocks_Closing_Price_Trend.png)](images/Stocks_Closing_Price_Trend.png)
Raw daily closing price evolution, revealing absolute price movements and volatility across all four tickers.

🖼️ **Executive Overview Dashboard**
[![Executive Overview Dashboard](images/Executive_Overview_Story.png)](images/Executive_Overview_Story.png)
Combined normalised stock performance and annual trading volume for MSFT, IBM, MS, and AAPL (2014–2024) — designed for strategic, high-level review.

🖼️ **Managerial Overview Dashboard**
[![Managerial Overview Dashboard](images/Managerial_Overview_Dashboard.png)](images/Managerial_Overview_Dashboard.png)
Granular quarterly traded volume alongside normalised price trends — designed for operational and managerial review.

---

## Tech Stack

| Category         | Tools / Libraries         |
|:-----------------|:--------------------------|
| Data Acquisition | yfinance (Yahoo Finance)  |
| Data Handling    | Pandas, SQLite3           |
| Feature Engineering | Custom Normalized Close metric |
| Visualization    | Tableau                   |
| GUI Application  | CustomTkinter             |
| Environment      | Python 3.11+              |

---

## Data-to-Insight Flow

```
Yahoo Finance API → Python (yfinance + pandas) → SQLite DB → CSV Export → Tableau Dashboard
```

The desktop GUI (CustomTkinter) enables CRUD (Create, Read, Update, Delete) management of the tracked ticker list, making it easy to add or remove stocks and re-run the pipeline on demand.

---

## 📂 Project Structure

```
📦 stock-analysis/
┣ 📁 scripts/
┃ ┣ 📜 main_guiM.py        ─ Modern GUI (CustomTkinter)
┃ ┣ 📜 main_guiC.py        ─ Classic GUI
┃ ┣ 📜 db_utils.py         ─ Database utility functions (CRUD)
┃ ┣ 📜 import_yahoo.py     ─ Yahoo Finance automated importer
┃ ┣ 📜 export_csv.py       ─ CSV export script
┃ ┣ 📜 insert_window.py    ─ GUI: add ticker
┃ ┣ 📜 delete_window.py    ─ GUI: delete record
┃ ┣ 📜 select_window.py    ─ GUI: view records
┃ ┗ 📜 update_window.py    ─ GUI: update entry
┣ 📁 images/
┃ ┣ 🖼️ Executive_Overview_Story.png
┃ ┣ 🖼️ Stocks_Relative_Performance.png
┃ ┣ 🖼️ Stocks_Closing_Price_Trend.png
┃ ┗ 🖼️ Managerial_Overview_Dashboard.png
┣ 📁 database/
┃ ┣ 🗄️ stocks.db               ─ SQLite database
┃ ┣ 📄 stock_data_export.csv    ─ Exported CSV for Tableau
┃ ┗ 🗄️ stocks DB Browser.sqpro ─ (Optional) DB Browser session
┣ 📜 README.md
┗ (other project files)
```

---

## ⚙️ Installation & Usage

1. **Clone the repository**
   ```bash
   git clone https://github.com/A-purv-Ai/stock-analysis.git
   cd stock-analysis
   ```
2. **Install dependencies**
   ```bash
   pip install customtkinter yfinance pandas
   ```
3. **Run the modern GUI**
   ```bash
   python main_guiM.py
   ```
   *(Alternatively, run `python main_guiC.py` for the classic version.)*

4. **Export to CSV for Tableau**
   ```bash
   python export_csv.py
   ```
   Import `database/stock_data_export.csv` into Tableau to reproduce the dashboards.

---

## 🔮 Future Enhancements

- Add risk metrics: Sharpe Ratio, max drawdown, rolling volatility
- Expand ticker universe beyond 4 stocks
- Integrate live price feeds for real-time dashboard refresh
- Build a Streamlit web app for browser-based interactive exploration

---

## 👤 Author

**Apurva Upadhyay**
*Data Analytics | Data Science | AI Engineering*

[![LinkedIn](https://img.shields.io/badge/LinkedIn-%230077B5.svg?logo=linkedin&logoColor=white)](https://linkedin.com/in/upadhyayapurva) [![email](https://img.shields.io/badge/Email-D14836?logo=gmail&logoColor=white)](mailto:apurvaupadhyayai@gmail.com)

📫 Feel free to connect and share feedback!

---

## 🏷️ Keywords

Financial Analytics · Equity Analysis · Investment Analysis · Python · Pandas · Feature Engineering · Normalized Close · SQLite · Yahoo Finance · Tableau · Data Visualization · Stock Performance · Long-Term Returns · Dashboard · End-to-End Data Pipeline
