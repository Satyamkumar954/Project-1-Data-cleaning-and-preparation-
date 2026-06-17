# 🧹 DecodeLabs P1 — Data Cleaning & Preparation

## 📁 Project Files

| File | Description |
|------|-------------|
| `DecodeLabs_P1_Dataset.xlsx` | Original raw dataset (messy) |
| `DecodeLabs_Data_Cleaning.ipynb` | Jupyter Notebook — all cleaning steps |
| `DecodeLabs_P1_Cleaned.csv` | Final cleaned output (CSV) |
| `DecodeLabs_P1_Cleaned.xlsx` | Final cleaned output (Excel) |

---

## ⚙️ Requirements

Install the required libraries before running the notebook:

```
pip install pandas numpy openpyxl
```

If you are using a virtual environment (.venv):

```
.venv\Scripts\pip install pandas numpy openpyxl
```

---

## 🚀 How to Run

1. Open VS Code
2. Open the file `DecodeLabs_Data_Cleaning.ipynb`
3. Select Python kernel (top-right corner → **Select Kernel → Python 3**)
4. In **Step 1**, update the file path:

```python
FILE_PATH = r"C:\Users\shubh\Downloads\DecodeLabs_P1_Dataset.xlsx"
```

5. Click **Run All** — cleaned files will be saved automatically

---

## 🐛 Issues Fixed (15 Total)

| Issue ID | Issue Type | Column | Method Used |
|----------|------------|--------|-------------|
| ISS001, ISS002 | Duplicate Records | All columns | `drop_duplicates(keep='first')` |
| ISS003 | Missing Name | Customer_Name | `fillna('Unknown')` |
| ISS004 | Missing Age | Age | `fillna(median)` |
| ISS005 | Missing Purchase Amount | Purchase_Amount | `fillna(mean)` |
| ISS006 | Missing Email | Email | `fillna('Not Provided')` |
| ISS007 | Missing Status | Status | `fillna(mode)` |
| ISS008 | Wrong Date Format | Join_Date | `pd.to_datetime()` → YYYY-MM-DD |
| ISS009 | Inconsistent Name Case | Customer_Name | `str.title()` |
| ISS010 | Inconsistent City Names | City | `replace()` with mapping |
| ISS011 | Inconsistent Category | Category | `str.title()` |
| ISS012 | Inconsistent Status | Status | `str.title()` |
| ISS013 | Invalid Age Value (999) | Age | `replace(999, NaN)` |
| ISS014 | Negative Purchase Amount | Purchase_Amount | `replace(<0, NaN)` → `fillna(mean)` |
| ISS015 | Extra Whitespace | City | `str.strip()` |

---

## 📊 Notebook Structure

| Step | Description |
|------|-------------|
| Step 0 | Import libraries |
| Step 1 | Load the dataset |
| Step 2 | Initial exploration (dtypes, nulls, duplicates) |
| Step 3 | Fix all 15 issues one by one |
| Step 4 | Final verification (0 nulls, 0 duplicates) |
| Step 5 | Export cleaned data as CSV and Excel |
| Step 6 | Print cleaning summary report |

---

## 📌 Notes

- Always use `r"..."` (raw string) for Windows file paths to avoid errors
- The notebook uses **median** for numeric imputation and **mode** for categorical
- Negative and invalid values are first replaced with `NaN`, then imputed
