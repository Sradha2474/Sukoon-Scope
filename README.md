# 🎓 Student Stress Prediction Model

![Python](https://img.shields.io/badge/Python-3.8%2B-blue)
![Library](https://img.shields.io/badge/Library-Scikit_Learn-orange)
![Status](https://img.shields.io/badge/Status-Analaysis_Complete-green)
![License](https://img.shields.io/badge/License-MIT-lightgrey)

## 📖 Project Overview
Mental health in academic settings is a critical concern. This project develops a machine learning solution to predict student stress levels by analyzing academic, social, and personal habits. 

**The Goal:** To build a predictive model that can identify students at risk of high stress early on, enabling educational institutions to provide timely support and resources.

---

## 📊 Data Overview
Dataset: `enhanced_student_habits_performance_dataset.csv`  
Scale: 80,000 entries | 31 columns

The dataset captures a 360-degree view of student life:

| Category | Key Variables |
| :--- | :--- |
| Demographics | Age, Gender, Major |
| 📚 Study Habits | Study hours/day, GPA, Time management, Study environment |
| 📱 Social Habits | Social media usage, Netflix hours, Extracurriculars |
| ❤️ Well-being | Sleep hours, Diet quality, Mental health rating, Stress level |
| 📈 Performance | Attendance %, Exam score |
| 🏠 Socio-economic | Parental support, Income range, Internet quality |

---

## ⚙️ Methodology

### 1. Data Preprocessing
* **Cleaning:** Removal of missing values (`NaN`) and duplicates to ensure data integrity.
* **Optimization:** Dropped non-predictive identifiers (e.g., `student_id`).
* **Encoding:** Applied One-Hot Encoding to categorical variables (with `drop_first=True` to prevent multicollinearity).
* **Splitting:** 80/20 Train-Test split with **Stratification** to maintain balanced stress classes.

### 2. Exploratory Data Analysis (EDA)
We utilized statistical visualization to uncover key trends:
* **Distribution Analysis:** Visualized exam scores and stress levels using Count Plots.
* **Correlation:** Analyzed the relationship between screen time and academic performance using Box Plots.

### 3. Feature Engineering
To capture complex behavioral patterns, I engineered three custom features:

1.  `Study_Sleep_Interaction`
    * Logic: `Study Hours * Sleep Hours`  
    * Why:Captures the productivity balance. High study time is only effective if paired with adequate rest.

2.  `Social_Study_Ratio`
    * Logic: `Social Media Hours / (Study Hours + epsilon)`  
    * Why:Quantifies distraction levels. A high ratio indicates a potential lack of focus.

3.  `Total_Screen_Time`
    * Logic:`Social Media Hours + Netflix Hours`  
    * Why: Aggregates total recreational digital consumption to measure digital overload.

---

## 🧠 Model Development

* Algorithm:`RandomForestClassifier`
* Why Random Forest? Selected for its robustness against overfitting, ability to handle non-linear relationships, and built-in feature importance ranking.
* Hyperparameter Tuning: Optimized using **RandomizedSearchCV** (50 iterations, 3-fold CV) to find the best balance of `n_estimators`, `max_depth`, and split criteria.

---

## 🏆 Key Results

The model successfully identifies key drivers of student stress.

* **Top 3 Predictors:**
    1.  `attendance_percentage`: (Strongest correlation with stress/performance)
    2.  `Study_Sleep_Interaction`: (Proves the importance of balanced rest)
    3.  `Social_Study_Ratio`: (Highlights the impact of distractions)

* **Accuracy:** ~55.7% (Baseline)
    * *Note: While accuracy provides a baseline, the Feature Importance analysis provides the most actionable insights for intervention.*

---

## 💻 Installation & Usage

1.  **Clone the repository:**
    ```bash
    git clone [https://github.com/yourusername/student-stress-prediction.git](https://github.com/yourusername/student-stress-prediction.git)
    cd student-stress-prediction
    ```

2.  **Install dependencies:**
    ```bash
    pip install -r requirements.txt
    ```

3.  **Run the Analysis:**
    Open the Jupyter Notebook to explore the EDA and Model Training steps.
    ```bash
    jupyter notebook notebooks/02_Model_Training.ipynb
    ```

---

## 🚀 Future Roadmap

* **Model Improvement:** Experiment with XGBoost and Gradient Boosting for potentially higher accuracy.
* **Explainability:** Integrate SHAP (SHapley Additive exPlanations) to explain *why* a specific student is flagged as high risk.
* **Data Enrichment:** Incorporate physiological data (heart rate, sleep quality from wearables) for more precise predictions.

---

## 🤝 Contributing
Contributions, issues, and feature requests are welcome! Feel free to check the [issues page](https://github.com/yourusername/student-stress-prediction/issues).

---

**Author:** [Sradha Ram]  
**Contact:** [sradharam2474@gmail.com]
