# Analyzing London Transport Crime Through Linear Regression and K-Means Clustering

# London Transport Crime Analysis

This project investigates crime patterns across London’s transportation network using **Linear Regression** and **K-Means Clustering**. The goal is to understand how crimes on different transport modes contribute to the total crime count and identify high and low-crime clusters. These insights aim to support public safety improvements through better resource allocation and targeted interventions.

---

## Dataset

- **Source**: Data obtained from the [London Datastore](https://data.london.gov.uk/dataset/transport-crime-london), spanning **April 2009 to March 2023**.
- **Features**:
  - Temporal Data: `YEAR`, `MONTH_NO`.
  - Transport Modes: Crime counts for:
    - `BUS_CRIMES` (Buses)
    - `UG-DLR_CRIMES` (Underground/DLR)
    - `OG_CRIMES` (Overground)
    - `TL_CRIMES` (Tramlink)
    - `TFL_RAIL_CRIMES` (TfL Rail)
  - `TOTAL_CRIMES`: Aggregate crime count across all modes.
- **Preprocessing**:
  - Handled missing values (e.g., null rows for `TFL_RAIL_CRIMES`).
  - Merged columns (e.g., `UG-DLR_CRIMES` for consistency across years).
  - Added derived columns such as `TOTAL_CRIMES`.

---

## Methods

### 1. Linear Regression

Linear Regression was employed to analyze the relationship between total crimes and each transport mode.

#### Objective:
To predict `TOTAL_CRIMES` based on crimes for individual transport modes.

#### Process:
- Used **Ordinary Least Squares (OLS)** Regression for each mode (e.g., `BUS_CRIMES`, `UG-DLR_CRIMES`) against `TOTAL_CRIMES`.
- Derived equations of the line:
  \[
  Y = \beta_0 + \beta_1 X
  \]
  - \( Y \): Predicted `TOTAL_CRIMES`.
  - \( \beta_0 \): Intercept (constant term).
  - \( \beta_1 \): Coefficient for the independent variable \( X \) (e.g., `BUS_CRIMES`).

#### OLS Summary Report:
- Example for **Underground/DLR Crimes**:
  - Equation: \( Y = 15.32 + 1.67 X \)
  - Metrics:
    - **R-squared = 0.72**: Strong positive relationship.
    - **RMSE = 302.76**: Low prediction error.

![image](https://github.com/user-attachments/assets/12ba8416-c4e2-4ceb-a257-f68bac033824)

![image](https://github.com/user-attachments/assets/b139c0ef-700a-483b-92d7-6904ac2269a4)


#### Key Findings:
- **Strongest relationship**: Underground/DLR crimes (\( R^2 = 0.72 \)).
- **Weakest relationship**: Overground crimes (\( R^2 = 0.06 \)).
- **Moderate relationship**: Bus crimes (\( R^2 = 0.54 \)) and Tramlink crimes (\( R^2 = 0.30 \)).

---

### 2. K-Means Clustering

K-Means Clustering was used to group transport modes based on their crime rates.

#### Objective:
To cluster transport modes into high and low-crime groups.

#### Process:
1. **Elbow Method**:
   - Determined the optimal number of clusters (\( k=3 \)) by plotting the **Sum of Squared Errors (SSE)** for \( k=1 \) to \( 10 \).
   - The "elbow" in the curve indicated the best \( k \) value.

  ![image](https://github.com/user-attachments/assets/b19773a5-521d-49cf-8274-0c2fcef1cfc0)

    
2. **Clustering**:
   - Features were scaled using `StandardScaler`.
   - K-Means was applied with \( k=3 \), resulting in:
     - **High-crime cluster**: Bus and Underground/DLR.
     - **Low-crime cluster**: Overground and Tramlink.
    
    
3. **Visualization**:
   - Plots with centroids highlighted showed distinct high and low-crime clusters.


    ![image](https://github.com/user-attachments/assets/622e22e0-acf6-41e7-851b-afc9e244a2f4)

    ![image](https://github.com/user-attachments/assets/910f24fd-7812-4352-8731-9d9030233306)

---

## Conclusion

### Linear Regression Findings:
- Crimes on Underground/DLR and buses are major contributors to total crimes.
- Overground and Tramlink crimes have weaker correlations with total crimes.

### K-Means Clustering Insights:
- High-crime modes (Bus, Underground/DLR) are distinct from low-crime modes (Overground, Tramlink).
- The clustering results enable targeted safety measures, such as focusing resources on high-crime clusters.

This analysis highlights the potential of machine learning and statistical methods to improve public safety in urban transit systems.

---
