# 👓 Predicting Myopia from Eye Measurements and Lifestyle Data

Machine Learning final project for the **MSc in Data Analytics for Engineering**.
🏆 **Winning team of the class competition**: our models achieved the best accuracy among all teams. <!-- TODO: add details when available (e.g. number of teams, final test accuracy) -->

**Team:** Patricia Urdiroz · [Luis Martín](https://github.com/luis-martin-b)

---

## 🎯 The problem

Using eye measurements, family history and lifestyle habits of university students, we predict four related labels:

| Task | Question | Classes |
|---|---|---|
| `M` | Is the student myopic? | Yes / No |
| `MM` | Is the student severely myopic? | Yes / No |
| `Combo` | No myopia, myopia or severe myopia? | C / M / MM |
| `DCombo` | Same as `Combo`, with myopia split into two types | C / M1 / M2 / MM |

The main challenge: **a very small dataset** (132 labelled students), with rare classes and some inconsistent labels.

## 🧭 Approach

1. **Data quality first:** detected and removed students with contradictory labels across tasks.
2. **Hold-out set** kept aside from the start to get an honest final evaluation.
3. **Exploratory analysis** of eye measurements, family history, lifestyle and sun exposure.
4. **Feature engineering** guided by the exploration, and **feature selection with Lasso**.
5. **Model comparison** (Logistic Regression, Random Forest, XGBoost) with stratified cross-validation, tuning the decision threshold per task.
6. **Overfitting / underfitting check** with error-vs-complexity curves.
7. **Final predictions** on the unlabelled test set.

## 📊 Results

| Task | Final model | Cross-validation | Hold-out | Baseline |
|---|---|---|---|---|
| `M` | Logistic regression | 0.804 | 0.742 | 0.645 |
| `MM` | Random forest | 0.964 | 1.000 | 0.935 |
| `Combo` | Derived from the `DCombo` model | 0.764 | 0.806 | 0.581 |
| `DCombo` | Logistic regression | 0.631 | 0.677 | 0.355 |

*Accuracy. Baseline = always predicting the most frequent class.*

**Key insights**
- **Eye length** (combined with curvature) is by far the strongest predictor; severe myopia is linked to eyes of 26 mm or longer.
- Family history and lifestyle add little once eye measurements are known.
- With so little data, **simple models perform as well as complex ones**.

## 📂 Repository contents

| File | Description |
|---|---|
| `Myopia_ML_Final_Project.ipynb` | Full analysis: code, explanations, figures and results (saved already executed) |
| `requirements.txt` | Python libraries and versions |

## 🔒 About the data

The dataset contains **health data** and is **not included** in this repository. The notebook is saved with all outputs, so the full analysis, figures and results can be read directly on GitHub.

## 🛠️ Tech stack

Python · pandas · scikit-learn · XGBoost · matplotlib · seaborn · Jupyter
