# Physical-compositional-data-analysis
Evaluates data reliability in compositional datasets via Poisson noise modeling. Calculates Effective Library Size &amp; Noise Floor per sample to classify taxa as Reliable (>=10x margin), Uncertain, or Undetected. Generates profiles, heatmaps &amp; strict QC reports.

# Compositional Reliability Evaluation and Visualization Tool

[![License: MIT](https://shields.io)](https://opensource.org)
[![R-Version](https://shields.io)](https://r-project.org)

An R-based analytical framework designed to evaluate and visualize data reliability in compositional datasets (e.g., microbiome relative abundance matrices). It establishes sample-specific quality thresholds using Poisson noise modeling to distinguish true biological signals from technical artifacts near the detection limit.

## Core Methodology

The framework analyzes sequencing depths dynamically by calculating the **Effective Library Size** ($1 / \text{minimum observed non-zero proportion}$) to set a precise **Poisson Noise Floor** for each sample. Taxa are classified into three operational tiers:
*   **Reliable**: Abundances $\ge 10\times$ above the noise floor (Safety Margin).
*   **Uncertain**: Detected taxa falling below the safety margin (high risk of stochastic noise).
*   **Undetected**: Taxa completely absent or zero-valued in the sample.

## Features & Outputs

The script automates data preparation, filters uniformly zero features, and generates three professional PDF reports:
1.  **`ITAGAKI_1_Reliability_Profiles.pdf`**: Individual log-scale impulse plots showing asset distribution against noise and safety thresholds.
2.  **`ITAGAKI_2_Reliability_Heatmap.pdf`**: A clean, publication-ready grid heatmap tracking system-wide physical existence and taxon status.
3.  **`ITAGAKI_Strict_Individual_Reliability_Report.pdf`**: High-fidelity diagnostics featuring localized overlay boxes with key metrics (Effective Library Size, detected vs. reliable counts).

A final percentage-based **Reliability Score** is printed directly to the console for rapid quality control.

## Getting Started

### Prerequisites
*   **R** (version 4.0.0 or higher recommended)
*   No external R packages required (built entirely on base R graphics)

### Input Data Structure
The script expects a data frame or matrix named `Dataset` where:
*   **Rows** represent samples (with unique `rownames`).
*   **Columns** represent taxa/features.
*   **Values** represent relative or absolute abundance proportions.

### Usage
Simply load your data as `Dataset` and run the script:
```R
# Load your microbiome matrix
Dataset <- read.csv("your_data.csv", row.names = 1)

# Execute the script logic here...
```

## 📚 Academic Citation

If you use this software or its logic in your research, please cite the following works:

**Itagaki, T. (2026).**  DOI: [10.13140/RG.2.2.35655.05287](https://doi.org/10.13140/RG.2.2.35655.05287)

## License

This project is licensed under the MIT License - see the [LICENSE](https://opensource.org) link for details.

Copyright (c) 2026 Tatsuki Itagaki

WARNING: Compositional data analysis is an analysis without scales. There was very little information available regarding the compositional data, so I had to perform many unnecessary calculations to reach the true conclusion. Reliability is the shortest path to truth. 

# This is something I gained only by acknowledging my defeat and reflecting on it. This system would not exist without my mentor (Norio Sugimoto) who taught me statistics.

*For more context on the exploratory journey and the defeats that led to this methodology, please refer to my other repository.*
