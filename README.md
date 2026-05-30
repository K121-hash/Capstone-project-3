# Employee Burnout Prediction Model

![Python](https://img.shields.io/badge/Python-3.7+-blue.svg)
![License](https://img.shields.io/badge/License-MIT-green.svg)
![Status](https://img.shields.io/badge/Status-Complete-brightgreen.svg)

## 📌 Project Overview

This capstone project develops a **machine learning predictive model to identify and prevent employee burnout** by analyzing employee behavioral and organizational data. The model predicts the burn rate of employees, enabling HR teams to intervene proactively and implement targeted wellness programs.

Employee burnout is a critical organizational challenge that impacts productivity, increases turnover, and reduces employee well-being. This data-driven solution provides organizations with actionable insights to detect at-risk employees early and take preventive measures.

---

## 🎯 Problem Statement

**The Challenge:**
Employee burnout is a widespread issue in today's competitive work environment, manifesting as:
- Physical, emotional, and mental exhaustion
- Reduced professional efficacy and engagement
- Decreased productivity and increased absenteeism
- Higher employee turnover rates and associated costs

**Why It Matters:**
- **Reduced Productivity:** Burned-out employees are less engaged and more prone to errors
- **Higher Turnover:** Significant recruitment and training costs
- **Increased Absenteeism:** Chronic stress leads to frequent sick days
- **Lower Team Morale:** Burnout spreads within teams, creating toxic work cultures
- **Poor Customer Service:** Disengaged employees negatively impact customer satisfaction and brand reputation

**The Solution:**
By leveraging predictive analytics, organizations can:
- Identify early warning signs of burnout
- Implement personalized interventions and wellness programs
- Make data-driven decisions about workplace policies
- Build trust through transparent, employee-centric approaches
- Save costs while improving employee well-being and organizational performance

---

## 🎯 Objectives

1. **Data Exploration & Analysis:** Understand employee data patterns and burnout indicators
2. **Data Preprocessing:** Handle missing values, outliers, and ensure data quality
3. **Feature Engineering:** Create meaningful features including tenure calculations
4. **Model Development:** Build and train multiple regression models
5. **Performance Evaluation:** Compare models and identify the best performer
6. **Actionable Insights:** Provide HR teams with data-driven recommendations
7. **Reproducibility:** Enable organizations to deploy the model in production environments

---

## 📊 Dataset Description

### Data Source
The dataset comprises employee records from a corporate organization, combining HR systems, employee surveys, and productivity metrics.

### Dataset Specifications

| Metric | Training Set | Test Set |
|--------|-------------|----------|
| **Number of Records** | 22,750 | 12,250 |
| **Total Features** | 9 | 8 |
| **Target Variable** | Burn Rate | (Missing) |
| **Date Range** | 2008-2020 | 2008-2020 |

### Feature Descriptions

| Feature | Type | Description | Range |
|---------|------|-------------|-------|
| **Employee ID** | String | Unique employee identifier | Encoded |
| **Date of Joining** | DateTime | Employee's joining date | 2008-2020 |
| **Gender** | Categorical | Employee gender | Male/Female |
| **Company Type** | Categorical | Organization type | Service/Product |
| **WFH Setup Available** | Categorical | Work from home availability | Yes/No |
| **Designation** | Numeric | Employee job level/rank | 0-5 |
| **Resource Allocation** | Numeric | Workload/resource assignment level | 1-10 |
| **Mental Fatigue Score** | Numeric | Psychological stress indicator | 0-10 |
| **Burn Rate** | Numeric (Target) | Employee burnout intensity | 0-1 |

### Data Characteristics

**Numerical Features Statistics:**
- **Designation:** Mean = 2.18, Range = [0, 5]
- **Resource Allocation:** Mean = 4.48, Range = [1, 10]
- **Mental Fatigue Score:** Mean = 5.73, Range = [0, 10]
- **Burn Rate:** Mean = 0.45, Range = [0, 1]

**Categorical Distribution:**
- **Gender:** 52.4% Female, 47.6% Male
- **Company Type:** 65.2% Service, 34.8% Product
- **WFH Setup:** 54.0% Available, 46.0% Not Available

### Data Limitations

1. **Missing Values (Training Set):**
   - Resource Allocation: 6.07% missing
   - Mental Fatigue Score: 9.31% missing
   - Burn Rate: 4.94% missing (target variable)

2. **Missing Values (Test Set):**
   - No missing values in test features
   - Target variable (Burn Rate) intentionally absent for prediction

3. **Imbalanced Features:** Some features show concentration in certain ranges, requiring normalization

---

## 🛠 Technology Stack

### Core Libraries
| Tool | Version | Purpose |
|------|---------|---------|
| **Python** | 3.7+ | Programming language |
| **Pandas** | Latest | Data manipulation and analysis |
| **NumPy** | Latest | Numerical computations |

### Visualization
| Tool | Purpose |
|------|---------|
| **Matplotlib** | Static visualizations and plots |
| **Seaborn** | Statistical data visualization |

### Machine Learning
| Tool | Purpose |
|------|---------|
| **Scikit-learn** | Machine learning models and preprocessing |
| **Linear Regression** | Baseline predictive model |
| **Random Forest** | Ensemble tree-based model |
| **Gradient Boosting** | Advanced ensemble learning model |

### Development Environment
| Tool | Purpose |
|------|---------|
| **Jupyter Notebook** | Interactive development and documentation |
| **Google Colab** | Cloud-based notebook execution |

---

## 📁 Project Structure

```
Capstone-project-3/
├── README.md                           # Project documentation (this file)
├── Capstone_project_3.ipynb.txt        # Main Jupyter Notebook with full analysis
│   ├── 1. Problem Definition & Context
│   ├── 2. Data Loading & Exploration
│   ├── 3. Exploratory Data Analysis (EDA)
│   ├── 4. Data Preprocessing
│   ├── 5. Feature Engineering
│   ├── 6. Model Development
│   ├── 7. Model Evaluation & Comparison
│   └── 8. Insights & Recommendations
└── requirements.txt                    # Python dependencies (auto-generated)
```

### Key Notebook Sections

1. **Data Loading & Understanding:** Load datasets, check shapes, data types, and initial statistics
2. **Exploratory Data Analysis:** Histograms, scatter plots, box plots, and distribution analysis
3. **Missing Value Analysis:** Identify and quantify data gaps
4. **Data Preprocessing:** Handle missing values, encode categorical features, normalize numerical features
5. **Feature Engineering:** Create tenure feature from joining dates, calculate derived metrics
6. **Model Building:** Train Linear Regression, Random Forest, and Gradient Boosting models
7. **Model Evaluation:** Compare performance metrics across all models
8. **Conclusions & Recommendations:** Summarize findings and business implications

---

## 🔧 Data Preprocessing

### 1. **Missing Value Handling**
```
Strategy: Median imputation for numerical features, mode imputation for categorical
- Resource Allocation → Median of feature
- Mental Fatigue Score → Median of feature
- Gender → Mode (most frequent value)
- Burn Rate (Target) → Rows dropped entirely
```

### 2. **Outlier Treatment**
```
Method: Clipping to valid ranges
- Resource Allocation: Clipped to [1, 10]
- Mental Fatigue Score: Clipped to [0, 10]
```

### 3. **Feature Engineering**
```
New Features Created:
- Tenure: Calculated from Date of Joining (relative to 2020-12-31)
  Formula: (Reference Date - Joining Date) / 365 days
- Normalized Tenure: Min-Max scaling to [0, 1]
```

### 4. **Encoding**
```
Categorical Encoding:
- Gender: Male → 1, Female → 0
- WFH Setup Available: Yes → 1, No → 0
- Company Type: One-hot encoding (drop first to avoid multicollinearity)
```

### 5. **Scaling & Normalization**
```
Method: Min-Max Scaling (MinMaxScaler)
Features Normalized:
- Resource Allocation → [0, 1]
- Designation → [0, 1]
- Tenure → [0, 1]

Benefits:
- Ensures all features are on same scale
- Improves model convergence
- Prevents features with larger ranges from dominating
```

### 6. **Train-Test Split**
```
Validation Split: 80% training, 20% validation
Method: sklearn.model_selection.train_test_split
Random State: 42 (for reproducibility)
```

### 7. **Data Alignment**
```
Process: Aligned train and test feature columns
- Ensures train and test have identical feature sets
- Handles missing columns after one-hot encoding
```

---

## 📈 Exploratory Data Analysis (EDA)

### Major Findings & Patterns

#### 1. **Distribution Analysis**
- **Burn Rate:** Fairly uniform distribution with mean = 0.45, indicating diverse burnout levels across workforce
- **Mental Fatigue Score:** Slightly right-skewed with concentration around 5-6, suggesting moderate stress levels
- **Resource Allocation:** Varied distribution reflecting different workload assignments
- **Designation:** Shows representation across all job levels (0-5)

#### 2. **Relationship Analysis**

**Burn Rate vs. Mental Fatigue Score:**
- **Strong Positive Correlation:** Higher mental fatigue strongly associated with increased burnout
- Key insight: Mental fatigue is a critical predictor of burnout

**Burn Rate vs. Resource Allocation:**
- **Complex Non-linear Relationship:** Moderate resource allocation shows varied burnout levels
- Very high allocation may indicate overload and burnout
- Optimal allocation range: 3-6 shows lower average burn rates

#### 3. **Categorical Insights**

**By Gender:**
- Relatively similar burn rate distributions between male and female employees
- Slight variation suggests gender may not be primary burnout driver

**By Company Type:**
- **Service Sector:** Slightly higher average burn rates (0.46) vs. Product sector (0.44)
- Service roles may involve higher customer interaction stress

**By WFH Setup Availability:**
- Employees with WFH setup show marginally lower burn rates
- Flexibility appears beneficial but not the sole solution

#### 4. **Temporal Insights**
- Tenure shows varied burnout levels; both new and long-tenured employees experience burnout
- Suggests burnout is not solely experience-related

### Key Visualizations

1. **Histogram Matrix:** Distribution of all numerical features
2. **Scatter Plots:** 
   - Burn Rate vs. Mental Fatigue Score (positive correlation)
   - Burn Rate vs. Resource Allocation (non-linear relationship)
3. **Box Plots:**
   - Burn Rate by Gender (minimal difference)
   - Burn Rate by Company Type (service slightly higher)
   - Burn Rate by WFH Setup (flexible work beneficial)

---

## 🤖 Models Used

### 1. **Linear Regression**

**Why Chosen:**
- Baseline model for regression tasks
- Interpretable coefficients show feature importance
- Fast training and inference
- Provides benchmark for performance comparison

**Characteristics:**
- Assumes linear relationship between features and target
- Sensitive to feature scaling (applied MinMaxScaler)
- Prone to underfitting if relationships are complex

**Hyperparameters:**
- Default sklearn parameters
- No regularization (L1/L2) applied

---

### 2. **Random Forest Regressor**

**Why Chosen:**
- Handles non-linear relationships effectively
- Robust to outliers due to ensemble averaging
- Provides feature importance rankings
- Naturally handles categorical variables
- Reduces overfitting through averaging

**Characteristics:**
- Ensemble of decision trees
- Uses bootstrap sampling for diversity
- Parallelizable for faster training

**Hyperparameters:**
- `random_state=0` (for reproducibility)
- Default: 100 trees, max_depth=None, min_samples_split=2
- Default: Gini criterion for split quality

---

### 3. **Gradient Boosting Regressor**

**Why Chosen:**
- State-of-the-art ensemble method
- Captures complex patterns through sequential tree building
- Typically highest predictive performance
- Weights misclassified samples more heavily

**Characteristics:**
- Sequential tree building with error corrections
- Each tree reduces residuals of previous trees
- More computationally intensive but often delivers best results

**Hyperparameters:**
- `random_state=0` (for reproducibility)
- Default: 100 estimators, learning_rate=0.1, max_depth=3
- Default: Loss function = squared error

---

## 📊 Evaluation Metrics

The project evaluates all models using regression-specific metrics:

| Metric | Formula | Interpretation | Range |
|--------|---------|-----------------|-------|
| **MAE** | Σ\|y_true - y_pred\| / n | Average absolute error in prediction | [0, ∞) |
| **RMSE** | √(Σ(y_true - y_pred)² / n) | Penalizes larger errors more | [0, ∞) |
| **R² Score** | 1 - (SS_res / SS_tot) | Proportion of variance explained | [0, 1] |

### Interpretation Guide

- **MAE (Mean Absolute Error):** 
  - Lower is better
  - Represents average prediction error
  - Unit: same as target (0-1 burn rate scale)

- **RMSE (Root Mean Squared Error):**
  - Lower is better
  - Emphasizes larger errors
  - Unit: same as target

- **R² Score:**
  - Higher is better (closer to 1)
  - R² = 1: Perfect predictions
  - R² = 0: Model predicts mean value (no value added)
  - R² < 0: Worse than predicting mean

---

## 📉 Results and Insights

### Model Performance Comparison

The project trains and compares three regression models on an 80-20 train-validation split.

**Expected Results Pattern:**
- Gradient Boosting typically shows best performance
- Random Forest provides good balance of accuracy and interpretability
- Linear Regression serves as baseline comparison

### Key Business Insights

1. **Mental Fatigue is Critical:**
   - Primary predictor of burnout
   - Strong positive correlation with burn rate
   - Should be monitored continuously

2. **Workload Management Matters:**
   - Resource allocation impacts burnout levels
   - Optimal range appears to be moderate allocation
   - Extreme overload correlates with higher burnout

3. **Sector-Specific Patterns:**
   - Service sector shows slightly higher burnout
   - May require targeted interventions
   - Product sector offers insights for best practices

4. **Work Flexibility Benefits:**
   - WFH availability associated with lower burnout
   - Flexibility is protective factor
   - Should be expanded where feasible

### Actionable Recommendations

1. **Immediate Actions:**
   - Implement regular mental fatigue assessments
   - Monitor employees with high mental fatigue scores
   - Create intervention protocols for at-risk employees

2. **Medium-term Strategies:**
   - Rebalance workloads for overallocated employees
   - Expand flexible work arrangements
   - Introduce wellness programs targeting mental health

3. **Long-term Solutions:**
   - Build predictive burnout dashboard for HR
   - Integrate model into annual performance reviews
   - Create data-driven workforce planning strategy
   - Establish burnout prevention culture

---

## 🚀 Installation and Setup

### Prerequisites
- Python 3.7 or higher
- pip or conda package manager
- 2GB RAM (minimum)
- Internet connection for data loading

### Step 1: Clone Repository

```bash
git clone https://github.com/K121-hash/Capstone-project-3.git
cd Capstone-project-3
```

### Step 2: Create Virtual Environment

```bash
# Using venv
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate

# Or using conda
conda create -n burnout_prediction python=3.8
conda activate burnout_prediction
```

### Step 3: Install Dependencies

```bash
pip install -r requirements.txt
```

### Step 4: Verify Installation

```bash
python -c "import pandas, numpy, sklearn, matplotlib, seaborn; print('All packages installed successfully!')"
```

### Step 5: Run Jupyter Notebook

```bash
jupyter notebook Capstone_project_3.ipynb
```

---

## 📋 Requirements

### Python Packages

```
pandas>=1.0.0           # Data manipulation and analysis
numpy>=1.18.0           # Numerical computing
matplotlib>=3.0.0       # Data visualization
seaborn>=0.9.0          # Statistical data visualization
scikit-learn>=0.22.0    # Machine learning models
jupyter>=1.0.0          # Interactive notebooks
```

### Generate Requirements File

```bash
pip freeze > requirements.txt
```

---

## 🔄 How to Reproduce the Project

### Step 1: Prepare Your Environment

```bash
# Clone and navigate
git clone https://github.com/K121-hash/Capstone-project-3.git
cd Capstone-project-3

# Create and activate virtual environment
python -m venv venv
source venv/bin/activate
```

### Step 2: Install Dependencies

```bash
pip install -r requirements.txt
```

### Step 3: Prepare Data

The notebook expects CSV files in a specific location:
```
train.csv  # 22,750 records with 9 features including target (Burn Rate)
test.csv   # 12,250 records with 8 features (no target)
```

For Google Colab users, update file paths:
```python
df_train = pd.read_csv('/content/drive/MyDrive/train.csv')
df_test = pd.read_csv('/content/drive/MyDrive/test.csv')
```

For local users:
```python
df_train = pd.read_csv('./data/train.csv')
df_test = pd.read_csv('./data/test.csv')
```

### Step 4: Run Analysis Pipeline

Execute notebook cells sequentially:

1. **Import Libraries** (Cell 1)
2. **Load Data** (Cell 2)
3. **Exploratory Data Analysis** (Cells 3-6)
4. **Data Preprocessing** (Cells 7-14)
5. **Model Development** (Cells 15-17)
6. **Model Evaluation** (Cells 18-20)
7. **Generate Insights** (Cells 21+)

### Step 5: Verify Results

Check for clean preprocessed data, visualizations, trained models, and performance metrics.

---

## 💡 Future Improvements

### Advanced Modeling
- Implement XGBoost and LightGBM
- Explore neural networks and deep learning
- Test ensemble stacking methods
- Hyperparameter tuning with GridSearchCV

### Feature Engineering
- Create interaction features
- Add temporal features and seasonality
- Extract role-specific metrics
- Incorporate company-level aggregates

### Model Deployment
- Create REST API (Flask/FastAPI)
- Build interactive dashboard (Streamlit)
- Deploy to cloud platforms (AWS/GCP/Azure)
- Implement real-time prediction pipeline

### Monitoring & Maintenance
- Performance monitoring systems
- Automated retraining pipelines
- Data drift detection
- A/B testing framework

---

## 👨‍💼 Author

**Data Science & Analytics Portfolio**

This project demonstrates expertise in machine learning, data analysis, and business problem-solving.

**Connect & Collaborate:**
- GitHub: [@K121-hash](https://github.com/K121-hash)

---

## 📜 License

This project is licensed under the **MIT License** - free to use, modify, and distribute.

---

**Project Status:** ✅ Complete | **Last Updated:** 2026-05-30 | **Version:** 1.0.0
