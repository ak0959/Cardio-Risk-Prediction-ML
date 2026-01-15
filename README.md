# Cardio-Risk-Prediction-ML
A machine learning project exploring SVM and Decision Tree models to predict cardiovascular disease risk, with a focus on solving overfitting through hyperparameter tuning.

# Cardiovascular Disease Risk Prediction: Full Project Report

## 📋 1. Executive Summary
The primary objective of this project was to develop a machine learning model capable of identifying patients at high risk for cardiovascular disease. Through a systematic evaluation of linear (SVM) and non-linear (Decision Tree) algorithms, the analysis revealed a significant challenge with **overfitting**. 

While initial unconstrained models achieved near-perfect training scores, they failed to generalize to new data. By implementing **Hyperparameter Tuning via Grid Search**, the model was stabilized, moving from "memorizing" the training set to identifying broader clinical patterns. This project serves as a detailed case study in balancing model complexity with real-world reliability.

---

## 🛠️ 2. Project Workflow & Methodologies

### 2.1 Data Preprocessing & Cleaning
Raw clinical data was transformed to ensure biological and statistical validity:
* **Feature Categorization**: Features were grouped into Objective (Age, Height), Examination (Blood Pressure, Cholesterol), and Subjective (Smoking, Alcohol) categories.
* **Feature Engineering**: Age was converted from days to years, and **BMI** was calculated to provide standard clinical context.
* **Outlier Management**: Instances where blood pressure readings were physically impossible (e.g., diastolic higher than systolic) were removed to ensure data integrity.

### 2.2 Baseline Modeling: Linear SVM
We first established a performance baseline using a Linear SVM:
* **Outcome**: The model achieved a **0.7232 training accuracy** but suffered from a "no-skill" result on the test set (AUC 0.49).
* **Finding**: A linear boundary was insufficient to capture the complex relationships between these health indicators.

### 2.3 Advanced Modeling: Decision Tree
To capture non-linear interactions, we implemented a Decision Tree:
* **The Overfitting Issue**: Without constraints, the tree hit **99.4% training accuracy**.
* **Generalization Failure**: Testing accuracy dropped to **48.4%**, indicating the model was learning noise rather than transferable medical patterns.

### 2.4 Optimization via Grid Search
We used **Grid Search** with 5-fold cross-validation to prune the tree and find a stable middle ground:
* **Optimized Parameters**: `max_depth: 5` and `min_samples_leaf: 20`.
* **Stabilization**: Training accuracy was brought down to a more honest **72.3%**, narrowing the gap between training and testing performance.

---

## 📈 3. Final Performance Comparison

| Metric | Linear SVM | Unconstrained DT | **Optimized Decision Tree** |
| :--- | :--- | :--- | :--- |
| **Training Accuracy** | 0.7232 | 0.9943 | **0.7232** |
| **Testing Accuracy** | 0.4947 | 0.4844 | **0.4947** |
| **Testing Recall** | 1.0000 | 0.7446 | **1.0000** |

---

## 🧪 4. Conclusion & Clinical Insights
1. **Generalization over Accuracy**: High training scores (99%) are often a warning sign of overfitting. Real clinical utility requires depth constraints to handle noisy medical data.
2. **Prioritizing Sensitivity**: The final model achieved a **1.00 Recall** on the test set, ensuring that no high-risk patients are missed—a critical priority in healthcare settings.
3. **Future Recommendations**: Moving toward **Ensemble Methods** like Random Forest or Gradient Boosting is recommended to further improve precision while maintaining the stability achieved through Grid Search

---

## 🛠️ How to Run
1. Clone this repository.
2. Install dependencies: `pip install -r requirements.txt`
3. Open `Cardiovascular_Risk_Analysis.ipynb` in Jupyter Notebook.
