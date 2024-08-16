# Crop Yield Prediction

## Overview
The goal of this project is to predict crop yield based on various agricultural parameters using a dataset containing information on rainfall, temperature, fertilizer, and macronutrients. The dataset was sourced from the Crop Yield Prediction dataset.

## Data Dictionary
The dataset includes the following columns:
- **Rain Fall (mm)**: Rainfall in millimeters
- **Temperature (C)**: Temperature in Celsius
- **Fertilizer (kg)**: Fertilizer in kilograms
- **Nitrogen (N)**: Nitrogen macro nutrient
- **Phosphorous (P)**: Phosphorous macro nutrient
- **Potassium (K)**: Potassium macro nutrient
- **Yield (Q/acres)**: Crop yield in quintals per acre

## Data Preprocessing
1. **Loading the Data**:
    ```python
    import pandas as pd
    df = pd.read_excel("crop yield data sheet.xlsx")
    ```

2. **Handling Missing Values**:
    - Converted temperature data type from object to float.
    - Dropped invalid values and replaced missing values with the median of each column.

3. **Descriptive Statistics**:
    - Provided summary statistics for each feature in the dataset.

## Exploratory Data Analysis (EDA)
- **Rainfall Distribution**: Revealed two clusters indicating different crop types.
- **Fertilizer Distribution**: Showed potential proportional relationship with crop yield.
- **Temperature Distribution**: Indicated two clusters suggesting different crop types.
- **Macronutrients Distribution**: Demonstrated the importance of Nitrogen and Phosphorous, with Potassium having lesser but still significant variability.
- **Correlation Analysis**: Illustrated relationships between features and crop yield.

## Model Building
1. **Train-Test Split**:
    ```python
    from sklearn.model_selection import train_test_split
    X_train, X_test, y_train, y_test = train_test_split(df.drop('Yield (Q/acres)', axis=1), df['Yield (Q/acres)'], test_size=0.2, random_state=42)
    ```

2. **Models Used**:
    - **Decision Tree Regressor**
    - **Random Forest Regressor**

3. **Hyperparameter Tuning**:
    - Used GridSearchCV to find the best parameters for both models.

4. **Training and Evaluation**:
    - **Decision Tree Regressor**: Achieved an R2 score of 0.770.
    - **Random Forest Regressor**: Achieved an R2 score of 0.803, outperforming the Decision Tree model.

## Model Evaluation
- **Performance Metrics**:
    ```python
    from sklearn.metrics import mean_squared_error, mean_absolute_error, r2_score
    print("Decision Tree Regressor")
    print("Mean Squared Error: ", mean_squared_error(y_test, d_pred))
    print("Mean Absolute Error: ", mean_absolute_error(y_test, d_pred))
    print("R2 Score: ", r2_score(y_test, d_pred))

    print("\nRandom Forest Regressor")
    print("Mean Squared Error: ", mean_squared_error(y_test, r_pred))
    print("Mean Absolute Error: ", mean_absolute_error(y_test, r_pred))
    print("R2 Score: ", r2_score(y_test, r_pred))
    ```

- **Feature Importance**:
    - Temperature was identified as the most important feature for predicting crop yield, followed by rainfall and macronutrients.

## Conclusion
The dataset suggests the presence of two distinct crop types due to the observed clusters in rainfall, temperature, and yield. The Random Forest Regressor outperforms the Decision Tree Regressor in predicting crop yield. Temperature is the most influential feature in predicting yield, followed by rainfall. Macronutrients play a lesser role but still contribute to the prediction.

## Future Work
- Incorporate additional features such as soil type and crop breed.
- Experiment with other advanced models and techniques to improve prediction accuracy.

## Requirements
- Python 3.x
- Pandas
- NumPy
- Matplotlib
- Seaborn
- scikit-learn
- Openpyxl
