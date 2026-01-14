# Plant Disease Decision Pipeline

## Overview

This repository presents an applied machine learning prototype for precision agriculture that detects crop disease from RGB imagery and translates model predictions into actionable field decisions. The system is designed as a decision-support tool rather than an academic classification benchmark, with emphasis on real-world constraints such as limited data, offline inference, and asymmetric error costs.

The work combines a lightweight image classification model with a simple, interpretable decision layer intended to support fast and practical decision-making by farmers.

---

## Problem Context

Manual crop scouting is slow and often detects disease only after visible symptoms appear, by which time infections may have already spread. Laboratory testing is accurate but too slow for timely intervention. Farmers need early, localized signals that help them decide whether to ignore an alert, manually verify specific areas, or take targeted action.

This project explores how drone-captured RGB imagery can be used to flag potential disease hot spots and how uncertain model outputs can be converted into practical recommendations under real operational constraints.

---

## Approach

### Disease Detection

A binary image classifier (Healthy vs Diseased) is trained using transfer learning on a limited public plant disease dataset. The model is intentionally lightweight to ensure feasibility on standard consumer hardware without reliance on cloud infrastructure.

Key characteristics:

* RGB-only input
* Dataset size capped at 5,000 images
* Offline inference
* Emphasis on recall and false negative analysis

Model evaluation includes standard metrics as well as qualitative failure case analysis to highlight risks in real-world deployment.

### From Prediction to Decision

Model outputs alone are insufficient for field decisions. A rule-based decision logic layer converts predictions into recommendations by considering:

* Percentage of the field flagged as diseased
* Model confidence
* Farmer budget constraints
* Time remaining until harvest
* Relative cost of false positives versus false negatives

The goal is not to automate treatment, but to support informed, cost-aware decisions.

---

## Key Assumptions and Constraints

* Imagery is RGB-only, captured by drones at moderate altitude
* Internet connectivity may be unavailable during field operations
* Training data is limited and potentially biased toward clean, plant-clinic-style images
* Environmental noise such as shadows, occlusion, motion blur, and lighting variation is expected

---

## Limitations

This is a prototype and has known limitations:

* Performance is likely optimistic due to dataset bias
* Model confidence is not calibrated
* Early-stage disease may be missed if visual signals are subtle
* Shadows and lighting artifacts may cause false positives

These limitations are explicitly acknowledged to clarify where future work is required.

---

## How to Use

The entire implementation, including training, evaluation, failure analysis, and decision logic, is contained within the provided Colab notebook. The notebook can be run end-to-end to reproduce results and explore different decision scenarios.

---

## Disclaimer

This project is intended for research and evaluation purposes only. It is not production-ready and should not be used as a standalone diagnostic or treatment system in real agricultural operations.

---
