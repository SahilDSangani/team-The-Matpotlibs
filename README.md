# **Team Matplotlibs: WAR & PCA — Predicting Player Value in Baseball**

## **Project Overview**

Major League Baseball teams rely heavily on analytics to estimate player value — and “WAR” (Wins Above Replacement) is one of the most important summary statistics used today.

Our project builds a model that predicts a player’s **next-season WAR** based on their **current-season performance metrics**, using a combination of **PCA** and **machine learning models**.

This can help:

* Baseball managers and executives make informed roster or trade decisions
* Analysts identify under- or over-valued players
* Fans understand which players are likely to perform well next season

---

## **Team Members**

* **Sahil Sangani** — Modeling, Slides — [sahildsangani@gmail.com](mailto:sahildsangani@gmail.com)
* **Addison Naylor** — Modeling, Slides — [anaylortm@gmail.com](mailto:anaylortm@gmail.com)
* **Eleni Bovalis** — README, Variable Dictionary, Slides — [bovalis2@illinois.edu](mailto:bovalis2@illinois.edu)
* **Annika Luthe** — Variable Analysis, Slides — [annika.k@luthe.org](mailto:annika.k@luthe.org)
* **Tanvee Athavale** — Variable Dictionary, Slides — [tan.fll.vale@gmail.com](mailto:tan.fll.vale@gmail.com)

---

## **Data Description**

* **Source:** [https://www.baseball-reference.com](https://www.baseball-reference.com)
* **Training Data:** 2010–2023
* **Testing Data:** 2024–2025
* **Size:** ~13,000 player-seasons
* After filtering unnecessary variables, we found **1206 missing values**, which we dropped due to the large dataset size.

### **Key Variables (Examples)**

| Variable | Description            | Type    |
| -------- | ---------------------- | ------- |
| WAR      | Wins Above Replacement | Float   |
| R        | Runs Scored            | Integer |
| H        | Hits                   | Integer |
| 2B       | Doubles                | Integer |
| RBI      | Runs Batted In         | Integer |
| BB       | Walks                  | Integer |
| PA       | Plate Appearances      | Integer |
| AB       | At Bats                | Integer |
| HR       | Home Runs              | Integer |
| G        | Games Played           | Integer |

(Full variable dictionary available in the repository.)

---

## **Methodology**

Our workflow included:

### **1. Exploratory Data Analysis**

* Checking correlations
* Identifying multicollinearity
* Filtering out irrelevant variables
* Handling missing data

### **2. Dimensionality Reduction (PCA)**

* `n_components = 0.90` retained **90% of variance**
* Reduced ~34 variables → **14 principal components**
* Helped reduce overfitting and speed up model training

### **3. Machine Learning Models Tested**

* Linear Regression
* K-Nearest Neighbors
* Decision Tree
* Random Forest
* Gradient Boosting (Histogram-Based)

### **4. Best Model**

**Histogram-Based Gradient Boosting Regressor**

| Metric        | Score     |
| ------------- | --------- |
| 5-Fold CV MAE | **0.807** |
| Test MAE      | **0.931** |
| Test RMSE     | **1.368** |

---

## **Key Findings**

* PCA significantly improved model stability by reducing multicollinearity.
* The Gradient Boosting model performed best, with **MAE ≈ 0.8**, meaning predictions are typically within ±0.8 WAR of the true value.
* The model **can reliably estimate if a player is valuable**, but
  **should not be used for high-stakes decisions** (e.g., cutting or signing players solely off the prediction).
* Stronger predictors included power-related and playing-time variables (HR, PA, OPS components).

---

## **Future Work**

* Extend model to **pitchers**, who have different statistical structures
* Incorporate **college**, **minor league**, or **Statcast** data
* Predict WAR **multiple seasons into the future**
* Add **time series analysis** for player career trajectories

---

## **Acknowledgments**

* **Project Lead:** Lara T
* **Data:** Baseball Reference
* **Tools:** Python, Scikit-Learn, PCA, Pandas, PyBaseball, VSCode, GitHub, Google Slides
