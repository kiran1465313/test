# 🚦 AI Food Adulteration Detection Dashboard

## 🌍 Why This Project?

Food adulteration is a major threat to public health, industry reputation, and consumer trust. Early and accurate detection helps save lives, money, and brand value.

---

## 🤖 What Does This App Do?

- **Predicts risk** (Minor/Moderate/Severe) for any new food sample.
- **Interactive dashboard:** Visualizes food safety, category risk, recent alerts, and performance trends.
- **Live data upload:** Instantly analyzes any compatible dataset via CSV upload.
- **Views for all roles:** Executive KPIs, Analyst exploration, Regulator compliance, and Operations monitoring.

---

## 🛠️ Key Features

|           |               |
|-----------|:-------------:|
| 🌀 **AI Prediction** | Classifies new samples via trained ML models |
| 📈 **Live Visuals** | KPIs, trend lines, category heatmaps, alert feeds |
| 📂 **Easy Data Upload** | Drop in new CSVs—dashboard adapts automatically |
| 🎛️ **Role-Based Tabs** | Executive, Analyst, Regulator, Operations views |
| 🤝 **No-Code** | Streamlit UI—intuitive, accessible anywhere |

---

## 📦 Dataset Description

### Dataset Sources

- Structured food audit data, laboratory adulteration records, and regulatory agency test results.

### Schema & Field Descriptions

| Field             | Description                                            |
|-------------------|-------------------------------------------------------|
| product_name      | Name of the food product                              |
| brand             | Brand or manufacturer name                            |
| category          | Food category/type (e.g., Dairy, Meat, Bakery)        |
| adulterant        | Detected contaminant or adulterant                    |
| severity          | Model-assessed severity: Minor/Moderate/Severe        |
| health_risk       | Health risk assessed from test                        |
| detection_date    | Date the product was tested                           |
| month/year        | Detection month and year, extracted                   |

### Sample Rows

| product_name   | brand   | category | adulterant            | severity | health_risk | detection_date | month | year |
|:-------------- |:------- |:-------- |:--------------------- |:-------- |:----------- |:-------------- |:----- |:-----|
| Milk Powder X  | BrandY  | Dairy    | Melamine              | Severe   | High        | 2025-07-12     | 7     | 2025 |
| Energy Bar     | BrandZ  | Bakery   | Artificial sweeteners | Moderate | Medium      | 2025-06-05     | 6     | 2025 |
| Cold Drink A   | BrandX  | Beverages| Water                 | Minor    | Low         | 2025-06-13     | 6     | 2025 |

---

## 🧠 Model Training and Evaluation

### Preprocessing Steps

- One-hot encoding for categorical fields (category, adulterant, brand)
- Date conversion and `month`, `year` extraction
- Removal of ID/leakage columns
- Handling missing data

### Training Workflow

1. **Data split** into training/validation/test sets.
2. **Pipeline** combining preprocessing and model (Random Forest / XGBoost).
3. **Model selection** and hyperparameter tuning for optimal F1 score.
4. **Serialization** using joblib for deployment.

### Model Performance Metrics

- Validation Macro F1 Score: ~0.78
- Test Macro F1 Score: ~0.74
- Confusion matrices and detailed per-class performance
- Best accuracy: Identifying “Severe” and “Safe” cases

---

## 🖥️ App/Dashboard Features

### Role-Based Dashboards

- **Executive:** At-a-glance KPIs (percent safe, critical cases), trends, traffic-light status
- **Analyst:** Heatmaps (category vs. severity), top adulterants by type, bar charts
- **Regulator:** Compliance per category, violation logs, severity distribution
- **Operations:** Weekly/monthly test volumes, critical alerts, sample processing status

### Input Forms

- **Sidebar:** Predicts risk for any product scenario you enter, instantly
- **CSV Uploader:** Instantly switches dashboard to the newly uploaded data

### Visualizations

- Pie charts for safety breakdown
- Line charts for time trends
- Category–severity heatmaps
- Bar/stacked bar charts for adulterant distributions
- Real-time critical alert feeds

### What-If & Scenario Analysis

- Each prediction or CSV upload immediately refreshes every chart, KPI, and dashboard panel for efficient role-based decision-making.

---

## 🚀 How to Run the Project

### Requirements

- Python 3.8 or newer
- Packages: `streamlit`, `pandas`, `scikit-learn`, `xgboost`, `matplotlib`, `seaborn`, `joblib`, `pyngrok`
- Browser access

### Step-by-Step Instructions

**On Colab:**
1. Upload your CSV and model files.
2. Install dependencies:
  ```bash
!pip install streamlit pandas scikit-learn xgboost matplotlib seaborn joblib pyngrok --quiet
  ```
3. Write the app file:
  ```python
with open("app.py", "w") as f:
f.write(app_code)
  ```
4. Run Streamlit + pyngrok:
  ``` python
from pyngrok import ngrok
import threading, time, os
def run_streamlit(): os.system('streamlit run app.py --server.port 8501')
threading.Thread(target=run_streamlit).start(); time.sleep(5)
print("Public URL:", ngrok.connect(8501))
  ```
5. Open the displayed ngrok URL in your browser.

**Locally:**
1. Place your CSV/model in the same folder as `app.py`.
2. Install Python dependencies.
3. Launch:
    ```pyhon
    streamlit run app.py
    ```

4. Open http://localhost:8501 in your browser.

### Sample Data & Model

- `food_adulteration_data.csv`
- Model pipeline: `xgb_pipe.pkl`

---

## 🎉 Why Use This?

- **Instantly identify critical adulteration risks**
- **Role-specific analytics for every food safety stakeholder**
- **No coding required to update datasets, run predictions, or share insights**
- **Modern, visual, actionable analytics in a click**

---

*Made for safer food and smarter decisions, powered by AI and data.*
