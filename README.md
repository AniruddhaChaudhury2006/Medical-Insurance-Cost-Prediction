# Insurance Cost Prediction Project

## Introduction
This project aims to predict medical insurance costs using a Linear Regression model. The goal is to understand the factors influencing insurance charges and build a predictive model based on various individual attributes.

## Dataset
The dataset used for this project is `insurance.csv`. It contains the following features:
- `age`: Age of the primary beneficiary
- `sex`: Gender of the primary beneficiary (male/female)
- `bmi`: Body Mass Index
- `children`: Number of children covered by health insurance
- `smoker`: Whether the beneficiary is a smoker (yes/no)
- `region`: Residential area of the beneficiary in the US (northeast, southeast, southwest, northwest)
- `charges`: Individual medical costs billed by health insurance (target variable)

## Data Preprocessing
The following steps were performed to prepare the data for modeling:
- **Handling Missing Values**: Checked for and confirmed no missing values in the dataset.
- **Encoding Categorical Features**: Categorical features (`sex`, `smoker`, `region`) were converted into numerical representations using one-hot encoding.
  - `sex`: 'male' -> 0, 'female' -> 1
  - `smoker`: 'yes' -> 0, 'no' -> 1
  - `region`: 'southeast' -> 0, 'southwest' -> 1, 'northeast' -> 2, 'northwest' -> 3

## Exploratory Data Analysis (EDA)
Exploratory data analysis was conducted to understand the distribution of features and their relationships with insurance charges. Visualizations were created for:
- Age distribution
- Sex distribution
- BMI distribution
- Number of children distribution
- Smoker distribution
- Region distribution
- Charges distribution

## Model Training
- The dataset was split into training and testing sets (80% training, 20% testing).
- A Linear Regression model was trained on the preprocessed training data.

## Model Evaluation
The model's performance was evaluated using the R-squared metric:
- **R-squared value for training data**: 0.7515
- **R-squared value for test data**: 0.7447

These R-squared values indicate that approximately 75% of the variance in insurance charges can be explained by the model.

## How to Make Predictions
To predict insurance costs for a new individual, provide the input features in the same order and encoded format as used during training. For example:

```python
input_data = (age, sex_encoded, bmi, children, smoker_encoded, region_encoded)
# Example: (27, 0, 42.13, 0, 0, 0) -> age=27, male, bmi=42.13, 0 children, smoker=yes, region=southeast

# Convert to numpy array and reshape
input_data_as_numpy_array = np.asarray(input_data)
input_data_reshaped = input_data_as_numpy_array.reshape(1, -1)

# Make prediction
prediction = regressor.predict(input_data_reshaped)
print("Insurance cost in USD ", prediction[0])
```
