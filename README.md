# DCF-Calculator-
A simple Python-based Discounted Cash Flow (DCF) Calculator for estimating intrinsic stock value using future cash flow projections.
Project Overview

# The Discounted Cash Flow (DCF) model is one of the most widely used valuation methods in:

Equity Research
Investment Banking
Private Equity
Corporate Finance
Fundamental Stock Analysis

# This calculator:

Forecasts future Free Cash Flows.
Discounts future cash flows to present value.
Calculates Terminal Value.
Determines Enterprise Value.
Calculates Equity Value.
Estimates Intrinsic Value per Share.
Applies a Margin of Safety (MOS).

### Formula Used

Present Value of Cash Flow
PV=FCF/(1+R)^n

### Where:
FCF = Free Cash Flow
r = Discount Rate (WACC)
n = Year
### Terminal Value
TV = FCF(n+1)/WACC-g
Where:
g = Terminal Growth Rate

### Enterprise Value
 EV=PV(FCF)+PV(Terminal)

### Equity Value
Equity Value=EV+Cash−Debt

Intrinsic Value Per Share
Intrinsic Value=
Shares Outstanding/Equity Value
	​
# Code Walkthrough

## Step 1: Create Function
def dcf_valuation():

Defines a function named dcf_valuation().

Functions help organize code and make it reusable.

## Step 2: Display Title
print("===== DCF VALUATION CALCULATOR =====")

Prints a heading when the program starts.

Output:

===== DCF VALUATION CALCULATOR =====
## Step 3: Collect User Inputs
Current Free Cash Flow
fcf = float(input("Current FCF (₹ Cr): "))

Example:

Current FCF: 1000
Discount Rate (WACC)
discount_rate = float(input("Discount Rate (WACC %) : ")) / 100

Example:

10%

Converted to:

0.10
Growth Rate (Years 1–5)
growth_1_5 = float(input("Growth Rate (Year 1-5 %) : ")) / 100

Used for forecasting FCF during Years 1–5.

Growth Rate (Years 6–10)
growth_6_10 = float(input("Growth Rate (Year 6-10 %) : ")) / 100

Used for forecasting FCF during Years 6–10.

Cash
cash = float(input("Cash (₹ Cr): "))

Cash available on company's balance sheet.

Debt
debt = float(input("Debt (₹ Cr): "))

Total company debt.

Market Capitalization
market_cap = float(input("Market Cap (₹ Cr): "))

Needed to estimate shares outstanding.

Current Share Price
current_price = float(input("Current Market Price (₹): "))

Current stock price.

Terminal Growth Rate
terminal_growth = float(input("Terminal Growth Rate (%) : ")) / 100

Long-term growth assumption.

Typically:

2% – 5%
Margin of Safety
mos = float(input("Margin of Safety (%) : ")) / 100

Example:

25%

Converted to:

0.25
## Step 4: Initialize Variables
pv_fcf = 0
current_fcf = fcf
pv_fcf

Stores total present value of projected cash flows.

current_fcf

Stores the latest FCF value while forecasting.

## Step 5: Forecast Years 1–5
for year in range(1, 6):

Loops through:

Year 1
Year 2
Year 3
Year 4
Year 5
Grow FCF
current_fcf *= (1 + growth_1_5)

Example:

FCF = 1000
Growth = 10%

New FCF = 1100
Discount to Present Value
pv_fcf += current_fcf / ((1 + discount_rate) ** year)

Example:

1100 / (1.10)^1

Adds discounted value to total PV.

## Step 6: Forecast Years 6–10
for year in range(6, 11):

Loops through:

Year 6
Year 7
Year 8
Year 9
Year 10
Apply Growth
current_fcf *= (1 + growth_6_10)

Uses second-stage growth assumption.

Discount Cash Flow
pv_fcf += current_fcf / ((1 + discount_rate) ** year)

Adds PV of each year's cash flow.

## Step 7: Calculate Terminal Value
Next Year's FCF
terminal_fcf = current_fcf * (1 + terminal_growth)

Calculates Year 11 FCF.

Gordon Growth Formula
terminal_value = terminal_fcf / (discount_rate - terminal_growth)

Assumes perpetual growth after Year 10.

## Step 8: Discount Terminal Value
pv_terminal = terminal_value / ((1 + discount_rate) ** 10)

Converts terminal value into present value.

## Step 9: Enterprise Value
enterprise_value = pv_fcf + pv_terminal

Adds:

PV of forecast cash flows
PV of terminal value
## Step 10: Equity Value
equity_value = enterprise_value + cash - debt

Adjusts for:

Cash
Debt

Formula:

Equity Value = EV + Cash − Debt
## Step 11: Shares Outstanding
shares_outstanding = market_cap / current_price

Example:

Market Cap = ₹100000 Cr

Share Price = ₹100

Shares = 1000 Cr
## Step 12: Intrinsic Value Per Share
intrinsic_value = equity_value / shares_outstanding

Calculates fair value of one share.

## Step 13: Margin of Safety Price
mos_price = intrinsic_value * (1 - mos)

Example:

Intrinsic Value = ₹500

MOS = 25%

MOS Price = ₹375
## Step 14: Display Results
print(f"Enterprise Value      : ₹{enterprise_value:,.2f} Cr")

Displays Enterprise Value.

print(f"Equity Value          : ₹{equity_value:,.2f} Cr")

Displays Equity Value.

print(f"Intrinsic Value/Share : ₹{intrinsic_value:,.2f}")

Displays fair value per share.

print(f"MOS Buy Price         : ₹{mos_price:,.2f}")

Displays target buy price.

## Step 15: Valuation Decision
if current_price < mos_price:

Checks if stock trades below MOS price.

Undervalued
print("Status: UNDERVALUED ✅")
Overvalued
print("Status: OVERVALUED ❌")
## Step 16: Run the Program
dcf_valuation()

Calls the function and starts the calculator.

Example Input
Current FCF: 1000
WACC: 10
Growth 1-5: 12
Growth 6-10: 8
Cash: 5000
Debt: 2000
Market Cap: 100000
Current Price: 100
Terminal Growth: 4
MOS: 25
Example Output
===== RESULTS =====

Enterprise Value      : ₹25,438.56 Cr
Equity Value          : ₹28,438.56 Cr
Intrinsic Value/Share : ₹28.44
MOS Buy Price         : ₹21.33

Status: OVERVALUED ❌
# Future Improvements
Sensitivity Analysis
Excel Export
Graphical Visualization
Yahoo Finance Integration
Multi-Stage DCF Model
Monte Carlo Simulation
Streamlit Web App
Author

# Udith B
# & Python Projects | Equity Research | Valuation Models | Financial Analysis 🚀
