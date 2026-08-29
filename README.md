# 🔐 Data Quality Impact on SQL Injection Detection
### Comparative Deep Learning Study Using CNN, LSTM & Transformer-Based Models

An experimental study investigating the use of **deep learning for SQL injection detection** and, more importantly, examining how **data quality issues can affect machine-learning model performance**.

The project compares **Convolutional Neural Networks (CNNs), Long Short-Term Memory networks (LSTMs), and Transformer-based models**, while introducing data-quality problems such as missing values and noise to study model robustness.

## 📌 Project Overview

SQL injection is a major web-application security threat in which attackers manipulate SQL queries to access, modify, or compromise database systems.

Traditional rule-based and pattern-matching approaches can struggle with modified or previously unseen attack patterns. This project explores whether deep-learning models can effectively distinguish between **malicious and legitimate SQL queries**, while also investigating an often-overlooked factor: **the quality of the data used to train these models**.

The study was designed around two main questions:

1. **How effectively can CNN, LSTM, and Transformer-based models detect SQL injection attacks?**
2. **How does degraded data quality influence model performance?**

The dataset contains approximately **30,900 SQL queries**, categorized as malicious or normal.

---

## 📊 Key Results

The comparative experiments produced the following reported results:

| Model    |   Accuracy |  Precision |     Recall |   F1-Score |
| -------- | ---------: | ---------: | ---------: | ---------: |
| **CNN**  | **99.58%** | **99.87%** |     99.00% | **99.43%** |
| **LSTM** | **99.37%** |     99.21% | **99.08%** |     99.15% |
| **BERT** |     71.28% |     69.25% | **99.00%** |     82.15% |

### Key Findings

* 🥇 **CNN** achieved the strongest overall reported performance with **99.58% accuracy** and **99.43% F1-score**.
* 🥈 **LSTM** achieved similarly strong performance with **99.37% accuracy** and **99.15% F1-score**.
* 🔎 **BERT** achieved **99.00% recall**, but its accuracy and precision were substantially lower in this experimental setup.
* 🧪 Data-quality experiments demonstrated that missing values and noise can significantly affect model behavior.
* 🧹 Appropriate preprocessing and data-quality handling were therefore an important part of the overall detection pipeline.

The results illustrate that model architecture and data quality both play important roles in the performance of AI-based SQL injection detection systems.

---

## 🎯 Objectives

* Develop and evaluate a CNN-based SQL injection detection model.
* Develop and evaluate an LSTM-based SQL injection detection model.
* Investigate Transformer-based approaches using BERT-family models.
* Compare model performance using standard classification metrics.
* Investigate the effect of missing values and noise on model performance.
* Apply preprocessing techniques to improve data quality.
* Analyze the strengths and limitations of different deep-learning approaches.
* Provide practical insights into the importance of data quality in AI-based cybersecurity systems.

---

## 🧪 Research Methodology

The project followed an experimental workflow consisting of:

```text
Raw SQL Query Dataset
        │
        ▼
Data Inspection & Cleaning
        │
        ▼
Exploratory Data Analysis
        │
        ├── Word Cloud Analysis
        └── Frequency Analysis
        │
        ▼
Text Preprocessing
        │
        ├── Tokenization
        └── Sequence Padding
        │
        ▼
Model Development
        │
        ├── CNN
        ├── LSTM
        └── Transformer / BERT
        │
        ▼
Model Evaluation
        │
        ├── Accuracy
        ├── Precision
        ├── Recall
        └── F1-Score
        │
        ▼
Data Quality Experiments
        │
        ├── Missing Values
        └── Noise / Inconsistencies
        │
        ▼
Comparative Analysis
```

The research design used separate training/testing procedures and standard evaluation metrics to compare the models and investigate robustness under different data-quality conditions.

---

# 📊 Dataset

The project uses a dataset of approximately **30,900 SQL queries**, containing both malicious and normal SQL queries.

The dataset contains two primary fields:

| Field | Description |
|---|---|
| `Query` | SQL query text |
| `Label` | Classification label indicating the query category |

The prototype notebook contains:

- **19,537 normal queries**
- **11,382 malicious queries**
- **30,919 total queries**

The dataset was obtained from an external GitHub source and is **not included in this repository**.

### Dataset Availability

The original dataset source should be obtained from the source repository used during the research.

> **Note:** The original dataset URL is intentionally not hard-coded here until the exact source repository is verified. This avoids pointing users to an incorrect or unrelated dataset.

### Data Distribution

The dataset contains both legitimate and malicious SQL queries, providing the binary classification basis for the SQL injection detection experiments.

