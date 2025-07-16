# aave-credit-score

# Aave V2 Credit Scoring – ML Challenge

## Problem Statement

We were given raw transaction-level DeFi data from the Aave V2 protocol. Each row shows a wallet's action like deposit, borrow, repay, liquidation, etc.
The goal was to generate a **credit score (0–1000)** for each wallet based only on its transaction behavior.

---

## Dataset

- Format: JSON (approx 100k records)
- Important Columns:
  - `userWallet` → Wallet address
  - `action` → Type of activity (e.g., borrow, repay)
  - `actionData` → Contains transaction amount
  - `timestamp` → Time of action

---

## Approach

1. Loaded the JSON file using Python + Pandas
2. Extracted transaction `amount` from `actionData`
3. Grouped data by `userWallet`
4. Engineered wallet-level features like:
   - Total deposits
   - Total borrows
   - Total repays
   - Total liquidations
5. Assigned a rule-based score:
   - +10 for each repay
   - +5 for each deposit
   - −3 for each borrow
   - −30 for each liquidation

Final score = base 500 + points from above (capped between 0 and 1000)

---

##  Tools Used

- Google Colab (Python 3)
- Pandas, NumPy, Seaborn, Matplotlib

---

## Output

- `wallet_scores.csv`: Wallets with credit scores  
- `score_distribution.png`: Graph showing score distribution  
- `analysis.md`: Insights on score ranges and wallet behavior

---

## How to Run

1. Upload the JSON file to Google Drive  
2. Open the Colab notebook  
3. Run the cells step by step  
4. Final results saved to your Drive as `.csv` and `.png`

---

## Example Output

| userWallet | credit_score |
|------------|---------------|
| 0xABC123... | 760 |
| 0xDEF456... | 210 |

---

## Future Improvements

- Add time-based features (e.g. frequency)
- Use ML model like Random Forest instead of rule-based scoring
- Use wallet reputation from multiple protocols

