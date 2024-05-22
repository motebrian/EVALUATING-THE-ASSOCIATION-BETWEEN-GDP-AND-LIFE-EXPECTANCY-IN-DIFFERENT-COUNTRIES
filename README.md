# WORLD BANK - LIFE EXPECTANCY PORTFOLIO PROJECT

## Overview
This project aims to analyze the relationship between GDP and life expectancy at birth across different countries over time. Using data from the World Bank, we explore various statistical properties and visualize trends to gain insights into how economic factors influence health outcomes.

## Table of Contents
- [Data](#data)
- [Exploratory Data Analysis](#exploratory-data-analysis)
- [Bivariate Analysis](#bivariate-analysis)
- [Multivariate Analysis](#multivariate-analysis)
- [Conclusion](#conclusion)

## Data
The dataset used in this project is sourced from the World Bank and contains information on GDP and life expectancy at birth for multiple countries from 2000 to 2015.
- **Columns:**
  - `Country`: The name of the country
  - `Year`: The year of the observation
  - `Life expectancy at birth (years)`: The average number of years a newborn is expected to live
  - `GDP`: The Gross Domestic Product of the country

## Exploratory Data Analysis
1. **Loading Libraries:**
    ```python
    import pandas as pd
    import numpy as np
    import matplotlib.pyplot as plt
    import seaborn as sns
    ```

2. **Loading and Inspecting the Data:**
    ```python
    wb = pd.read_csv("path_to_your_file/all_data.csv")
    print(wb.head())
    print(wb.info())
    print(wb.describe())
    ```

3. **Distribution of Life Expectancy:**
    ```python
    sns.histplot(wb["Life expectancy at birth (years)"])
    plt.show()
    ```

4. **Distribution of GDP:**
    ```python
    sns.histplot(wb["GDP"])
    plt.show()
    ```

5. **Country Frequency:**
    ```python
    wb.Country.value_counts()
    ```

## Bivariate Analysis
1. **GDP by Country:**
    ```python
   Chile_Data3 = wb[wb.Country=='Chile']
   China_Data3 = wb[wb.Country =='China']
   Germany_Data3 = wb[wb.Country =='Germany']
   Mexico_Data3 = wb[wb.Country =='Mexico']
   USA_Data3 = wb[wb.Country =='United States of America']
   Zim_Data3 = wb[wb.Country =='Zimbabwe']
   #Getting the GDP of each country
   plt.figure(figsize=(10,8))
   sns.lineplot(x='Year', y='GDP', data=Chile_Data3, marker='o',label='Chile')
   sns.lineplot(x='Year', y='GDP', data=China_Data3, marker='o',label = 'China')
   sns.lineplot(x='Year', y='GDP', data=Germany_Data3, marker='o',label = 'Germany')
   sns.lineplot(x='Year', y='GDP', data=Mexico_Data3, marker='o', label = 'Mexico')
   sns.lineplot(x='Year', y='GDP', data=USA_Data3, marker='o',label = 'USA')
   sns.lineplot(x='Year', y='GDP', data=Zim_Data3, marker='o',label = 'Zimbambwe')
   plt.legend()
   plt.ylabel("GDP")
   plt.xlabel("Year")
   plt.savefig("GDP.PNG")
   plt.plot(China_Data3.Year,China_Data3.GDP)
   plt.show()
    ```
![GDP](https://github.com/motebrian/EVALUATING-THE-ASSOCIATION-BETWEEN-GDP-AND-LIFE-EXPECTANCY-IN-DIFFERENT-COUNTRIES/assets/90248185/f1bdd45d-6b8f-4c3d-9591-1c822e460761)

2. **Life Expectancy by Country:**
    ```python
    sns.boxplot(data=wb, x='Country', y="Life expectancy at birth (years)")
    plt.xticks(rotation=90)
    plt.show()
    ```

3. **Correlation between GDP and Life Expectancy:**
    ```python
    sns.lmplot(x='GDP', y='Life expectancy at birth (years)', data=wb, aspect=2, height=6)
    plt.title('Scatter Plot with Regression Line of GDP vs Life Expectancy')
    plt.xlabel('GDP')
    plt.ylabel('Life Expectancy at Birth (years)')
    plt.show()
    ```

## Multivariate Analysis
1. **GDP Over Time:**
    ```python
    plt.figure(figsize=(10, 6))
    sns.lineplot(x='Year', y='GDP', data=wb, marker='o')
    plt.title('GDP Over Years')
    plt.xlabel('Year')
    plt.ylabel('GDP')
    plt.grid(True)
    plt.show()
    ```

2. **Life Expectancy Over Time:**
    ```python
    plt.figure(figsize=(10, 6))
    sns.lineplot(x='Year', y='Life expectancy at birth (years)', data=wb, marker='o')
    plt.title('Life Expectancy Over Years')
    plt.xlabel('Year')
    plt.ylabel('Life Expectancy')
    plt.grid(True)
    plt.show()
    ```

3. **Individual Country Analysis:**
    ```python
    countries = ['Chile', 'China', 'Germany', 'Mexico', 'United States of America', 'Zimbabwe']
    plt.figure(figsize=(15, 10))
    for i, country in enumerate(countries):
        plt.subplot(2, 3, i+1)
        country_data = wb[wb.Country == country]
        sns.lineplot(x='Year', y='GDP', data=country_data, marker='o')
        plt.title(f'GDP of {country} Over Time')
        plt.xlabel('Year')
        plt.ylabel('GDP')
    plt.tight_layout()
    plt.show()
    ```
![GDP](https://github.com/motebrian/EVALUATING-THE-ASSOCIATION-BETWEEN-GDP-AND-LIFE-EXPECTANCY-IN-DIFFERENT-COUNTRIES/assets/90248185/f77278ca-acfe-4be1-8d9c-8d33138769e6)

4. **Life Expectancy for Individual Countries:**
    ```python
    plt.figure(figsize=(15, 10))
    for i, country in enumerate(countries):
        plt.subplot(2, 3, i+1)
        country_data = wb[wb.Country == country]
        sns.lineplot(x='Year', y='Life expectancy at birth (years)', data=country_data, marker='o')
        plt.title(f'Life Expectancy of {country} Over Time')
        plt.xlabel('Year')
        plt.ylabel('Life Expectancy')
    plt.tight_layout()
    plt.show()
    ```
![Life Expectancy](https://github.com/motebrian/EVALUATING-THE-ASSOCIATION-BETWEEN-GDP-AND-LIFE-EXPECTANCY-IN-DIFFERENT-COUNTRIES/assets/90248185/0b9cddf5-9574-413c-bc73-9f7d9993e087)

5. **Scatter Plot of GDP vs Life Expectancy:**
    ```python
    sns.scatterplot(x='GDP', y='Life expectancy at birth (years)', hue='Country', data=wb, palette='bright')
    plt.title('GDP vs Life Expectancy by Country')
    plt.xlabel('GDP')
    plt.ylabel('Life Expectancy at Birth (years)')
    plt.show()
    ```
![Scatterplot](https://github.com/motebrian/EVALUATING-THE-ASSOCIATION-BETWEEN-GDP-AND-LIFE-EXPECTANCY-IN-DIFFERENT-COUNTRIES/assets/90248185/98fabefc-6495-4696-9b76-4ff29769c7ac)

## Conclusion
The analysis reveals a positive correlation between GDP and life expectancy. Countries with higher GDPs tend to have higher life expectancies. This project underscores the importance of economic factors in determining health outcomes.