---

# 🔎 Exploratory Data Analysis

Before model training, the project investigated the characteristics of malicious and normal SQL queries.

### Word Cloud Analysis

Word clouds were generated separately for:

* Malicious SQL queries
* Normal SQL queries

The analysis was also repeated after introducing data-quality problems to observe how the distribution of query terms changed.

The research report documents word-cloud analysis both before and after introducing missing values and noise.

### Frequency Analysis

The project also examined frequently occurring words and patterns within malicious queries to identify potentially informative characteristics of SQL injection attempts.

---

# 🧹 Data Preprocessing

The text-processing pipeline included:

* Data inspection
* Handling missing/inconsistent data
* Text preparation
* Tokenization
* Sequence conversion
* Padding sequences to a consistent length

In the prototype implementation, SQL queries were tokenized and padded to a sequence length of **100** before being passed to the neural-network model.

For Transformer-based experiments, model-specific tokenization was used.

---

# 🧠 Models

## 1. Convolutional Neural Network — CNN

A CNN architecture was developed for detecting patterns within tokenized SQL queries.

The model used:

* Embedding layer
* Convolutional layers
* Pooling
* Fully connected layers
* Classification output

The prototype notebook contains the initial CNN implementation, including tokenization, sequence padding, model construction, training, and evaluation.

### Reported Performance

| Metric    |        CNN |
| --------- | ---------: |
| Accuracy  | **99.58%** |
| Precision | **99.87%** |
| Recall    | **99.00%** |
| F1-Score  | **99.43%** |

The research report identifies CNN as the strongest overall performer among the evaluated models on the reported metrics.

---

## 2. Long Short-Term Memory — LSTM

An LSTM-based model was developed to capture sequential relationships within SQL query representations.

The architecture included:

* Embedding layer
* LSTM layer
* Dense classification layers

The LSTM model was trained and evaluated using the same general experimental framework as the CNN model.

### Reported Performance

| Metric    |       LSTM |
| --------- | ---------: |
| Accuracy  | **99.37%** |
| Precision | **99.21%** |
| Recall    | **99.08%** |
| F1-Score  | **99.15%** |

The LSTM achieved performance close to the CNN while providing a different approach to modeling sequential query information.

---

## 3. Transformer-Based Model — BERT Family

The project also investigated Transformer-based approaches using pretrained language models.

The Transformer pipeline involved:

* Transformer-specific tokenization
* Pretrained language-model architecture
* Fine-tuning for SQL-query classification
* Classification-report analysis

The research process encountered dependency and training-time challenges. The implementation was moved to a TensorFlow-based workflow, and **DistilBERT** was used to reduce the training time associated with the Transformer experiment.

### Reported Performance

| Metric    |       BERT |
| --------- | ---------: |
| Accuracy  |     71.28% |
| Precision |     69.25% |
| Recall    | **99.00%** |
| F1-Score  |     82.15% |

The result illustrates an important aspect of the experiment: a more complex Transformer architecture does not automatically produce the best result for every dataset or experimental configuration.

---

# 📈 Model Comparison

### Overall reported results

| Model    |   Accuracy |  Precision |     Recall |   F1-Score |
| -------- | ---------: | ---------: | ---------: | ---------: |
| **CNN**  | **99.58%** | **99.87%** |     99.00% | **99.43%** |
| **LSTM** | **99.37%** |     99.21% | **99.08%** |     99.15% |
| **BERT** |     71.28% |     69.25% | **99.00%** |     82.15% |

Based on the reported evaluation, CNN produced the strongest overall combination of accuracy, precision, and F1-score, while LSTM produced similarly strong results. BERT achieved very high recall but substantially lower accuracy and precision in this experimental setup.

---

# 🧪 Data Quality Investigation

A central component of this project was investigating what happens when the quality of the training data is intentionally degraded.

The dataset was modified by introducing:

* Missing values
* Noise
* Inconsistencies

The objective was to simulate imperfect real-world data and observe how model predictions changed.

The research report specifically documents experiments involving CNN and LSTM under degraded data conditions.

### Key Finding

The experiments demonstrated that **data quality can have a substantial effect on machine-learning performance**.

In particular, the project encountered zero-accuracy behavior for CNN/LSTM experiments when missing values were introduced without appropriate handling. Preprocessing and missing-value handling were subsequently applied to address the problem.

This reinforced one of the central conclusions of the project:

> **Model performance depends not only on model architecture, but also on the quality and preparation of the underlying data.**

---

# 🚀 How to Run

