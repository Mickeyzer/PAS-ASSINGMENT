# Assignment 1: Learn Probability Density Functions using Roll-Number-Parameterized Non-Linear Model

## Overview
This assignment demonstrates how to estimate probability density functions (PDFs) from real-world data using a roll-number-parameterized non-linear transformation. The workflow involves transforming air quality data (NO₂ concentrations) and learning the parameters of the resulting distribution.

## Objectives
- Apply a non-linear transformation to environmental data
- Estimate probability density function parameters from transformed data
- Visualize original and transformed distributions
- Compare empirical distributions with theoretical PDFs

## Dataset
The assignment uses an air quality dataset (`data.csv`) containing NO₂ (Nitrogen Dioxide) concentration measurements.

## Methodology

### Step 1: Non-Linear Transformation
Each data point x is transformed into z using a roll-number-dependent function:

```
z = x + aᵣ × sin(bᵣ × x)
```

Where:
- `aᵣ = 0.05 × (r mod 7)`
- `bᵣ = 0.3 × ((r mod 5) + 1)`
- `r = 102313022`

### Step 2: Parameter Estimation
The transformed data is modeled using a Gaussian-like PDF:

```
p(z) = c × exp(-λ(z - μ)²)
```

Parameters estimated from the data:
- **μ (mu)**: Mean of the transformed distribution
- **λ (lambda)**: Precision parameter = 1/(2×variance)
- **c**: Normalization constant = √(λ/π)

### Step 3: Validation
Visualize the estimated PDF against the empirical histogram to verify the model fit.

## Installation & Requirements

```bash
pip install numpy pandas matplotlib seaborn
```

For Google Colab, these libraries are pre-installed.

## Usage

1. **Upload the dataset**: Run the first code cell to upload `data.csv`
2. **Load and preprocess**: The notebook automatically:
   - Selects the NO₂ feature
   - Removes missing and negative values
3. **Apply transformation**: Set your roll number in the designated cell
4. **Estimate parameters**: Run the parameter estimation cells
5. **View results**: The final cell displays μ, λ, and c values

## File Structure

```
Assignment-1.ipynb          # Main Jupyter notebook
data.csv                    # Air quality dataset (to be uploaded)
README.md                   # This file
```

## Key Results

The notebook outputs:
- Original NO₂ distribution histogram
- Transformed distribution (z) histogram
- Estimated PDF overlaid on empirical distribution
- Final parameter values: μ, λ, c

## Data Preprocessing

The following preprocessing steps are applied:
- Drop NA values
- Filter out negative NO₂ concentrations
- Maintain data integrity for statistical analysis

## Visualization

The assignment includes three main visualizations:
1. **Original Distribution**: Histogram of raw NO₂ concentrations
2. **Transformed Distribution**: Histogram after non-linear transformation
3. **PDF Estimation**: Comparison of empirical vs. theoretical distributions

## Notes

- The PDF assumes a Gaussian-like form in the transformed space
- Ensure the dataset encoding is set to 'latin1' for proper loading

## Troubleshooting

**Issue**: File upload fails
- **Solution**: Ensure `data.csv` is in the correct format and accessible

**Issue**: Negative values in data
- **Solution**: The preprocessing step automatically filters these out

**Issue**: PDF doesn't match histogram well
- **Solution**: Verify transformation parameters and check for outliers

## Author
Ishan Bhat 102313022

## License
Educational use only.
