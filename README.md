#  Fuel Economy Analysis Using Python & Seaborn

##  Project Overview
This project analyzes **fuel economy trends** using Python, Seaborn, and Matplotlib. The dataset used is the **mpg dataset** from Seaborn, which contains information about fuel economy, horsepower, cylinders, and vehicle origins.

### **Key Objectives**
- Understand the **relationship between horsepower and fuel economy**.
- Analyze **fuel economy trends by country of origin**.
- Observe **how fuel economy has changed over time**.
- Explore the **distribution of fuel economy**.
- Examine **the impact of cylinder count on fuel efficiency**.

---

## 🛠 **Tools & Libraries Used**
- **Python**  → Data processing and visualization.
- **Pandas**  → Data manipulation and analysis.
- **Seaborn**  → Statistical data visualization.
- **Matplotlib**  → Creating plots and visualizations.

---

##  **Data Analysis & Key Findings**

### **1️⃣ Relationship Between Horsepower and Fuel Economy**
 **Objective:** Examine how a car’s horsepower affects its fuel efficiency.  
 **Observation:** There is an **inverse relationship** between horsepower and fuel economy – as horsepower **increases**, fuel economy **decreases**.

```python
plt.figure(figsize=(10, 6))
sns.scatterplot(x='horsepower', y='mpg', data=mpg)
plt.title('Relationship between Horsepower and Fuel Economy')
plt.xlabel('Horsepower')
plt.ylabel('Miles per Gallon (mpg)')
plt.grid(True, linestyle='--', linewidth=0.5)
plt.show()
```

---

### **2️⃣ Fuel Economy by Country of Origin**
 **Objective:** Compare fuel economy across **USA, Japan, and Europe**.  
 **Observation:** **Japanese cars tend to have better fuel economy** compared to American and European cars.

```python
fuel_economy_by_origin = mpg.groupby('origin')['mpg'].mean().reset_index()
fuel_economy_by_origin.columns = ['Country of Origin', 'Average Fuel Economy (mpg)']
fuel_economy_by_origin
```

 **Average Fuel Economy by Origin:**

| Country  | Avg MPG  |
|----------|---------|
| **Europe**  | 27.89  |
| **Japan**   | 30.45  |
| **USA**     | 20.08  |

---

### **3️⃣ Change in Fuel Economy Over Time**
 **Objective:** Observe how fuel economy has evolved across different years.  
 **Observation:** Fuel economy **improved significantly in the late 1970s and early 1980s**, likely due to oil crises and regulatory changes.

```python
mpg['year'] = mpg['model_year'] + 1900
average_mpg_by_year = mpg.groupby('year')['mpg'].mean().reset_index()
sns.lineplot(x='year', y='mpg', data=average_mpg_by_year)
plt.title('Change in Fuel Economy Over Time')
plt.xlabel('Year')
plt.ylabel('Average Miles per Gallon (mpg)')
plt.grid(True)
plt.show()
```

---

### **4️⃣ Distribution of Fuel Economy**
 **Objective:** Understand the spread and concentration of fuel economy values.  
 **Observation:** Most cars have **fuel economy between 15 and 30 mpg**, with a few outliers on both ends.

```python
plt.figure(figsize=(10, 6))
sns.histplot(mpg['mpg'], bins=20, kde=True)
plt.title('Distribution of Fuel Economy')
plt.xlabel('Miles per Gallon (mpg)')
plt.ylabel('Frequency')
plt.show()
```

---

### **5️⃣ Fuel Economy by Cylinder Count**
 **Objective:** Investigate how the number of cylinders affects fuel efficiency.  
 **Observation:** Cars with **fewer cylinders tend to have better fuel economy**.  
🔹 **4-cylinder cars** have the **highest median mpg**, while **8-cylinder cars** have the **lowest**.

```python
plt.figure(figsize=(10, 6))
sns.boxplot(x='cylinders', y='mpg', data=mpg, palette="Set2")
plt.title('Fuel Economy by Number of Cylinders', fontsize=16)
plt.xlabel('Number of Cylinders', fontsize=14)
plt.ylabel('Miles per Gallon (mpg)', fontsize=14)
plt.grid(True, which='major', axis='y', linestyle='--', linewidth=0.7, color='gray')
plt.show()
```

---

## 🔍 **Summary of Findings**
✔️ **Horsepower vs. Fuel Economy** → As **horsepower increases, fuel economy decreases**.  
✔️ **Fuel Economy by Origin** → **Japanese cars have the best fuel economy**, followed by **European and American cars**.  
✔️ **Fuel Economy Trends Over Time** → Fuel efficiency **improved significantly** in the late **1970s & 1980s**.  
✔️ **Distribution of Fuel Economy** → Most cars **fall between 15-30 mpg**.  
✔️ **Cylinders vs. Economy** → Cars with **fewer cylinders** tend to have **higher mpg**.  

---

##  **How to Use This Repository**
1️⃣ **Clone this repository**  
```bash
git clone https://github.com/YOUR_GITHUB_USERNAME/Fuel-Economy-Analysis.git
cd Fuel-Economy-Analysis
```
2️⃣ **Install dependencies**  
```bash
pip install pandas seaborn matplotlib
```
3️⃣ **Run the Python script** to generate visualizations.

