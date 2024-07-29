### Introduction

This project focuses on analyzing the MPG (Miles Per Gallon) dataset using various data visualization techniques. The dataset provides information about the fuel economy of different car models, including attributes such as horsepower, cylinders, and country of origin. By leveraging Python libraries like `seaborn`, `pandas`, and `matplotlib`, the analysis aims to uncover insights and trends related to fuel efficiency, helping to understand factors that influence vehicle performance and fuel consumption over time.

### Steps Taken

1. **Import Libraries**: 
   - The necessary libraries are imported: `seaborn`, `pandas`, and `matplotlib.pyplot`.

    ```python
    import seaborn as sns
    import pandas as pd
    import matplotlib.pyplot as plt
    ```

2. **Load the Dataset**:
   - The `mpg` dataset is loaded using the `seaborn` library.

    ```python
    mpg = sns.load_dataset('mpg')
    ```

3. **Scatter Plot - Horsepower vs. Fuel Economy**:
   - A scatter plot is created to visualize the relationship between horsepower and fuel economy.

    ```python
    plt.figure(figsize=(10, 6))
    sns.scatterplot(x='horsepower', y='mpg', data=mpg)
    plt.title('Relationship between Horsepower and Fuel Economy')
    plt.xlabel('Horsepower')
    plt.ylabel('Miles per Gallon (mpg)')
    plt.grid(True, linestyle='--', linewidth=0.5)
    plt.xticks(fontsize=12)
    plt.yticks(fontsize=12)
    plt.show()
    ```

4. **Summary Table - Fuel Economy by Country of Origin**:
   - A table is generated summarizing the average fuel economy by country of origin.

    ```python
    fuel_economy_by_origin = mpg.groupby('origin')['mpg'].mean().reset_index()
    fuel_economy_by_origin.columns = ['Country of Origin', 'Average Fuel Economy (mpg)']
    fuel_economy_by_origin
    ```

5. **Line Plot - Change in Fuel Economy Over Time**:
   - A line plot is created to show the change in fuel economy over time. Future warnings from `seaborn` are suppressed.

    ```python
    import warnings

    # Suppress the FutureWarning
    warnings.filterwarnings("ignore", category=FutureWarning, module="seaborn")

    plt.figure(figsize=(10, 6))
    mpg['year'] = mpg['model_year'] + 1900
    average_mpg_by_year = mpg.groupby('year')['mpg'].mean().reset_index()
    sns.lineplot(x='year', y='mpg', data=average_mpg_by_year)
    plt.title('Change in Fuel Economy Over Time')
    plt.xlabel('Year')
    plt.ylabel('Average Miles per Gallon (mpg)')
    plt.grid(True)
    plt.show()
    ```

6. **Histogram - Distribution of Fuel Economy**:
   - A histogram is plotted to show the distribution of fuel economy (MPG).

    ```python
    plt.figure(figsize=(10, 6))
    sns.histplot(mpg['mpg'], bins=20, kde=True)
    plt.title('Distribution of Fuel Economy')
    plt.xlabel('Miles per Gallon (mpg)')
    plt.ylabel('Frequency')
    plt.show()
    ```

7. **Box Plot - Fuel Economy by Number of Cylinders**:
   - A box plot is created to visualize the fuel economy based on the number of cylinders in the cars.

    ```python
    sns.set_style("whitegrid")

    plt.figure(figsize=(10, 6))
    sns.boxplot(x='cylinders', y='mpg', data=mpg, palette="Set2")
    plt.title('Fuel Economy by Number of Cylinders', fontsize=16)
    plt.xlabel('Number of Cylinders', fontsize=14)
    plt.ylabel('Miles per Gallon (mpg)', fontsize=14)

    plt.grid(True, which='major', axis='y', linestyle='--', linewidth=0.7, color='gray')

    plt.xticks(fontsize=12)
    plt.yticks(fontsize=12)
    plt.show()
    ```
