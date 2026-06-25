# 📊 DCF Calculator

A **Discounted Cash Flow (DCF) Valuation Calculator** built in Python (Jupyter Notebook) to estimate the intrinsic value of a stock and determine if it's undervalued or overvalued — with a configurable Margin of Safety.

---

## 🚀 Features

- Two-stage FCF growth model (Year 1–5 and Year 6–10)
- Terminal value calculation using Gordon Growth Model
- Enterprise Value → Equity Value → Intrinsic Value per share
- Margin of Safety (MOS) buy price
- Instant verdict: **Undervalued** or **Overvalued**
- Indian market-friendly (₹ Crore inputs)

---

## 📥 Inputs

| Parameter | Description |
|---|---|
| Current FCF | Free Cash Flow in ₹ Crore |
| Discount Rate (WACC) | Weighted Average Cost of Capital (%) |
| Growth Rate Year 1–5 | Expected FCF growth for first 5 years (%) |
| Growth Rate Year 6–10 | Expected FCF growth for next 5 years (%) |
| Cash | Cash & equivalents in ₹ Crore |
| Debt | Total debt in ₹ Crore |
| Market Cap | Current market capitalisation in ₹ Crore |
| Current Market Price | Stock's current price (₹) |
| Terminal Growth Rate | Perpetual growth rate beyond Year 10 (%) |
| Margin of Safety | Discount applied to intrinsic value (%) |

---

## 📤 Output

```
======RESULTS=====
Enterprise Value      : ₹ X,XX,XXX.XX Cr
Equity Value          : ₹ X,XX,XXX.XX Cr
Intrinsic Value/Share : ₹ XXX.XX per share
MOS Buy Price         : ₹ XXX.XX per share
Status: Undervalued ✅ / Overvalued ❌
```

---

## 🛠️ Installation & Usage

### Prerequisites

- Python 3.x
- Jupyter Notebook or JupyterLab

### Setup

```bash
# Clone the repository
git clone https://github.com/your-username/dcf-calculator.git
cd dcf-calculator

# (Optional) Create a virtual environment
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate

# Install Jupyter if not already installed
pip install notebook
```

### Run

```bash
jupyter notebook DCF-Calculator.ipynb
```

Then run all cells and enter your inputs when prompted.

---

## 📐 How It Works

The calculator uses a **two-stage DCF model**:

1. **Stage 1 (Years 1–5):** FCF grows at `growth_1_5` rate; each year's FCF is discounted back to present value.
2. **Stage 2 (Years 6–10):** FCF grows at `growth_6_10` rate; similarly discounted.
3. **Terminal Value:** Calculated using the Gordon Growth Model on Year 10 FCF, then discounted to present.
4. **Enterprise Value** = PV of FCFs + PV of Terminal Value
5. **Equity Value** = Enterprise Value + Cash − Debt
6. **Intrinsic Value/Share** = Equity Value ÷ Shares Outstanding
7. **MOS Price** = Intrinsic Value × (1 − Margin of Safety)

---

## ⚠️ Disclaimer

This tool is for **educational and research purposes only**. It is not financial advice. Always do your own due diligence before making investment decisions.

---

## 📄 License

This project is licensed under the [MIT License](LICENSE).

---

## 🤝 Contributing

Contributions are welcome! Feel free to open an issue or submit a pull request for improvements like:
- GUI / web interface
- Multi-stock batch analysis
- Export results to PDF/Excel
- Historical FCF data auto-fetch via API
