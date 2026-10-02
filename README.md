# Transaction Anomaly Checker

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/kennedyhuang88/transaction-anomaly-checker/blob/main/transaction_anomaly_checker.ipynb)

A Python notebook that scans a business's payment records and flags transactions that look suspicious.

## Why I built this

My family's business once had a problem with an employee hiding transactions. I helped go through the records by hand to find the faulty entries. This project is my first attempt at automating that review. I can't share real financial data, so the notebook generates a simulated dataset of 500 transactions and plants four kinds of problems in it on purpose (53 in total) in it on purpose.

## What it checks

| Check | What it looks for |
|---|---|
| Duplicate payments | Same date, vendor, and amount appearing more than once |
| Outliers | Amounts far above the normal range for their category (IQR rule) |
| Just under the limit | Payments between $470 and $499.99, just below a $500 approval limit |
| Missing approver | Payments with no approver on file |

Each transaction gets a `total_flags` score showing how many checks it tripped.

## Results

On the simulated data, 62 of 508 transactions were flagged. The notebook also includes a bar chart of flags by check and a histogram of transaction amounts with the approval limit marked.

## How to run it

1. Click the **Open in Colab** badge above.
2. In Colab, choose **Runtime → Run all**.

No installs or data files are needed. The notebook builds its own data.

## Tools

Python, pandas, NumPy, Matplotlib, Google Colab

## Limitations and next steps

- The rules use fixed thresholds and outlier limits I chose, not ones learned from data, so they won't catch every problem and may flag some normal transactions.
- Next, I'd like to try this on real anonymized data, add a small dashboard for exploring flagged transactions, and compare it to an anomaly-detection model like Isolation Forest.

## Notes

This is my first data analysis project. I used AI tools for coding and debugging help, and I worked through the logic myself. I'm a beginner in data analytics and very interested in learning more.
