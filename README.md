# Aave V2 Credit Scoring (0–1000)

## Overview

This project assigns a credit score (0–1000) to each wallet on the Aave V2 protocol based on their transaction history (e.g., deposit, borrow, repay, liquidation).

## Dataset

- Format: JSON  
- Fields: userWallet, action, actionData.amount, timestamp

## Tools Used

- Python (Google Colab)  
- Pandas, NumPy  
- Seaborn, Matplotlib

## Scoring Logic

Rule-based formula:

Score = 500  
+10 × repays  
+5 × deposits  
−3 × borrows  
−30 × liquidations  
(score is capped between 0 and 1000)

## Output

- score_distribution.png → credit score histogram  
- analysis.md → insights and behavior patterns

## Run Steps

1. Upload the JSON file to Google Drive  
2. Open generate_scores.ipynb in Colab  
3. Run the notebook to generate results

## Goal

Identify safe versus risky wallets based on DeFi transaction behavior.
