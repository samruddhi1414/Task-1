# Task-1
Data Cleaning and Preprocessing

[sales_dataa.csv](https://github.com/user-attachments/files/19835904/sales_dataa.csv)
![image](https://github.com/user-attachments/assets/6e1ea6b7-cbab-499f-a01c-6be162493e59)

import pandas as pd

# Load the dataset
df = pd.read_csv("sales_dataa.csv", encoding='latin1')

# Basic info
print("Original Data Shape:", df.shape)
print(df.info())

# Checking for missing values
print("\nMissing values per column:\n", df.isnull().sum())

# Droping rows with missing critical values 
df_cleaned = df.dropna(subset=['QUANTITYORDERED', 'PRICEEACH', 'ORDERDATE'])

# Filling less critical missing values 
df_cleaned['ADDRESSLINE2'].fillna("N/A", inplace=True)
df_cleaned['STATE'].fillna("Unknown", inplace=True)
df_cleaned['POSTALCODE'].fillna("00000", inplace=True)

# Removing duplicates
df_cleaned = df_cleaned.drop_duplicates()

# Converting ORDERDATE to datetime format
df_cleaned['ORDERDATE'] = pd.to_datetime(df_cleaned['ORDERDATE'], errors='coerce')

# Rename columns for readability 
df_cleaned.rename(columns={
    'QUANTITYORDERED': 'Quantity',
    'PRICEEACH': 'UnitPrice',
    'ORDERDATE': 'OrderDate',
    'CUSTOMERNAME': 'CustomerName'
}, inplace=True)

# Final check
print("\nCleaned Data Shape:", df_cleaned.shape)
print(df_cleaned.head())

# Save the cleaned file
df_cleaned.to_csv("cleaned_sales_data.csv", index=False)
print("Cleaned dataset saved as 'cleaned_sales_data.csv'")


Output:
![image](https://github.com/user-attachments/assets/a86588db-338f-43ff-8faf-c2dc1e9e9e01)
![image](https://github.com/user-attachments/assets/a60be1b3-d9f8-47ef-860d-078b91e32229)
![image](https://github.com/user-attachments/assets/68d128bc-75b8-4173-9ef8-5a875ef9d613)
![image](https://github.com/user-attachments/assets/4ede9d00-f353-406d-b090-79c7da2fe098)
Cleaned dataset saved as 'cleaned_sales_data.csv'
<ipython-input-2-edd6e3f371ba>:17: FutureWarning: A value is trying to be set on a copy of a DataFrame or Series through chained assignment using an inplace method.
The behavior will change in pandas 3.0. This inplace method will never work because the intermediate object on which we are setting values always behaves as a copy.

For example, when doing 'df[col].method(value, inplace=True)', try using 'df.method({col: value}, inplace=True)' or df[col] = df[col].method(value) instead, to perform the operation inplace on the original object.


  df_cleaned['ADDRESSLINE2'].fillna("N/A", inplace=True)
<ipython-input-2-edd6e3f371ba>:18: FutureWarning: A value is trying to be set on a copy of a DataFrame or Series through chained assignment using an inplace method.
The behavior will change in pandas 3.0. This inplace method will never work because the intermediate object on which we are setting values always behaves as a copy.

For example, when doing 'df[col].method(value, inplace=True)', try using 'df.method({col: value}, inplace=True)' or df[col] = df[col].method(value) instead, to perform the operation inplace on the original object.


  df_cleaned['STATE'].fillna("Unknown", inplace=True)
<ipython-input-2-edd6e3f371ba>:19: FutureWarning: A value is trying to be set on a copy of a DataFrame or Series through chained assignment using an inplace method.
The behavior will change in pandas 3.0. This inplace method will never work because the intermediate object on which we are setting values always behaves as a copy.

For example, when doing 'df[col].method(value, inplace=True)', try using 'df.method({col: value}, inplace=True)' or df[col] = df[col].method(value) instead, to perform the operation inplace on the original object.


  df_cleaned['POSTALCODE'].fillna("00000", inplace=True)

[cleaned_sales_data.csv](https://github.com/user-attachments/files/19835935/cleaned_sales_data.csv)

Data Cleaning Report: Sales Dataset

For this task, I used a sales dataset containing information on product orders, customer details, sales values, and order status. The dataset had 24 columns and included fields such as ORDERDATE, QUANTITYORDERED, PRICEEACH, CUSTOMERNAME, and STATUS.

During cleaning:
I checked for missing values and removed rows missing key data like quantity, price, or order date.Columns such as STATE and POSTALCODE with minor missing values were filled with default values like 'Unknown' and '00000'.
Duplicate rows were identified and removed.
The ORDERDATE column was converted to a proper datetime format for easy analysis.Column names were simplified for readability, such as renaming QUANTITYORDERED to Quantity.
After cleaning, the dataset was saved as cleaned_sales_data.csv. It is now ready for further analysis or visualization.


In the preprocessing stage
 I extracted new features from the OrderDate such as year, month, and day. I also created a TotalSale column by multiplying quantity and unit price to help with future revenue analysis. Text data in columns like CustomerName and ProductLine were standardized to lowercase and stripped of whitespace. Lastly, the Status column was encoded into numerical values using label encoding, making the dataset more suitable for further analysis or modeling.




Sales Data Cleaning & Preprocessing

Overview
This project involves cleaning and preprocessing a sales dataset that includes customer orders, order dates, product details, and sales values.

Tasks Completed
- Removed missing and duplicate records
- Converted `OrderDate` to datetime format
- Renamed and standardized column names
- Extracted new features: `Year`, `Month`, `Day`, `TotalSale`
- Encoded the `Status` column using label encoding

Output
- Final cleaned file: `cleaned_sales_data.csv`

Tools Used
- Python (Pandas)
- Google Colab


