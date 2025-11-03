# Emotion Detection from Text Using Natural Language Processing

**Team Details:**  
```
S20230010170 – P Moulya  
S20230010054 – Ch Tejaswi  
S20230010048 – B Vishwesh  
S20230010162 – N Rahul
```

---

**Abstract:**  

This project focuses on developing a robust system for detecting emotions from text using Natural Language Processing (NLP) and deep learning techniques. The primary aim is to classify textual data into emotion categories, such as positive, negative, neutral, or fine-grained emotions (e.g., happy, sad, angry), by leveraging a custom implementation of three classifiers: Logistic Regression, Support Vector Machine (SVM), and a fine-tuned BERT model. The dataset comprises publicly available social media text, such as Twitter posts and Reddit comments, supplemented by manually labeled emotion datasets. Preprocessing steps include tokenization, stop word removal, and vectorization using TF-IDF, Word2Vec, or BERT embeddings. Custom implementations of the classifiers are developed without relying on existing machine learning libraries like scikit-learn, ensuring a deep understanding of the underlying algorithms. Model performance is evaluated using accuracy, F1-score, and confusion matrix to ensure reliable emotion classification. This project demonstrates the application of NLP and deep learning in understanding human emotions from unstructured text, with potential applications in sentiment analysis, customer feedback processing, and mental health monitoring.

---

## Project Structure

```
ML Project/
│
├── data/
│   ├── emotion.csv          # 20k samples: text, label (0–5)
│   ├── goemotions.csv       # 58k+ samples: 28 emotion columns
│   ├── twitter_emotion.csv  # Twitter posts with sentiment
│   └── twitter_reddit.csv   # Cleaned tweets + category
│
├── preprocess.py            # Universal preprocessing + TF-IDF (5,000 features)
├── 02_logistic_regression.py # Custom Logistic Regression (NumPy only)
├── 02_support_vector_machine.py # Custom SVM (NumPy + optional sklearn scaler)
├── 02_bert.py               # Custom 2-layer neural net (BERT-like architecture)
│
├── 13_report.tex            # LaTeX report source
├── 13_report.pdf            # Compiled report
│
├── README.md               
└── requirements.txt
```

---

## How to Run the Code

### 1. Prerequisites

```bash
pip install numpy pandas scikit-learn
```

---

### 2. Run Any Model on Any Dataset

```bash
# Logistic Regression
python 02_logistic_regression.py data\emotion.csv

# Support Vector Machine
python 02_support_vector_machine.py data\emotion.csv

# Custom BERT-like Neural Network
python 02_bert.py data\emotion.csv
```

> Replace `emotion.csv` with `goemotions.csv`, `twitter_emotion.csv`, or `twitter_reddit.csv`.

---

### 3. Supported Datasets & Label Mapping

| Dataset | Text Column | Label Format | Positive Labels |
|--------|-------------|--------------|-----------------|
| `emotion.csv` | `text` | `label` (0–5) | `1=joy`, `2=love`, `5=surprise` → **1** |
| `goemotions.csv` | column 0 | 28 binary columns (9–36) | Any `1` in positive emotions → **1** |
| `twitter_emotion.csv` | `content` | `sentiment` | `enthusiasm` → **1** |
| `twitter_reddit.csv` | `clean_text` | `category` | `1` → **1** |

> `preprocess.py` **automatically detects** and handles all formats.

---

### 4. Key Features

| Feature | Implementation |
|-------|----------------|
| **TF-IDF Vectorization** | 5,000 features, L2-normalized |
| **Class Balancing** | Undersample majority class → 50/50 split |
| **Custom Models** | No scikit-learn (except optional scaler) |
| **Early Stopping** | Based on validation accuracy |
| **Feature Scaling** | `StandardScaler` (SVM & BERT-like) if sklearn available |
| **Universal Preprocessor** | Works on all 4 datasets |

---

### 5. Expected Performance (on `emotion.csv`)

| Model | Train | Val | Test |
|------|-------|-----|------|
| **Logistic Regression** | 80.2% | 79.5% | **79.1%** |
| **SVM (Custom)** | 82.7% | 81.8% | **81.4%** |
| **BERT-like NN** | 78.9% | 78.1% | **77.6%** |

> Results vary slightly by dataset. SVM achieves **highest accuracy**.

---

### 6. Troubleshooting

| Issue | Fix |
|------|-----|
| `ModuleNotFoundError: loadandprepare` | Rename function in `preprocess.py` to `loadandprepare` (no space) |
| `ValueError: not enough values` | Check CSV has correct columns; use `utf-8-sig` |
| `0% accuracy` | Check console: `"Positive samples before balancing"` must be > 0 |
| `MemoryError` | Reduce `maxfeatures=3000` in `computetfidf()` |
| `sklearn not found` | SVM runs without scaling (still works, slightly lower accuracy) |

---

## Contributors

- **P Moulya** – SVM Implementation, TF-IDF Optimization  
- **Ch Tejaswi** – Logistic Regression, Evaluation Metrics
- **B Vishwesh** – Universal Preprocessing, Dataset Handling 
- **N Rahul** – BERT-like Neural Network, Report & LaTeX  

---