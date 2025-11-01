# 🧠 Neural Network Regression with WEKA

### Author  
**Konstantinos Vasiladiotis (AM: 1088094)**  

---

## 📘 Project Overview  

This project was developed as part of the **Computational Intelligence course**.  
It focuses on training a **Multilayer Perceptron (MLP)** neural network in **WEKA** to predict the **`date_min`** attribute of an inscription dataset using both numerical and textual features.

The project combines **Python preprocessing** (for text transformation and data preparation) with **WEKA-based training and evaluation**, demonstrating the full pipeline from data cleaning to neural network optimization.

---

## ⚙️ Tools & Technologies  

| Category | Tools |
|-----------|--------|
| Data Preprocessing | Python, Pandas, TF-IDF Vectorizer |
| Machine Learning | WEKA (Multilayer Perceptron) |
| Validation | 5-Fold Cross Validation |
| Evaluation Metrics | RMSE, Error per Epoch |

---

## 🧩 Dataset Description  

The dataset includes the following attributes:  
`id`, `text`, `date_min`, `date_max`, `date_circa`, and `region_sub_id`.  

Among these, the `text` field required natural language preprocessing and transformation into numerical form.

### Preprocessing Steps:
1. **Text Vectorization:**  
   Applied **TF-IDF encoding** to represent the text field as numerical vectors.  
   Limited vocabulary size using `max_features=1000`.  
2. **Dimensionality Adjustment:**  
   Kept the **maximum TF-IDF value per text record** to ensure a valid ARFF format for WEKA.  
3. **ARFF File Generation:**  
   All attributes were converted to numeric type for WEKA compatibility.  
4. **Normalization:**  
   - Input attributes normalized to range [0, 1].  
   - Experiments were conducted with both normalized and non-normalized output (`date_min`).  

---

## 🧮 Neural Network Architecture  

- **Model:** Multilayer Perceptron (MLP)  
- **Algorithm:** Backpropagation  
- **Learning Rate (η):** 0.001  
- **Momentum (m):** Tuned between 0.2 – 0.6  
- **Hidden Layers:** 1 to 3  
- **Activation Function:** Sigmoid (default in WEKA)  

### Key Experiments:

| Configuration | Hidden Neurons | RMSE (Years) |
|----------------|----------------|---------------|
| 1 Hidden Layer | 1 | 129.02 |
| 1 Hidden Layer | 3 | **127.91** ✅ |
| 1 Hidden Layer | 7 | 133.46 |
| 2 Hidden Layers (2-1) | 259.82 |
| 3 Hidden Layers (2-2-2) | 259.85 |

➡️ The best configuration achieved **RMSE = 127.9 years** with **1 hidden layer and 3 neurons**.

---

## 🔬 Training & Evaluation  

- **Validation:** 5-Fold Cross Validation (automated by WEKA).  
- **Criterion:** RMSE (Root Mean Square Error) measured in years relative to `date_min`.  
- **Early Stopping:** Observed by tracking error per epoch — learning stabilized after ~360 epochs.  

| Epoch | Error per Epoch |
|--------|-----------------|
| 124 | 0.02219 |
| 235 | 0.02084 |
| 360 | 0.01991 |
| 500 | 0.01940 |

---

## 📈 Parameter Tuning Results  

| Learning Rate (η) | Momentum (m) | RMSE |
|--------------------|--------------|------|
| 0.001 | 0.2 | 127.91 |
| 0.001 | 0.6 | **126.30** ✅ |
| 0.05 | 0.6 | 131.99 |
| 0.1 | 0.6 | 132.38 |

📊 **Conclusion:** A small learning rate (0.001) combined with moderate momentum (0.6) yielded the best convergence and generalization.

---

## 🧠 Insights & Conclusions  

- One hidden layer with 3 neurons provided the best performance.  
- Adding more layers increased complexity but not accuracy.  
- Sigmoid activation was suitable for normalization and non-linearity.  
- Momentum improved convergence speed and stability.  
- The model reached a stable generalization point after 5-fold validation with RMSE ≈ 127 years.  

---

## 🧩 Repository Contents  

```
├── NEURAL.py               # Python preprocessing script
├── iphi2802.csv            # Original dataset
├── processed_data.arff      # Generated ARFF file for WEKA
├── results/                 # Output logs and WEKA results
└── README.md
```

---

## 🔗 GitHub Repository  

[➡️ Visit Repository](https://github.com/kostisvass/NEURAL_NETWORKS_PART_A)

---

## 🪪 License  
This project is for **educational purposes only**.  
All rights reserved © 2025 – *University of Patras, Computational Intelligence Course.*
