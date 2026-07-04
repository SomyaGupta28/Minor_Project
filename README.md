# Minor_Project
# SpendDNA: Fintech Transaction Analytics System

SpendDNA is a Python-based transaction analytics tool engineered to replicate the financial data pipelines used by top Indian fintech companies (like Cred, Slice, and Jupiter). The system parses raw, messy multi-format bank/UPI statements, normalizes vendor text, categorizes spending, handles anomaly detection, and generates a formatted, console-printed analytics report—reminiscent of a "Spotify Wrapped" for money.

## 🎯 Project Overview & Features

The system processes 6 months of synthetic financial data (1,328 transaction rows) for a Bengaluru-based software engineer, executing 8 core analytical features:

1. **Transaction Parser:** Extracts and cleans 4 distinct date formats and 3 different amount formats while standardizing transaction type fields and filtering duplicates.
2. **Vendor Extractor (Merchant Normalization):** Uses keyword-mapping logic to clean messy UPI/POS text (e.g., mapping `BUNDL Tech P L` to `Swiggy`). 
3. **Category Tagger:** Maps normalized merchants into 12 distinct financial categories (e.g., Food Delivery, Investments, Quick Commerce).
4. **Spending Overview:** Generates headline executive stats including total debits, credits, net savings rate, and top category expenditures.
5. **Monthly Trend Analysis:** Identifies month-on-month percentage changes and growth trends across various expense categories using data matrices.
6. **Time-of-Day Patterns:** Builds a time-distribution matrix to isolate specific consumer habits, such as late-night food ordering or morning cafe runs.
7. **Anomaly Detection:** Flags unusually large transactions by calculating localized Z-scores within specific spending categories.
8. **Behavioral Archetype Detection:** Implements a rule-based system to flag user profiles matching multiple archetypes (such as *The Foodie*, *The Investor*, *The Late-Night Snacker*, and *The YOLO Spender*).

---

## 🛠️ Tech Stack & Constraints

This project enforces strict architecture constraints to showcase pure problem-solving and algorithmic logic to recruiters. **No external automation tools or heavy ML libraries were used.**

### Built With:
* **Python Fundamentals:** Loops, conditional chains, dictionaries, lists, sets, and f-string formatting.
* **Pandas:** Data ingestion (`read_csv`), `groupby`, `pivot_table`, `.dt` / `.str` accessors, and data wrangling transforms.
* **NumPy:** Vectorized arrays, mathematical aggregates (`mean`, `std`), and rolling matrix math.

### Forbidden (Strictly Excluded):
* ❌ **No Data Profiling Libraries** (`pandas-profiling`, `sweetviz`) — all metrics are coded manually.
* ❌ **No Visualization Libraries** (`matplotlib`, `seaborn`) — all reports and data bars are purely text/ASCII-based.
* ❌ **No Advanced ML/Stats Libraries** (`scikit-learn`, `scipy`) — Z-score algorithms are calculated by hand.
* ❌ **No Regular Expressions** (`re` module) — pattern matching is handled via native string manipulation methods.

---

## 📊 Target Report Architecture

The engine generates a clean, screenshot-ready terminal report with the following structural layout:

```text
================================================================
 SpendDNA REPORT - RAHUL SHARMA
 6 months - 1,310 transactions - Jan to Jun 2024
================================================================

 EXECUTIVE SUMMARY
 Total credits  : Rs. 5,09,774
 Total debits   : Rs. 8,26,679
 Net change     : -Rs. 3,16,905 (overspending)
 Savings rate   : -62.2% (BURNING SAVINGS)

 TOP CATEGORIES (% of debit total)
 Food Delivery  ################## 23.0% Rs. 1,89,899
 Quick Commerce ################   19.5% Rs. 1,61,564
 E-commerce     #############      16.8% Rs. 1,39,018

 TIME-OF-DAY PATTERNS
 Food Delivery peaks: 21:00 - 01:00 (62% of orders)
 Cafe peaks: 09:00 - 11:00 (morning runs)

 TOP ANOMALIES (3+ stddev from category mean)
 14 Apr - Myntra Rs. 12,540 (z=4.2)
 22 Mar - Amazon Rs. 18,300 (z=3.8)

 RAHUL'S SPENDING ARCHETYPES
 -> THE FOODIE (30.1% on food)
 -> THE LATE-NIGHT SNACKER (62% food after 9 PM)
 -> THE YOLO SPENDER (savings rate -62%)
================================================================
