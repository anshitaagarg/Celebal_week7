# 🚀 Delta Lake MERGE Implementation using Azure Databricks

## 📌 Overview

This project demonstrates **incremental data processing** using **Delta Lake** in **Azure Databricks**. The assignment focuses on implementing the **MERGE (Upsert)** operation to efficiently update existing records and insert new records into a Delta table.

The project follows a complete data engineering workflow including data loading, cleaning, Delta table creation, incremental data simulation, MERGE operation, and result validation.

---

## 🎯 Objective

The objective of this assignment is to:

- Load a CSV dataset into a Delta Table
- Perform basic data cleaning
- Simulate incremental data
- Apply the Delta Lake MERGE operation
- Validate the final dataset
- Understand incremental processing using Delta Lake

---

## 🛠️ Technology Stack

| Technology | Purpose |
|------------|---------|
| Azure Databricks | Data Processing Platform |
| Apache Spark 4.1.0 | Distributed Data Processing |
| PySpark | Data Transformation |
| Delta Lake | ACID Storage Layer |
| Python | Programming Language |

---

## 📂 Project Structure

```
delta-lake-assignment/
│
├── data/
│   ├── customer_master.csv
│   └── customer_incremental.csv
│
├── notebooks/
│   └── delta_merge_assignment.ipynb
│
├── screenshots/
│   ├── data_loading/
│   ├── data_cleaning/
│   ├── scd1/
│   ├── validation/
│   └── final_output/
│
├── Assignment_Summary.pdf 
│
└── README.md
```

---

# 📊 Dataset

**Dataset Used**

Superstore Dataset

The dataset contains sales transaction information including:

- Customer Details
- Product Details
- Sales
- Profit
- Quantity
- Shipping Information

---

# ⚙️ Workflow

## Step 1: Load Dataset

- Imported CSV into a PySpark DataFrame
- Explored schema
- Verified row count

---

## Step 2: Data Cleaning

Performed:

- Null value analysis
- Duplicate record check
- Standardized column names
- Prepared cleaned DataFrame

---

## Step 3: Create Delta Table

Converted the cleaned DataFrame into a Delta Table.

```python
df_clean.write \
    .format("delta") \
    .mode("overwrite") \
    .saveAsTable("week7_databricks.assignment.customer_master_delta")
```

---

## Step 4: Simulate Incremental Data

Created an incremental dataset containing:

- Existing customer records (Update)
- New customer records (Insert)

---

## Step 5: Delta MERGE Operation

Applied Delta Lake MERGE to perform an Upsert.

```python
delta_table.alias("target") \
.merge(
    incremental_df.alias("source"),
    "target.Row_ID = source.Row_ID"
) \
.whenMatchedUpdate(...) \
.whenNotMatchedInsertAll() \
.execute()
```

---

## Step 6: Validation

Validated the implementation by checking:

- Final row count
- Duplicate records
- Updated records
- Newly inserted records

---

# 📈 Results

 Dataset loaded successfully

 Delta Table created successfully

 No missing values found

 No duplicate records found

 Incremental dataset created

 Existing records updated successfully

 New records inserted successfully
 
 MERGE operation completed successfully
 
 Final dataset validated

---

# 💡 Why Delta Lake?

Delta Lake extends Apache Spark with:

- ACID Transactions
- Schema Enforcement
- Time Travel
- Data Versioning
- Efficient MERGE Operations
- Scalable Incremental Processing

These capabilities make Delta Lake an ideal choice for modern Data Engineering pipelines.

---

# ✅ Conclusion

This project successfully demonstrates an end-to-end incremental data processing workflow using Delta Lake on Azure Databricks. By implementing the MERGE operation, both record updates and new record insertions were handled efficiently within a single transaction. The project highlights industry-standard practices for building reliable, scalable, and ACID-compliant data pipelines.

---

## 👩‍💻 Author

**Anshita Garg**

B.Tech (AI & ML)

DIT University

Data Engineering Intern | Celebal Technologies
