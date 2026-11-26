# Explainable Hybrid Intrusion Detection and Risk Prioritization for IoT Networks

## Overview

This project presents an explainable hybrid Intrusion Detection System (IDS) designed to identify malicious network activity in Internet of Things (IoT) environments.

The framework combines supervised machine learning and unsupervised anomaly detection using Random Forest and Isolation Forest. A hybrid OR-based decision mechanism combines their predictions to improve attack detection coverage.

The research uses the **CICIoT2023 dataset** for experimental evaluation.

## Research Objectives

- Detect malicious network traffic in IoT environments.
- Compare supervised and unsupervised intrusion detection approaches.
- Evaluate a hybrid detection strategy.
- Identify influential network traffic features.
- Prioritize detected threats using a risk scoring mechanism.

## Technologies Used

| Technology | Purpose |
|---|---|
| Python 3.11 | Programming language |
| Jupyter Notebook | Experimentation |
| Pandas and NumPy | Data processing |
| Scikit-learn | Machine learning |
| Matplotlib and Seaborn | Visualization |
| Joblib | Model serialization |
| CICIoT2023 | Dataset |

## Detection Architecture

The proposed framework consists of three detection approaches:

1. **Random Forest:** Supervised classification using labeled network traffic.
2. **Isolation Forest:** Unsupervised anomaly detection trained on benign traffic.
3. **Hybrid OR:** Flags traffic as malicious if either model identifies it as an attack.

A risk prioritization mechanism uses detection outputs to assign heuristic risk scores to suspicious traffic.

## Dataset

The project uses the CICIoT2023 dataset published by the Canadian Institute for Cybersecurity.

Dataset: https://www.unb.ca/cic/datasets/iotdataset-2023.html

The original dataset is not included in this repository because of its large size. Download the CSV files separately and place them in the expected data directory.

Expected structure:

```text
data/
└── CSV/
    ├── Benign_Final/
    ├── DDoS-UDP_Flood/
    ├── DDoS-TCP_Flood/
    └── ...
```

## Experimental Results

The following results were obtained using a source-file group-based evaluation split.

| Metric | Random Forest | Isolation Forest | Hybrid OR |
|---|---:|---:|---:|
| Accuracy | 88.63% | 76.51% | 88.43% |
| Precision | 85.76% | 96.09% | 85.26% |
| Recall | 86.68% | 44.59% | 86.81% |
| F1-score | 86.22% | 60.91% | 86.03% |
| False Positive Rate | 10.02% | 1.26% | 10.45% |

The hybrid approach achieved a slightly higher recall than Random Forest, while also producing a higher false positive rate. These results illustrate the trade-off between attack detection coverage and false alarms.

## Repository Structure

```text
iot-hybrid-intrusion-detection/
│
├── notebooks/
│   └── iot_hybrid_intrusion_detection.ipynb
│
│
├── Springer_Paper.pdf
├── requirements.txt
├── LICENSE
└── README.md
```

## Installation

Clone the repository:

```bash
git clone https://github.com/ishapageni/iot-hybrid-intrusion-detection.git

cd iot-hybrid-intrusion-detection
```

Create a Python environment:

```bash
conda create -n websec-research python=3.11
conda activate websec-research
```

Install dependencies:

```bash
pip install -r requirements.txt
```

Launch Jupyter Notebook:

```bash
jupyter notebook
```

Open `notebooks/iot_hybrid_intrusion_detection.ipynb` and execute the cells in order after configuring the dataset path.

## Research Paper

The complete research paper is available in:

- `Springer_Paper.pdf`


## Limitations

- Experiments use sampled CICIoT2023 records rather than the complete dataset.
- Group separation is performed at the source CSV level.
- Some attack categories have limited source-file representation.
- The risk score is a heuristic prioritization mechanism, not a calibrated probability of compromise.
- Results on this benchmark do not establish production performance against all real-world IoT attacks.

## Code Availability

Source code and experimental implementation:

https://github.com/ishapageni/iot-hybrid-intrusion-detection

## License

This project is released under the MIT License.
