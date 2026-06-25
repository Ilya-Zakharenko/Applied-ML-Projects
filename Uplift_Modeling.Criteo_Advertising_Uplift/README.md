# <center> **PROJECT: Uplift Modeling**  
Criteo Advertising Campaign Optimization

This project focuses on selecting the best uplift modeling approach to maximize the effectiveness of advertising campaigns for a French advertising agency (Criteo).

---

### **Description**

Uplift modeling aims to predict the **incremental effect** of a treatment (in this case, showing an advertisement) on a user's behavior. The goal is to identify users who are most likely to respond positively to the ad (high uplift), thereby improving ROI and campaign efficiency.

We compare several popular uplift modeling strategies:
- S-Learner
- T-Learner  
- X-Learner
- R-Learner
- Custom Uplift Random Forest

The analysis is performed on the large-scale **Criteo Uplift Modeling Dataset** (25+ million rows).

---

### **Dataset**

- **Name**: Criteo Uplift Modeling Dataset
- **Size**: ~25.3 million rows, 459 MB (compressed)
- **Features**: 11 anonymized dense features (`f0`–`f11`)
- **Key columns**:
  - `treatment` — whether the user was exposed to advertising (1 = treated, 0 = control)
  - `visit` — whether the user visited the site
  - `conversion` — whether a conversion occurred
  - `exposure` — actual exposure to treatment
- **Paper**: “A Large Scale Benchmark for Uplift Modeling” (AdKDD 2018)

---

### **Objectives**

- Prepare and explore the Criteo uplift dataset
- Implement classic and advanced uplift modeling approaches
- Evaluate models using Qini curves and Qini AUC metric
- Determine which model maximizes ROI by identifying high-uplift users
- Provide practical recommendations for advertising campaign targeting

---

### **Models Implemented**

- **S-Learner** — Single model with treatment as a feature
- **T-Learner** — Two separate models (treated and control)
- **X-Learner** — Two-stage approach focused on uplift estimation
- **R-Learner** — Residual-based approach
- **Custom Uplift Random Forest** — Specialized tree-based uplift model

All models are based on `RandomForestClassifier` / `RandomForestRegressor`.

---

### **Key Results**

| Model                  | Qini AUC   | Recommendation                          |
|------------------------|------------|-----------------------------------------|
| X-Learner              | **0.1751** | Best performer — maximizes ROI          |
| R-Learner              | ~0.17      | Strong alternative                      |
| Uplift Random Forest   | ~0.17      | Strong alternative                      |
| T-Learner              | 0.0639     | Not recommended                         |
| S-Learner              | 0.0360     | Not recommended                         |

**Conclusion**:  
The **X-Learner** shows the best performance and is recommended for production use when the advertising budget is limited and the goal is to target users with the highest predicted uplift.

---

### **Used Tools & Libraries**

- `Python`
- `Pandas`, `NumPy` — data processing
- `scikit-learn` — base models (Random Forest)
- `causalml` or custom implementation — uplift modeling techniques
- `matplotlib`, `seaborn`, `plotly` — visualization (Qini curves, uplift distributions)
- `sklearn` metrics and custom Qini score calculation

---

### **Project Structure**

- `data/` — dataset (or download instructions)
- `notebooks/` — main analysis notebook
- `src/` — custom uplift model implementations
- `figures/` — Qini curves, uplift distributions, and comparison plots
- `requirements.txt` — project dependencies

---