
---

## What `headers="keys"` does

When you pass `headers="keys"` to `tabulate`, you are telling tabulate: _“My data is a list of dicts (or has keys), so use the dict keys as the column headers”_.

Here’s how it works:

- Suppose your data is:

```python
data = [
    {"Name": "Alice", "Age": 30},
    {"Name": "Bob", "Age": 25},
]
```

- When you call:

```python
print(tabulate(data, headers="keys", tablefmt="grid"))
```

what `tabulate` does is:

1. It inspects all the dicts in `data` and gets the union of all keys (or a consistent set of keys) across rows.

2. It decides that those keys (e.g. `"Name"`, `"Age"`) are your column headers.

3. For each row (each dict), it fetches values in that key order (or consistent ordering). If a dict doesn’t have a key, it may substitute a “missing value” placeholder.    

4. Then it formats a table with those header names and the corresponding values under each column, applying alignment, width, etc.


So `headers="keys"` is a convenience: you don’t have to separately supply a list of column names; tabulate will derive them from your dict keys.

In contrast, if you pass `headers` as a list (e.g. `["Name", "Age"]`) while your data is a list of dicts, tabulate complains because it expects in that case a mapping (or a keyword) rather than a bare list for that type of input. That’s why you got the error earlier — you passed `headers=self.header` (a list) while your data was a list of dicts, rather than telling tabulate to use the keys.

---

## How **tabulate** works in general (overview)

Tabulate is a library for converting structured data into nicely formatted textual tables. It handles a variety of input formats and provides many output styles. Here is a high-level explanation of how it works:

1. **Accept different input formats**  
    Tabulate accepts:
    
    - A _list of lists_ (or generally an iterable of iterables)
    - A _list of dicts_
    - A _dict of iterables_ (keys = columns)
    - Pandas DataFrames, NumPy arrays, etc.
    - Possibly named tuples or other row-like objects
    
    Depending on which format you supply, tabulate chooses how to interpret headers and rows. ([pyneng.readthedocs.io](https://pyneng.readthedocs.io/en/latest/book/12_useful_modules/tabulate.html?utm_source=chatgpt.com "tabulate - Python for network engineers"))
    
2. **Normalize data + headers**  
    It internally transforms the data into a unified internal representation, something like:
    
    - `list_of_lists` (rows),
    - `headers` list,
    
    even if your input was dict-based or other types.
    As part of normalization, it deals with missing values, ensures each row has the same number of columns, etc. ([pyneng.readthedocs.io](https://pyneng.readthedocs.io/en/latest/book/12_useful_modules/tabulate.html?utm_source=chatgpt.com "tabulate - Python for network engineers"))
    
3. **Decide column widths and alignment**  
    Tabulate inspects all rows and headers to compute:
    
    - The maximum width for each column (based on longest cell or header)
    - The types in each column (numeric, string)
	
    - Alignment rules:
        - Numeric columns are usually right-aligned (or aligned at decimal point)
        - Strings are usually left-aligned
        - You can override alignment via parameters like `numalign`, `stralign` ([hanspeterschaub.info](https://hanspeterschaub.info/basilisk/Documentation/utilities/tabulate.html?utm_source=chatgpt.com "tabulate — Basilisk 2.4.0 documentation"))

4. **Configure formatting rules**  
    It supports optional parameters:
	
    - `tablefmt`: controls the style (grid, plain, fancy, pipe, html, etc.)
    - `floatfmt`: how floating-point numbers are displayed (e.g. `".2f"`)
    - `missingval`: what to put when a cell has no value
    - `maxcolwidths`: maximum width for each column (wrap long text)
    - `showindex`: whether to include a row index column        
    - Alignments: `numalign`, `stralign`, `colalign` ([PyPI](https://pypi.org/project/tabulate/?utm_source=chatgpt.com "tabulate"))

5. **Render the table**  
    Once the widths, alignments, and formatted cell strings are ready, tabulate builds the table line by line:
    - Print the header row, underlines or dividers
    - Print each data row
    - Add borders or separators depending on `tablefmt`

For example, with `tablefmt="grid"`, tabulate will draw `+---+---+` style borders. With `plain`, it prints just columns separated by spaces. ([hanspeterschaub.info](https://hanspeterschaub.info/basilisk/Documentation/utilities/tabulate.html?utm_source=chatgpt.com "tabulate — Basilisk 2.4.0 documentation"))
