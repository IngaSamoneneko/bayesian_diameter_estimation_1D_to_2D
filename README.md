# Bayesian Diameter Estimation from Chord Lengths

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

A computational method for estimating sphere diameters from chord length measurements in 2D cross-sections using Bayesian inference.

## Key Features
- **Normalized Geometry**: All inputs/outputs scaled to [0,1] range
  - `true_diameter ∈ (0,1)`
  - `chord_lengths ∈ [0,1]`
- **Exact Bayesian Solution**: Closed-form posterior estimation
- **Visual Diagnostics**: Interactive Jupyter notebook visualization

## Normalization Requirements
For correct operation:
1. **Input Data** must be pre-scaled such that:
   ```python
   # Example normalization
   true_diameter = actual_diameter / max_expected_diameter
   chord_lengths = measured_lengths / max_expected_diameter|
   
# To recover physical units
estimated_diameter = posterior_mean * max_expected_diameter

from diameter_estimation import bayesian_estimator

# Normalized inputs (all values ∈ [0,1])
chords = [0.15, 0.22, 0.18]  # Normalized chord lengths

# Run estimation
results = bayesian_estimator(chords)
print(f"Diameter estimate: {results['mean']:.3f} ± {results['std']:.3f}")
