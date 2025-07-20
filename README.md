# Anomaly-Detection-for-CNC-Machining

## Overview
This project is a deep dive into anomaly detection using sensor data from a Computer Numerical Control (CNC) machine. The analysis tackles two separate but related challenges using a dataset of tool audio profiles and power/vibration data:

 - Acute Anomaly Detection: Identifying which of sixteen tools experienced an acute failure at a specific time.
 - Wear-Out Detection: Identifying a different tool that was gradually wearing out over time.

By developing a suite of statistical metrics and applying machine learning techniques like PCA and K-means clustering, this investigation successfully identifies both the broken and the worn-out tools from the raw signal data.

## Methodology & Features
### Part 1: Identifying the Broken Tool
 - Signal Processing: The raw audio waveforms were transformed into a Root-Mean-Square (RMS) representation and smoothed using a wavelet denoise function to emphasize their structural shapes.
 - Feature Engineering: A custom suite of metrics was developed to compare a "good" tool cycle against potentially anomalous ones. These include:
 - Instantaneous Disagreement: Root-Mean-Squared-Difference (RMSD) and Area Under the Residual Curve (AUC).
 - Overall Similarity: Pearson Correlation, Cross-Correlation, and Dynamic Time Warping (DTW) to account for phase shifts.
 - Unsupervised Learning: Principal Component Analysis (PCA) and K-Means clustering were applied to the engineered metrics to successfully isolate the anomalous tool as an outlier.

### Part 2: Identifying the Worn-Out Tool
 - First-Principles Hypothesis: Based on the physical principle that a worn-out tool is less efficient and expends more energy through vibration.
 - Vibration Analysis: Used the power and velocity vibration data provided for the tools.
 - Energy Calculation: The total vibrational energy for each cycle was calculated by integrating the square of the total vibrational velocity. A clear increasing trend in energy expenditure over time successfully identified the worn-out tool.

The analysis successfully identified Tool 1 as the most likely candidate for the acute, one-off anomaly.

Tool 4 was identified as the worn-out tool, confirmed by a clear, rising trend in its vibrational energy output across successive cycles, followed by a sharp drop when the tool was replaced.







