

# AIOps Anomaly Detection Agent

## Overview

This project implements a lightweight AI-driven AIOps agent that monitors system metrics and autonomously detects anomalous behavior.

The system uses unsupervised machine learning to identify abnormal system states and applies a decision layer to recommend remediation actions.

---

# Architecture & Design

## High-Level Flow

```
System Metrics → Preprocessing → Anomaly Detection → Decision Engine → Action Recommendation
```

### 1 Data Collection Layer

System metrics are either:

* Loaded from a dataset
* Or simulated in real time (CPU, Memory, Disk I/O, Network I/O)

---

### 2 Preprocessing Layer

* Select relevant numeric features
* Apply feature scaling using `StandardScaler`

---

### 3 Anomaly Detection Layer

* Model: **Isolation Forest**
* Unsupervised learning approach
* Identifies rare and abnormal system states

Outputs:

* `1` → Normal
* `-1` → Anomaly
  Converted to:
* `1` → Anomaly
* `0` → Normal

---

### 4 Decision & Action Layer

If anomaly is detected:

* Evaluate which metric exceeds threshold
* Generate recommended action to take

This transforms passive detection into actionable AIOps behavior.

---

### 5 Autonomous Monitoring Loop

The agent runs continuously in a loop:

1. Collect metrics
2. Detect anomalies
3. Decide action
4. Output recommendation
5. Sleep and repeat

This simulates real-time monitoring in cloud infrastructure.

---

# AI Techniques & Logic Used

## 1. Unsupervised Anomaly Detection

Isolation Forest isolates anomalies by randomly partitioning feature space.

Why chosen:

* Works well for high-dimensional numeric data
* No need for labeled training data
* Efficient and scalable

---

## 2. Feature Standardization

Used `StandardScaler` to normalize feature distributions.

Why important:

* Prevents one metric from dominating anomaly detection
* Improves separation of abnormal points

---


## 3. Rule-Based Decision Engine

After detection, a lightweight rule engine, for example:

```
if CPU > 85:
    recommend scale up
```

---

## Autonomous Agent Pattern

The system is structured as:

```
Detect → Decide → Act
```

which mirrors real AIOps architectures.

---

# Setup Instructions

## 1. Clone Repository

---

## 2. Install Dependencies

```
pip install pandas numpy scikit-learn matplotlib
```

---

## 3. Run Notebook

Open:

```
anomaly_detection.ipynb

```

---

# Assumptions

* System metrics are numeric and structured
* Anomaly percentage is 10%
* Threshold-based remediation is acceptable


---

# Future Improvements


## 1. Multi-Agent Architecture

Separate agents for:

* Detection
* Diagnosis
* Remediation

---
## 2. Expand the Training Dataset

---

# Dataset Used:
https://www.kaggle.com/datasets/programmer3/cloud-resource-usage-dataset-for-anomaly-detection?resource=download

---

# Video:

https://youtu.be/iqFuLO40IhI

