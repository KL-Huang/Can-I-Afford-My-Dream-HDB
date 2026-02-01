# Can I Afford My Dream HDB?

This repository contains an Excel-based decision support tool to help prospective HDB buyers in Singapore evaluate their dream flats and assess affordability under real-world financial and regulatory constraints.

## Overview

The tool combines historical resale transaction data, housing market growth assumptions, Monetary Authority of Singapore (MAS) and Central Provident Fund (CPF) regulations, and a multi-criteria decision model (Analytic Hierarchy Process, AHP) to support users in three key tasks:

- Projecting future prices of preferred HDB flats based on historical trends and chosen criteria.
- Planning personal finances and understanding how income, savings, and debts affect purchasing power.
- Assessing loan eligibility and overall affordability under MAS and CPF rules.

## Key Features

### 1. Dream Home Selection

- Allow users to specify up to three candidate “dream homes” with attributes such as:
  - Town (Ang Mo Kio, Sengkang, Clementi)
  - Flat type (e.g., 3-room, 4-room, 5-room, Executive)
  - Remaining lease
  - Walking distance to MRT
  - Walking distance to primary school
  - Intended year of purchase
- Let users rank their decision criteria (e.g., price, location, proximity to MRT/schools, flat type).
- Use an Analytic Hierarchy Process (AHP) model to convert rankings into weights and score each property, recommending the flat that best matches the user’s priorities.

### 2. Loan Calculator

- Inputs:
  - Age of buyer(s)
  - Gross monthly salary
  - Monthly variable income (with haircut applied)
  - CPF Ordinary Account (CPF OA) balance
  - Cash on hand
  - Existing monthly debt obligations
  - Desired loan tenure
  - Income growth rate
- Integrates MAS rules (MSR, TDSR, LTV) and CPF usage constraints to compute:
  - Maximum permissible loan
  - Monthly installment
  - Required minimum cash downpayment
  - Overall purchasing power for housing

### 3. Affordability & Shortfall Analysis

- Combines projected property price, stamp duty, legal fees and other costs to compute total purchase cost.
- Checks whether the buyer can:
  - Meet the minimum cash downpayment requirement.
  - Cover the remaining balance using CPF OA and cash under CPF rules.
- If there is a funding gap, the tool:
  - Flags affordability as “FAIL”.
  - Estimates additional months of saving required given user-specified savings rates.
  - Highlights how adjusting savings rates or purchase timing affects feasibility.

### 4. Price Estimation and Simulation

- Uses historical resale transactions (e.g., 2017–2024) for selected towns to:
  - Bring past prices forward using year-by-year resale price index (RPI) growth rates.
  - Apply compounded growth to approximate current and future prices.
- Applies Monte Carlo simulation to:
  - Sample historical growth rates across multiple years.
  - Generate a distribution of possible future prices for flats that match the chosen criteria.
  - Select a representative projected price from the most probable range.

### 5. AHP Backend Calculations

- Converts user-defined rankings into normalized criterion weights.
- Assigns scores to each property for:
  - Location and accessibility (MRT/schools)
  - Flat type and size
  - Price (via pairwise comparison matrix, normalized, with cheaper flats scoring higher)
- Aggregates scores into a final AHP score per property and returns the best option to the Dream Home tab.

## How to Use

1. **Open the Excel model**  
   Open `loan_calculator_recovered.xlsx` in a recent version of Microsoft Excel (Microsoft 365 / Excel 2021 or later recommended).

2. **Select candidate properties**  
   - Go to the `Dream Home Selection` tab.  
   - Enter details for three candidate flats.  
   - Rank your decision criteria and preferred location.  
   - Review the recommended “best” property and its AHP score.

3. **Assess financing and affordability**  
   - Go to the `Loan Calculator` tab.  
   - Enter your personal financial information and assumptions (income, CPF, cash, debts, loan tenure, income growth).  
   - Review:
     - Maximum loan amount
     - Monthly installment
     - Purchasing power and regulatory limits (MSR, TDSR, LTV).

4. **Check shortfall and savings plan**  
   - Review the affordability and shortfall section.  
   - If there is a shortfall, examine how many additional months of saving are required at your chosen savings rate and whether changing purchase year or savings rate helps.

5. **Understand the methodology**  
   - For detailed formulas, assumptions, and sensitivity analyses, refer to `IS602-Final-Report.docx`.

## Data and Assumptions

- Historical HDB resale transactions for selected towns (Ang Mo Kio, Sengkang, Clementi).
- External data sources such as:
  - HDB Resale Price Index
  - HDB town and flat supply / BTO launch data
  - URA property price trends
  - MRT/LRT station locations
  - MOE school locations
  - MAS and CPF guidelines for housing loans and CPF usage
  - SORA / interest rate benchmarks and CPI / inflation data
- Assumes buyers own only one property.

## Requirements

- Microsoft Excel with support for:
  - Dynamic arrays
  - LET and LAMBDA functions  
  (e.g., Microsoft 365, Excel 2021 or later)

## Limitations

- Designed for educational and planning purposes; not a substitute for professional financial advice.
- Limited to resale HDB flats in selected towns and specific criteria.
- Projections are based on historical data and simulated growth rates; actual market prices and regulations may change.
