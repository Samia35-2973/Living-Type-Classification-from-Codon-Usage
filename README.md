# Living Type Classification from Codon Usage

In this project, I participated in a hackathon where I worked with a raw codon usage dataset. The goal was to classify the data into different living types by cleaning the data thoroughly. The classes of the 'type' were:

- bacteria
- virus
- plant
- bacteriophage
- mammal
- vertebrate
- invertebrate
- rodent
- archaea
- primate
- plasmid

## Directory Structure

```
- codon-usage-dataset-partially-cleaned
    - dna_test - dna_test.csv.csv
    - train_replaced_missing_values.csv
- Raw Data
    - dna_sample_submission.csv
    - dna_test.csv
    - dna_train.csv
- output
    - submission3.csv
    - submission4.csv
    - submission5.csv
- living-type-classification-from-codon-usage.ipynb
```

### Data Cleaning

1. **Handling Missing Values**: The first step was to load the raw data (`dna_train.csv` and `dna_test.csv`) into Excel, where I addressed string values indicating `NaN`. These string values caused the column's data type to be recognized as `Object`. Once cleaned, the columns were automatically formatted with the correct data types. The cleaned datasets were saved as:
   - `train_replaced_missing_values.csv`
   - `dna_test - dna_test.csv.csv`

2. **Exploratory Data Analysis (EDA)**: After inspecting the data, I performed EDA to identify and impute remaining missing values. I used data distribution analysis to impute numerical variables. During this analysis, I identified an issue with the `uuu` column, which contained a string value among the float values. This was corrected and handled.

3. **Encoding Categorical Data**: After cleaning and imputation, I encoded categorical data for model training.

### Model Training

I trained the following models:

1. **RandomForestClassifier**: 
   ```python
   r_mod = RandomForestClassifier(n_estimators=100, random_state=42)
   ```

2. **XGBoost Classifier**: 
   ```python
   x_mod = XGBClassifier(objective='multi:softmax', n_estimators=100, random_state=42)
   ```

3. **Optimized XGBoost Classifier**:
   ```python
   xm = XGBClassifier(objective='multi:softmax', n_estimators=500, learning_rate=0.5, random_state=42)
   ```

### Results

- **Random Forest Results**:
  - Accuracy: 0.8399
  - Precision: 0.8468
  - Recall: 0.8399
  - F1-Score: 0.8252

- **XGBoost Results**:
  - Accuracy: 0.8910
  - Precision: 0.8899
  - Recall: 0.8910
  - F1-Score: 0.8865

### Submission Files

The results were saved in the following files:
- `submission3.csv`
- `submission4.csv`
- `submission5.csv`

## How to Run

1. Clone this repository.
2. Open the `living-type-classification-from-codon-usage.ipynb` notebook.
3. Load the cleaned datasets: `train_replaced_missing_values.csv` and `dna_test - dna_test.csv.csv`.
4. Replace the train data path under the "Understanding Data" section and the test data path under the "Test Data Preparation" section of the notebook (use the `read_csv()` function).
5. Run the notebook.

Alternatively, you can start from scratch by using the raw data files (`dna_train.csv` and `dna_test.csv`) and following the cleaning and preprocessing steps in the notebook.
