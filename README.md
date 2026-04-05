# 🩺 Medical Insurance Cost Analysis using Python
 
## 📘 Project Overview
This project explores **factors influencing medical insurance charges** using a dataset of **1,338 individuals** from the U.S. healthcare system.  
The analysis aims to understand how **age, gender, BMI, number of children, smoking status, and region** affect the **medical insurance cost (`charges`)** billed to individuals.  

This project demonstrates:
- **Exploratory Data Analysis (EDA)**
- **Feature Engineering**
- **Visualization & Statistical Insights**
- **Data-driven business interpretation**

---

## 🧩 About the Dataset

The dataset contains medical insurance information for **1,338 people**, commonly used for **regression modeling** and **healthcare economics research**.

### 🗂️ Columns Description
| Column | Description |
|---------|-------------|
| **age** | Age of the primary beneficiary |
| **sex** | Gender of the beneficiary *(male/female)* |
| **bmi** | Body Mass Index — a measure of body fat based on height and weight |
| **children** | Number of children covered by health insurance |
| **smoker** | Smoking status *(yes/no)* |
| **region** | Residential region in the U.S. *(northeast, northwest, southeast, southwest)* |
| **charges** | Medical insurance cost billed to the beneficiary |

### 💡 Potential Use Cases
- Explore how **smoking and BMI impact charges**
- Analyze **healthcare affordability** trends
- Build **pricing strategies** for insurers
- Support **data science education** and tutorials

---

## 🎯 Objectives
1. Perform a **comprehensive exploratory data analysis (EDA)**
2. Identify **key drivers** of insurance costs (age, BMI, smoking, etc.)
3. Build **meaningful visualizations** to support insights
4. Derive **data-backed business recommendations** for insurers

---

## 🧮 Tech Stack
| Tool / Library | Purpose |
|----------------|----------|
| **Python (Pandas, NumPy)** | Data loading, cleaning, and analysis |
| **Matplotlib, Seaborn** | Data visualization and storytelling |
| **Jupyter Notebook** | Interactive analysis and documentation |

---

## 🧾 Project Workflow

### 1️⃣ Data Loading & Inspection
- Loaded dataset using `pandas.read_csv()`
- Checked structure with `.info()` and `.describe()`
- Verified no missing values using `.isnull().sum()`
- Checked unique values in categorical columns (`sex`, `smoker`, `region`)

#### 🧠 Key Insights
- Dataset is **complete (no missing values)**
- Balanced data types: 4 numeric + 4 categorical
- Ideal for immediate analysis and visualization

---

### 2️⃣ Feature Engineering — Age Segmentation
Created a new feature **`age_segment`** using Python’s `apply()` — similar to SQL CASE WHEN logic:

```python
def get_age_segment(age):
    if age <= 12:
        return '0-12 children'
    elif age <= 20:
        return '13-20 teen age'
    elif age <= 30:
        return '21-30 youths'
    elif age <= 45:
        return '31-45 mid-old'
    elif age <= 60:
        return '46-60 old'
    else:
        return '60+ senior citizen'

insurance['age_segment'] = insurance['age'].apply(get_age_segment)
``````````````````````````````````````````````````````````````````

## 3️⃣ Data Quality Check

No missing values were found in any column.  
All categorical variables were clean and properly labeled.

### 📊 Insights
- **Perfect data completeness** — 0 missing values across all features.  
- Ready for analysis and modeling without preprocessing.  
- Ensures **high-quality and unbiased insights**.

---

## 4️⃣ Exploratory Data Analysis (EDA)

### 🔹 Correlation Analysis
```python
insurance[['age', 'charges']].corr()
`````````````````````````````````````
### 📈 Insight

- **Moderate positive correlation** (r = 0.299) between **age** and **charges** — older individuals tend to have higher medical costs.  
- Other numerical features (like **BMI**) show weaker correlation.

---

### 🔹 Category-wise Average Charges

| Factor | Observation |
|---------|--------------|
| **Gender** | Males (₹13,956) pay slightly higher than females (₹12,569). |
| **Smoking** | Smokers (₹32,050) pay almost **4x more** than non-smokers (₹8,434). |
| **Region** | Southeast has the highest average charges. |
| **Children** | Costs rise up to 3 children, then slightly drop. |
| **Age Segment** | Costs increase steadily with age. |

---

## 5️⃣ Visualization & Insights

### 📊 Univariate Analysis
- **Age Distribution:** Most individuals are between **20–30 years** (young, low-cost demographic).  
- **BMI Distribution:** Centered around **25–30** (overweight range).  
- **Charges Distribution:** Highly **right-skewed** — few individuals with very high medical costs.

---

### 📈 Bivariate Analysis
- **Charges by Gender:** Minimal median difference, but higher outliers for males.  
- **Charges by Smoker:** Drastic difference — smoking is the **dominant risk factor**.  
- **Charges by Region:** Slightly higher in Southeast, otherwise similar.  
- **Age vs Charges:** Charges increase with age, especially for smokers.  
- **BMI vs Charges:** BMI increases cost primarily for smokers.

---

### 🔥 Correlation Heatmap
- **Age** shows the strongest correlation (0.30) with **charges**.  
- **BMI** has moderate correlation (0.20).  
- **Children** has almost no direct impact.

---

## 6️⃣ Advanced Segmentation Insights

### 📊 Average Charges by Age Segment

| Age Segment | Avg Charges |
|--------------|-------------:|
| 13–20 Teen Age | 8,713 |
| 21–30 Youths | 9,806 |
| 31–45 Mid-old | 12,647 |
| 46–60 Old | 16,341 |
| 60+ Senior Citizen | 21,063 |

### 📈 Insights
- **Insurance charges rise steadily with age** — senior citizens pay ~2.5x more than youth.  
- **Age segmentation** provides actionable insights for **premium pricing** and **risk assessment**.

---

### 📉 Average Charges by Age Segment and Smoking Status
- **Smokers** consistently face **3–4× higher** medical charges than non-smokers.  
- The **cost gap widens with age**, showing compounded risk effects.

---

### ⚖️ Average BMI by Age Segment
- Average **BMI remains around or above 30 (obese range)** across all groups.  
- Mid-aged individuals (**31–45**) show the **highest BMI values**.  
- Indicates widespread **weight-related health risks**.

---

## 7️⃣ Visual Summary

### 🖼️ Visualizations Used
- **Histograms:** Age, BMI, Charges  
- **Boxplots:** Sex, Smoker, Region vs Charges  
- **Scatterplots:** Age vs Charges, BMI vs Charges  
- **Barplots:** Age Segment vs Charges  
- **Heatmap:** Correlations  
- **Countplot:** Smoker Distribution by Age Segment  

---

### 🪶 Visualization Styling
```python
sns.set_style('whitegrid')
sns.set_palette('coolwarm')
````````````````````````````
## 📈 Key Findings Summary
- **Smokers incur the highest costs** — ~4x higher than non-smokers.
- **Charges increase sharply with age, especially for senior citizens.**
- **BMI and smoking combined lead to the most expensive medical claims.**
- **Regional variation is minimal, with the Southeast slightly higher.**
- **No missing data ensures robust, reliable insights.**

## ✅ Conclusions & Recommendations
### 🧩 Conclusions
- **Age and smoking are the most influential predictors of insurance charges.**
- **BMI adds moderate impact, particularly for smokers.**
- **Non-smokers and younger people represent the lowest-risk group.**

### 💡 Recommendations
- **Implement smoker-based premium multipliers.**
- **Offer wellness and weight management programs to reduce BMI-related risks.**
- **Create age-tiered premium plans for fair pricing.**
- **Promote preventive health campaigns targeting middle-aged customers.**
- **Maintain a strong non-smoker base to improve profitability.**

## 👩‍💻 Author
- **Priyanka Lenka**
- **📍 Bhubneswar, India**
- **📧 lenkapriyanka20007@gmail.com**
![Analysis Demo](https://github.com/PRIYANKALENKA07/Insurance-/blob/main/insurance%20charges%20distribution.png)

