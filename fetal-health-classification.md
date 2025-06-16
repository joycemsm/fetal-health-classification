# Fetal Health Classification

The **reduction of infant and maternal mortality** is one of the main global commitments established by the **United Nations Sustainable Development Goals (SDGs)**. The aim is that, by 2030, all countries reduce the mortality rate of children under the age of 5 to less than **25 per 1,000 live births** and eliminate preventable deaths of **newborns and pregnant women**. In 2017, for example, around **295,000 maternal deaths** were recorded—mostly in low-resource regions and, in most cases, avoidable.

In this context, **fetal health monitoring** through **cardiotocography (CTG)** exams offers an accessible and effective solution. CTG evaluates the **fetal heart rate**, the **baby’s movements**, and **uterine contractions**, providing valuable insights that help healthcare professionals identify possible complications early during pregnancy.

This project aims to analyze clinical data obtained from CTGs to develop a **fetal health classification system**. The analysis is based on a dataset with **2,126 real-world exams**, each evaluated by **three medical specialists**, who assigned one of the following classifications: **normal (1)**, **suspicious (2)**, or **pathological (3)**. The dataset was originally published by the **UCI Machine Learning Repository** and later organized on Kaggle by Andrew Mvd.

The material supports **data-driven clinical decision-making**, helping to prevent fetal complications and thereby **contributing to the reduction of maternal and infant mortality**.



# Dataset Acquisition

This data was originally made available by the **UCI Machine Learning Repository** and later organized and published on **Kaggle**. The dataset consists of records from **fetal heart rate monitoring exams**, also known as **cardiotocography (CTG)**. Each case was reviewed and classified by **three medical specialists**.