## 1. Clone the Repository


git clone https://github.com/sherazkhan-ai/data-quality-impact-on-sql-injection-detection.git
cd data-quality-impact-on-sql-injection-detection

---

# 🧰 Technologies & Tools

### Programming

* Python

### Machine Learning / Deep Learning

* TensorFlow
* Keras
* Scikit-learn
* CNN
* LSTM

### NLP / Transformers

* Hugging Face Transformers
* BERT
* DistilBERT

### Data Analysis

* Pandas
* Matplotlib
* Seaborn
* WordCloud

### Development

* Jupyter Notebook

The research implementation was developed using Python with TensorFlow, Keras, and Hugging Face Transformers.

---

# 📁 Repository Structure

```text
data-quality-impact-on-sql-injection-detection/
│
├── README.md
│
├── Research_Prototype.ipynb
│
├── notebooks/
│   ├── ...
│
├── figures/
│   ├── ...
│
├── results/
│   ├── ...
│
├── requirements.txt
│
└── .gitignore
```

### Current implementation

`Research_Prototype.ipynb` represents the **initial research prototype** used during development.

The prototype currently demonstrates the early stages of the project, including dataset inspection, exploratory analysis, tokenization, padding, and CNN implementation.

The complete CNN, LSTM, and Transformer implementations belong to the broader research project and can be added to this repository when the remaining implementation files are available.

---

# 🔬 Research Findings

The project produced several important observations:

### 1. CNN performed strongly

CNN achieved the highest reported overall performance, reaching **99.58% accuracy** and **99.43% F1-score**.

### 2. LSTM was also highly effective

LSTM achieved **99.37% accuracy** and **99.15% F1-score**, showing performance close to CNN.

### 3. Transformer performance depended heavily on configuration

The BERT experiment achieved very high recall but lower overall accuracy and precision than CNN and LSTM. This highlighted the importance of model configuration, fine-tuning, and dataset characteristics.

### 4. Data quality matters

The data-quality experiments demonstrated that missing values and noisy/inconsistent data can severely affect model behavior, emphasizing the importance of robust preprocessing and data handling.

### 5. Model complexity does not guarantee better performance

One of the practical lessons from the comparison was that a more sophisticated architecture is not automatically the best-performing solution for a particular dataset and task.

---

# ⚠️ Limitations

The project has several limitations that provide opportunities for future development:

* The dataset could be expanded with more diverse SQL injection techniques.
* Additional datasets could be used to evaluate generalization.
* Transformer models could be further fine-tuned.
* Hyperparameter optimization could be explored more extensively.
* Ensemble or hybrid architectures could be investigated.
* Real-time SQL injection detection could be developed.
* Deployment in a practical web-security environment remains future work.

These areas are also identified in the research report's proposed future work.

---

# 🚀 Future Work

Potential extensions include:

* 🔬 Fine-tuning larger and more suitable Transformer models.
* 🤝 Combining CNN, LSTM, and Transformer approaches.
* 📚 Expanding the dataset with more diverse SQL queries.
* 🧪 Performing systematic data-augmentation experiments.
* ⚙️ Optimizing model hyperparameters.
* 🌐 Developing a real-time SQL injection detection API.
* 🛡️ Integrating the model into web-application security systems.
* 📊 Evaluating performance on completely independent datasets.

---

# 📚 Research Context

This repository represents the implementation and experimentation associated with an academic research project focused on **deep-learning-based SQL injection detection and the impact of data quality on model performance**.

The project was completed as part of my Computer Science studies.

**Author:** Sheraz Khan

**Field:** Computer Science / Artificial Intelligence / Machine Learning / Cybersecurity

---

## ⭐ Key Takeaway

This project explores an important principle in applied AI:

> **A strong model cannot compensate indefinitely for poor-quality data.**

By comparing CNN, LSTM, and Transformer-based approaches under both cleaner and degraded data conditions, the project examines not only *which model performs best*, but also *how the quality of the information supplied to the model influences its behavior*.

---

## 📌 Status

🟡 **Research project — implementation being organized for public release**

The repository currently contains the initial research prototype. Additional finalized implementation files, experimental outputs, and visualizations can be added as they become available.

---

## 👤 Author

**Sheraz Khan**

Master of Computer Science — University of Engineering & Technology, Peshawar

Bachelor of Computer Science — Abdul Wali Khan University Mardan

---

⭐ If you find this project interesting, feel free to explore the repository and follow my work in **AI, Machine Learning, Deep Learning, NLP, and AI-driven cybersecurity**.
