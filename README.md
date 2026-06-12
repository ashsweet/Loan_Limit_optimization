# Loan Limit Optimization

A comprehensive operations research solution for optimizing loan limit increase allocations across customer risk tiers to maximize profitability while managing portfolio risk.

## Problem Statement

The objective is to determine how to allocate loan limit increases across different customer segments to maximize customer retention, lifetime value, and profitability—while ensuring regulatory compliance and capital efficiency constraints are met.

## Project Structure

```
Loan_Limit_optimization/
├── loan_limit_optimization.ipynb    # Main analysis notebook (6 modules)
├── loan_limit_increases.csv         # Source data (30,000 customer records)
├── requirements.txt                 # Python dependencies
├── README.md                        # This file
└── output/
    ├── preprocessed_data.csv        # Cleaned dataset
    ├── Loan_Limit_Optimization_Report.docx  # Final report
    ├── module1_output/              # EDA visualizations
    ├── module2_output/              # Markov model outputs
    ├── module3_output/              # Demand forecasts
    ├── module4_output/              # Monte Carlo simulation results
    ├── module5_output/              # Optimization results
    └── module6_output/              # Executive summary and recommendations
```

## Methodology

The analysis follows a six-module framework:

### Module 1: Data Preprocessing & Exploratory Analysis
- Data cleaning and validation
- Payment segment analysis
- K-means clustering for customer segmentation
- **Key Finding**: Uniform ~50% default rate across all segments indicates existing policy is not risk-based

### Module 2: Markov Chain Model for Risk State Transitions
- 4-state risk model (Low, Medium-Low, Medium-High, High Risk)
- Transition probability matrix estimation
- Stationary distribution and expected time in state calculations
- Customer lifetime value by risk tier ($136 - $224)

### Module 3: Stochastic Demand Forecasting
- Economic scenario simulation (inflation, unemployment, interest rates)
- Seasonal adjustment factors (0.90 - 1.15)
- Uptake rate modeling by risk tier (45% - 70%)
- Stress testing under adverse conditions

### Module 4: Loan Lifecycle Simulation (Monte Carlo)
- 100 simulations over 12-month horizon
- Individual customer journey modeling
- Portfolio NPV distribution (Mean: $5.78M, Std Dev: $19.6K)
- Risk metrics: VaR, percentiles, default rates

### Module 5: Optimization Engine
- Constrained optimization using SLSQP algorithm
- Objective: Maximize NPV
- Constraints: Default rate ≤ 50%, allocation bounds (10%-40%), capacity (16,000/month)
- **Result**: 40/40/10/10 allocation across tiers, +3.2% NPV improvement

### Module 6: Results & Reporting
- Executive dashboard
- Implementation roadmap
- Sensitivity analysis
- Risk assessment matrix

## Key Parameters

### Given (from problem statement)
| Parameter | Value |
|-----------|-------|
| Profit per Increase | $40 |
| Eligibility Threshold | 60 days |
| Max Increases per Year | 6 |
| Annual Discount Rate | 19% |

### Assumed (model inputs)
| Parameter | Value | Rationale |
|-----------|-------|-----------|
| Monthly Capacity | 16,000 | Based on demand forecast |
| Max Portfolio Default Rate | 50% | Risk appetite ceiling |
| Loss Given Default | $120 | 3x profit per increase |
| Min/Max Tier Allocation | 10%/40% | Portfolio diversification |

## Results

### Optimal Allocation Strategy
| Risk Tier | Allocation |
|-----------|------------|
| Low Risk | 40% |
| Medium-Low Risk | 40% |
| Medium-High Risk | 10% |
| High Risk | 10% |

### Performance Metrics
- **Optimized NPV**: $5,558,354
- **NPV Improvement**: +$172,364 (+3.2% vs baseline)
- **Weighted Default Rate**: 40.0% (within 50% constraint)

## Installation

1. Create a conda environment:
```bash
conda create -n loan_opt python=3.10
conda activate loan_opt
```

2. Install dependencies:
```bash
pip install -r requirements.txt
```

3. Launch Jupyter:
```bash
jupyter notebook loan_limit_optimization.ipynb
```

## Dependencies

- Python 3.10+
- pandas, numpy
- scipy (optimization)
- scikit-learn (clustering)
- matplotlib, seaborn (visualization)
- python-docx (report generation)

## Usage

Run the notebook sequentially from Module 1 through Module 6. Each module:
1. Loads outputs from previous modules
2. Performs analysis
3. Saves results to `output/moduleX_output/`

The final report is generated in `output/Loan_Limit_Optimization_Report.docx`.

## Operations Research Techniques Used

1. **Markov Chains** - Customer risk state transitions
2. **Stochastic Simulation** - Demand forecasting with economic factors
3. **Monte Carlo Simulation** - Portfolio NPV distribution
4. **Constrained Optimization** - Allocation under business constraints

## Key Insights

1. Historical data showed uniform default rates (~50%) across all payment segments—no predictive power for risk differentiation
2. Shifted from descriptive to prescriptive analytics using theoretical risk models
3. Lower-risk customers generate significantly higher lifetime value ($224 vs $136)
4. Optimal strategy concentrates 80% allocation on lower-risk tiers while maintaining diversification
5. Model is robust to moderate economic shocks based on stress testing

## Outputs

All outputs are saved to the `output/` directory:
- CSV files: Data exports and summary statistics
- JSON files: Model parameters and results
- PNG files: Visualizations and dashboards
- DOCX: Final comprehensive report

## Author

Aishwarya Mukherjee
