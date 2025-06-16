# Fetal Health Classification

The **reduction of infant and maternal mortality** is one of the main global commitments established by the **United Nations Sustainable Development Goals (SDGs)**. The aim is that, by 2030, all countries reduce the mortality rate of children under the age of 5 to less than **25 per 1,000 live births** and eliminate preventable deaths of **newborns and pregnant women**. In 2017, for example, around **295,000 maternal deaths** were recorded—mostly in low-resource regions and, in most cases, avoidable.

In this context, **fetal health monitoring** through **cardiotocography (CTG)** exams offers an accessible and effective solution. CTG evaluates the **fetal heart rate**, the **baby’s movements**, and **uterine contractions**, providing valuable insights that help healthcare professionals identify possible complications early during pregnancy.

This project aims to analyze clinical data obtained from CTGs to develop a **fetal health classification system**. The analysis is based on a dataset with **2,126 real-world exams**, each evaluated by **three medical specialists**, who assigned one of the following classifications: **normal (1)**, **suspicious (2)**, or **pathological (3)**. The dataset was originally published by the **UCI Machine Learning Repository** and later organized on Kaggle by Andrew Mvd.

The material supports **data-driven clinical decision-making**, helping to prevent fetal complications and thereby **contributing to the reduction of maternal and infant mortality**.

---

# Dataset Acquisition

This data was originally made available by the **UCI Machine Learning Repository** and later organized and published on **Kaggle**. The dataset consists of records from **fetal heart rate monitoring exams**, also known as **cardiotocography (CTG)**. Each case was reviewed and classified by **three medical specialists**.

![image](https://github.com/user-attachments/assets/a6250368-534d-4245-987b-2df853a2ba42) 

---

# Dataset Analysis

### **What does each row and column represent?**

- **Each row** = one fetal monitoring exam (CTG)  
- **Each column** = a clinical or statistical variable from the exam

### **How many variables and observations are there?**

- **Columns** (variables) → 21  
- **Rows** (exams) → 2,126

### **What is the goal of this dataset?**

- The dataset is used to **classify fetal health** as:
  - **1 = normal**
  - **2 = suspicious**
  - **3 = pathological**

### **What do these technical variables mean?**

- The fetal heart rate should vary normally (this is a good sign).  
- Sudden drops or lack of variation may indicate warning signs.  
- The variables show **how the baby's heart responds to stimuli**, helping assess whether the situation is safe.

---

### **Variable Dictionary**

- **`baseline value`** – Average fetal heart rate (bpm)  
- **`accelerations`** – Accelerations in heart rate per second  
- **`fetal_movement`** – Fetal movements per second  
- **`uterine_contractions`** – Uterine contractions per second  
- **`light_decelerations`** – Mild drops in heart rate  
- **`severe_decelerations`** – Severe drops in heart rate  
- **`prolonged_decelerations`** – Prolonged and concerning heart rate drops  
- **`abnormal_short_term_variability`** – Time with abnormal short-term variability  
- **`mean_value_of_short_term_variability`** – Mean of short-term variability  
- **`percentage_of_time_with_abnormal_long_term_variability`** – % of time with abnormal long-term variability  
- **`mean_value_of_long_term_variability`** – Mean of long-term variability  
- **`histogram_width`** – Total width of heart rate histogram  
- **`histogram_min`** – Minimum heart rate value  
- **`histogram_max`** – Maximum heart rate value  
- **`histogram_number_of_peaks`** – Number of peaks in the histogram  
- **`histogram_number_of_zeroes`** – Number of times with zero frequency (signal loss)  
- **`histogram_mode`** – Most frequent heart rate value  
- **`histogram_mean`** – Overall mean heart rate  
- **`histogram_median`** – Median heart rate  
- **`histogram_variance`** – Heart rate variability  
- **`histogram_tendency`** – Tendency of heart rate (increasing or decreasing)  
- **`fetal_health`** – Fetal health class (1 = normal, 2 = suspicious, 3 = pathological)

---



  
