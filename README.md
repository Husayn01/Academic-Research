# Automated Lithofacies Classification: A Physics-Informed Machine Learning Approach

## Overview
This repository contains the code and methodology for my undergraduate research project on automating subsurface lithology interpretation. Using the **FORCE 2020 Lithology Dataset**, this project develops a machine learning pipeline that integrates geophysical domain knowledge with high-performance gradient boosting algorithms.

The goal is to transition the traditionally manual, subjective process of lithofacies identification into a deterministic and scalable computational framework suitable for modern reservoir characterization.

## Scientific Context
In geological exploration, identifying rock types (lithology) from geophysical well logs is the cornerstone of understanding subsurface formations. However, raw wireline telemetry, such as Gamma Ray, Density, and Resistivity is often noisy, sparse, and subject to sensor failure. This project addresses these "AI for Science" challenges by:
- **Encoding Physics**: Implementing petrophysical ratios (e.g., GR/RHOB) and thermodynamic constraints to guide algorithmic splitting.
- **Spatial Awareness**: Utilizing vectorized windowing to capture the vertical continuity of geological strata.
- **Handling Imbalance**: Engineering a validation strategy for an extreme 6998:1 class imbalance between Shale and rare lithologies like Basement rock.

## Repository Structure
- `Notebooks/EDA.ipynb`: Exploratory data analysis, missing value diagnostics, and geological distribution plots.
- `Notebooks/Models.ipynb`: Feature engineering pipeline, and comparative benchmarking of Random Forest, XGBoost, and LightGBM.
- `Data/`: Directory for the FORCE 2020 training and test datasets.
- `requirements.txt`: List of required Python libraries for reproducibility.

## Key Features & Methodology
1. **Physics-Informed Engineering**:
   - Logarithmic linearization of resistivity measurements.
   - Matrix-specific transformations (Neutron-Density separation).
   - Instantaneous depth-gradients for formation boundary detection.
2. **Algorithmic Benchmarking**:
   - **XGBoost**: Sparsity-aware learning to handle missing sensor data.
   - **LightGBM**: Leaf-wise growth for high-speed processing of 1.1M+ records.
   - **Random Forest**: Bagging-based baseline for noise resilience.
3. **Validation**: 10-Fold Stratified Cross-Validation to ensure statistical integrity across diverse well environments.

## Results Summary
- **Top Performer**: XGBoost achieved the highest Weighted F1-Score (0.7610), demonstrating superior precision in distinguishing subtle facies transitions.
- **Efficiency**: LightGBM provided the best operational scalability, training nearly 2x faster than the Random Forest baseline.
- **Validation**: Feature importance mapping confirmed that engineered spatial context features (lags/leads) were the primary drivers of predictive accuracy, validating the domain-driven approach.

## Installation & Usage
To reproduce the results, clone this repository and install the dependencies:

```bash
git clone https://github.com/Husayn01/Academic-Research.git
cd Academic-Research
pip install -r requirements.txt
```
## Links
- Github page: [Visit link](https://github.com/bolgebrygg/Force-2020-Machine-Learning-competition)


## Data Source
Lithofacies data used in this project was provided by the FORCE Machine Learning competition with well logs and seismic data (Bormann et al., 2020).

**Citation:**
Bormann P., Aursand P., Dilib F., Dischington P., Manral S. 2020. 2020 FORCE Machine Learning Contest.