![Screenshot 2025-06-16 at 15 17 02](https://github.com/user-attachments/assets/833ac0e7-e56e-4953-97cb-0d6893ddafed)



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



# Question-Oriented Approach

In this project, I chose to organize the analysis around **key questions** that a doctor or healthcare professional might ask when interpreting fetal monitoring exams.



# How is fetal health distributed in the dataset?

The initial analysis shows the distribution of fetal health classifications based on cardiotocographic signals. Most fetuses were classified as **healthy (77.85%)**, while **13.88%** were labeled as **suspicious** and **8.28%** as **pathological**.

This overview suggests that, although most cases fall within normal parameters, **about 1 in every 5 fetuses shows some level of clinical risk**. This highlights the importance of data-driven decision support systems capable of quickly identifying warning signs that require medical attention.


### **Note on Class Imbalance**

The dataset shows a **strong imbalance among the classes**, with a predominance of healthy fetuses. This likely reflects real clinical conditions, where most exams do not indicate immediate risk.

Since this project is focused on **exploratory and descriptive analysis (EDA)**, this imbalance **will not be corrected**.

However, it’s important to mention, as it affects how statistics are compared across groups. The less represented categories (classes 2 and 3) are more prone to **statistical bias and sampling fluctuations**, requiring **careful interpretation** when drawing conclusions by class.

![image](https://github.com/user-attachments/assets/3b7be8af-f2c2-4d3e-a726-fcf272ced4e2)


**How this chart was created:**  
The chart was built in Power BI using a pie chart visual, based on the categorical column `Fetal Class`. The slices represent the proportion of fetuses in each health category (healthy, suspicious, and pathological), with percentages displayed directly on the chart. Colors were standardized according to risk level: green (healthy), yellow (suspicious), and red (pathological).



# Do babies with health risks have higher heart rates?

In this part of the study, we analyzed the **baseline fetal heart rates** — that is, the average heart rate of the fetus at rest, measured during routine exams.

The results showed that:

- Healthy fetuses have an average of **131.98 beats per minute (bpm)**  
- Fetuses with mild risk (suspicious): **141.68 bpm**  
- High-risk (pathological) fetuses: **131.69 bpm**

This indicates that **the higher the average heart rate, the greater the identified risk**.

Healthcare professionals can use this information as an **early warning sign**. A baseline heart rate above normal levels may suggest that the fetus is experiencing **fetal distress** and should be monitored more closely.

![image](https://github.com/user-attachments/assets/1271fa14-ca5b-4ec1-a032-071f280d25b0)

**How this chart was created:**  
I used a column chart in Power BI to compare the average baseline heart rate (`baseline_value`) across the three fetal health classes.  
The classification variable (`fetal_health`) was converted into a categorical column with custom labels: *Healthy*, *Suspicious*, and *Pathological* — to improve readability.

Then, I applied the "Average" aggregation function to display the mean heart rate per group, and enabled data labels to show the values directly on each column.

Colors were standardized using a risk-based color code: green (healthy), yellow (suspicious), and red (pathological).


# Can the lack of heart rate accelerations signal danger?

The chart shows that **healthy fetuses have a significantly higher average number of accelerations** (0.0040), while **suspicious and pathological cases show almost no accelerations** (0.0003 and 0.0004).

This pattern suggests that **a lack of accelerations is strongly associated with fetal risk**, reinforcing its value as a clinical indicator in fetal monitoring exams.

Interestingly, the *suspicious* group considered an intermediate risk had an even lower average than the pathological group. This shows that the absence of accelerations **does not follow a linear trend across risk levels**, and may vary depending on individual clinical patterns.

This reinforces the importance of evaluating **multiple indicators together**, rather than relying on a single metric.

![image](https://github.com/user-attachments/assets/70cd4d09-877b-42fd-bf1f-107955091f4e)


# How do key health signals behave in each risk group?

The table below summarizes the key clinical indicators from the fetal exams, showing their average values across each risk group: **Healthy**, **Suspicious**, and **Pathological**.  
The goal of this analysis is to observe **how the indicators behave together**, rather than looking at each variable in isolation.

This type of summary helps reveal the **typical patterns** for each group and supports the identification of meaningful trends that can guide clinical decision-making.

![image](https://github.com/user-attachments/assets/7ecc8ef0-c4ff-4dfe-8f3a-95b835574943)


- **Healthy fetuses** show more balanced signs: heart rates within normal range, good presence of accelerations, and stable variability in the exams. This suggests a **well-functioning fetal cardiovascular system**.

- **Suspicious fetuses** present a curious profile: the heart rate is elevated, but reactivity signals are weak as if the heart is beating faster, but not responding well to stimuli. This pattern may represent an **early warning sign** and requires closer observation.

- **Pathological fetuses** exhibit more critical signs: heart rate appears unstable, with wide variability over time and more frequent prolonged decelerations. This indicates a **higher risk of complications**.

Each fetal group displays its own behavior and risk is not always visible in just one signal.

**Analyzing the data in combination** helps uncover patterns that may go unnoticed in isolated charts.


# **Which Signals Should Be Monitored More Closely During the Exam?**

### **Accelerations** → **High variation**

Healthy fetuses have significantly more accelerations than the other groups.  
Suspicious and pathological fetuses show almost none.

This is classified as “High variation” because the difference between groups was clear and strong.

**Conclusion:** This signal is very helpful for identifying fetal risk.

### **Baseline value** → **Moderate variation**

The average heart rate changes slightly across groups (e.g., pathological cases tend to have slightly higher rates).  
However, this difference was not as prominent as in other indicators.

**Conclusion:** It helps indicate risk, but is **not sufficient on its own**. It serves better as a supporting metric.

### **Fetal movement** → **Moderate variation**

Healthy fetuses tend to move slightly more.  
However, the difference among groups was not large or consistent.

**Conclusion:** It can be useful, but **is not a reliable standalone signal**.

### **Histogram variance** → **High variation**

Pathological fetuses showed much more **variation in heart rate over time**.  
Healthy fetuses had more stable readings.

**Conclusion:** A strong sign of fetal instability. **Highly relevant for clinical screening.**

### **Prolonged decelerations** → **High variation**

This type of drop in heart rate occurred much more often in pathological cases.  
Healthy fetuses showed this signal rarely.

**Conclusion:** One of the **most critical indicators** of fetal risk. **High clinical priority.**

### **Severe decelerations** → **Low variation**

This signal **barely appeared in any group**.  
The average was close to zero across all cases.

**Important to understand:** This **does not mean the signal isn’t serious**, but rather that **it was rare in this dataset**.

**Conclusion:** It was not useful for distinguishing between groups in this analysis.  
**(However, it remains clinically important when it does occur.)**

![image](https://github.com/user-attachments/assets/ebc5d80b-3717-45ed-a338-ca88ae9cc132)


![image](https://github.com/user-attachments/assets/f83f43d7-fecf-4649-81fe-364a4f6d2cf5)


**How the chart was created:**  
An auxiliary table was created in Power BI using DAX (`DATATABLE`) to manually record the variation level of each clinical signal across the fetal health groups.  
The classification (High, Moderate, or Low) was based on the previous exploratory analysis.  
This matrix summarizes the signals most sensitive to clinical variation and highlights their relevance for screening purposes.


# Are strong contractions linked to more risky cases?

This chart shows the relationship between levels of uterine contractions (Low, Moderate, High) and fetal health classification (Healthy, Suspicious, Pathological).  
Each bar represents the number of fetuses observed at each contraction level, broken down by risk category.

At low levels, most fetuses are healthy (991), with fewer at-risk cases.  
At moderate levels, the number of suspicious and pathological cases becomes nearly equal, indicating that risk begins to increase.  
At high contraction levels, even though total cases are fewer, around 1 in every 3 fetuses shows signs of clinical risk.

This pattern suggests that intense contractions may be associated with a higher probability of fetal risk, making it an important signal to monitor during evaluation.

![image](https://github.com/user-attachments/assets/3463b35a-14c3-4d58-adff-4d87de579559)


**How the chart was created:**  
To calculate the number of cases in each group, a DAX measure called `Fetal Count` was created using the `COUNTROWS` function.


# Project Conclusion

This project explored fetal monitoring data with the goal of identifying clinical signals associated with pregnancy risk. The analysis revealed that:

- Most exams indicated healthy fetuses, but **approximately 22% of cases showed some level of risk**.  
- Variables such as **accelerations**, **heart rate variability**, and **prolonged decelerations** stood out as the most sensitive signals for risk screening.  
- The *suspicious* group displayed a distinct clinical profile, with elevated heart rates but low reactivity, which **highlights the importance of analyzing the data as a whole**, rather than signal by signal.  
- The Power BI dashboard makes it easy to visualize these patterns and can serve as a support tool for clinical decision-making.

This project reinforced the importance of communicating data in a simple, useful, and trustworthy way especially in sensitive contexts like fetal health.  
It also served as a practical opportunity to apply Power BI, DAX, and analytical reasoning in a setting with real-world impact.


# Power BI

Below is the Power BI dashboard developed for this project, where the main analyses are organized in an interactive format.  
It was designed to allow quick interpretation of risk signals, with filters available by fetal group and clinical variables.


![Screenshot 2025-06-16 at 15 20 17](https://github.com/user-attachments/assets/9f8d2368-9659-4e8c-aa0e-996d43c456e5)



### Tools Used:

Power BI · Power Query · DAX · Charts · Slicers · Cards · Matrix · Table · GitHub

---

**"Every mother deserves the peace of mind that comes from safe, informed, and compassionate care, and data can be a powerful ally in making that possible."** 💚

