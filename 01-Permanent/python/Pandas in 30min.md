---
From: youtube
created: 2025-08-09
tags:
  - "#python"
  - "#pythonlib"
source: https://www.youtube.com/watch/EXIgjIBu4EU
---
---

## **1. Points Covered in the Video**

### **Intro & Setup**

- Importance of **Pandas** for data science, AI, ML, and data visualization.
- Recommended editors: **VS Code**, **Cursor**, or **PyCharm**.
- Working from:
    - **.py files** for scripts.
    - **Jupyter Notebooks** for interactive exploration.
- Installing Pandas:
    - `uv install pandas` 

---
### **Core Pandas Concepts**

**📦 What Is Pandas?** → open-source Py library for **data manipulation and analysis**

```lua
Pandas has 2 data type:
	├── 01. DataFrame → 2D labeled data structure (like a spreadsheet or SQL table)
	├── 02. Series    → 1D labeled array (like a single column or row).
```

### 📊 What Is a DataFrame?

A **DataFrame** is a two-dimensional, tabular data structure with labeled rows and columns. Think of it as a Python-native spreadsheet — but way more powerful and programmable.
### ✅ Key Features:
- Label-based indexing
- Column-wise and row-wise operations
- Support for mixed data types
- Fast, vectorized operations (built on NumPy)
---
### Manually Creating a DF

```python
import pandas as pd

data = {
    'Name': ['Alice', 'Bob', 'Charlie'],
    'Age': [25, 30, 35],
    'Country': ['USA', 'Canada', 'UK']
}

df = pd.DataFrame(data)
print(df)
```
#### output
```markdown 
    Name   Age Country
0   Alice   25     USA
1     Bob   30  Canada
2 Charlie   35      UK
```

### **Core Operations**

```python
.
├── Load Data           ←  CSV, Excel, Dictionary.
├── Inspect             ←  head(), tail(), info(), describe(), columns(), index().
├── Select Data         ←  by column, row (iloc, loc).
├── Filter Data         ←  by condition, multiple conditions, string matching, isin().
├── Modify Data         ←  change cell values, apply transformations.
├── Delete Rows         ←  drop().
├── Clean Data          ←  dropna(), fillna(), rename columns.
├── Aggregate & Analyze ←  value_counts(), groupby(), sort_values().
├── Save Data           ←  to_csv().
```
---
### 📁**Loading Data**

- From CSV:
```python
df = pd.read_csv("orders.csv")
```

- From Excel:
```python
df = pd.read_excel("file.xlsx")
```

- From dictionary:
```python
df = pd.DataFrame({"Name": [...], "Age": [...]})
```

---
### ⛳**Selecting Data**

#### By Column:

- Single column (Series): `df["Country"]`   
- Multiple columns (DataFrame): `df[["Country", "Product"]]`    

#### By Row:

- **iloc** (index location): `df.iloc[0]`, `df.iloc[10]`    
- **loc** (label-based): `df.loc[df["Customer Name"] == "Anna"]` 

---

### 🧪**Filtering**

- Basic condition:
```python
df[df["Category"] == "Electronics"]
```

- Multiple conditions:    
    - AND: `(cond1) & (cond2)`
    - OR: `(cond1) | (cond2)`

- Comparisons: `>`, `<`, `<=`, `!=`

- String filters:
    - `.str.startswith("A")`
    - `.str.endswith("a")`

- Membership:
```python
df[df["Country"].isin(["USA", "Sweden"])]
```
    Negate with `~`.

---
### ✏️**Modifying Data**

- Update with `.loc`:
```python
df.loc[df["Customer Name"] == "Anna", "Product"] = "Tim"
```

- Change all matches:    
```python
df.loc[df["Country"] == "USA", "Country"] = "United States"
```

- Apply transformation:    
```python
df["Country"] = df["Country"].str.upper()
```

---
### ❌**Deleting Data**

- Remove rows by index:
```python
df = df.drop(39)
```

---

### 🧹**Cleaning Data**

- Drop missing:
```python
df.dropna()
```

- Fill missing:    
```python
df.fillna(0, inplace=True)
```

- Rename columns:    
```python
df.rename(columns={"OrderID": "Order ID"}, inplace=True)
```

---
### 📅**Aggregations & Analysis**

- Count values:
```python
 df["Country"].value_counts()
```

- Group by:    
```python
df.groupby("Country")["Price"].sum()
```

- Sort values:    
```python
df.sort_values("Price", ascending=False)
```
---

### 💾**Saving Data**

- To CSV:
```python
df.to_csv("new_file.csv", index=False)
```

---

## :luc_settings: **Pandas Cheat Sheet**

```python
# Import
import pandas as pd

# Load
df = pd.read_csv("file.csv")
df = pd.read_excel("file.xlsx")
df = pd.DataFrame({"col1": [...], "col2": [...]})

# Exploring Data (Inspect)
df.head()         # First 5 rows
df.tail()         # Last 5 rows
df.info()         # Summary info metadata (entries, columns, types).
df.describe()     # Stats summary
df.columns        # list of column names
df.index          # Index range info

# Select
df["Col"]                   # Single column (Series)
df[["Col1", "Col2"]]        # Multiple columns
df.iloc[0]                  # Row by index
df.loc[df["Col"] == value]  # Row by condition

# Filter
df[df["Col"] == val]
df[(df["A"] > 2) & (df["B"] == "X")]
df["Col"].str.startswith("A")
df["Col"].isin(["X", "Y"])
~df["Col"].isin(["X", "Y"]) # ~ is for reversing the condition like - (bare)

# Modify
df.loc[cond, "Col"] = new_value
df["Col"] = df["Col"].str.upper()

# Delete
df = df.drop(index)

# Clean
df.dropna()
df.fillna(value, inplace=True)
df.rename(columns={"old": "new"}, inplace=True)

# Aggregate
df["Col"].value_counts()
df.groupby("Col")["NumCol"].sum()
df.sort_values("NumCol", ascending=False)

# Save
df.to_csv("output.csv", index=False)
```

---

