# Pandas Quiz - In-Class Assessment

## Part 1: Fundamentals (Why Pandas, Series, DataFrame)

### Question 1 (Multiple Choice)
What is the main advantage of using Pandas over NumPy for data analysis?

A) Pandas is faster than NumPy  
B) Pandas can only work with numeric data  
C) Pandas provides labeled data structures and handles heterogeneous data types  
D) Pandas uses less memory than NumPy  

**Answer: C**  
*Explanation: Pandas provides labeled axes (rows and columns) and can handle different data types within the same DataFrame, making it more suitable for real-world data analysis.*

---

### Question 2 (Multiple Choice)
Which of the following statements about Pandas Series is TRUE?

A) A Series can contain multiple data types in the same object  
B) A Series is a two-dimensional labeled data structure  
C) A Series is a one-dimensional labeled array capable of holding any data type  
D) A Series cannot have a custom index  

**Answer: C**  
*Explanation: A Pandas Series is one-dimensional and can hold any data type (integers, strings, floats, Python objects, etc.) with labeled indices.*

---

### Question 3 (Code Analysis)
Given the following code:
```python
import pandas as pd
data = {'Name': ['Alice', 'Bob', 'Charlie'], 
        'Age': [25, 30, 35]}
df = pd.DataFrame(data)
print(df.shape)
```

What will be the output?

A) (3, 2)  
B) (2, 3)  
C) 6  
D) [3, 2]  

**Answer: A**  
*Explanation: The DataFrame has 3 rows and 2 columns, so shape returns (3, 2) as a tuple (rows, columns).*

---

## Part 2: Indexing & Slicing

### Question 4 (Multiple Choice)
What is the difference between `loc[]` and `iloc[]` in Pandas?

A) `loc[]` is faster than `iloc[]`  
B) `loc[]` uses label-based indexing, while `iloc[]` uses integer position-based indexing  
C) `loc[]` is for columns only, `iloc[]` is for rows only  
D) There is no difference, they are interchangeable  

**Answer: B**  
*Explanation: `loc[]` accesses data by labels/names, while `iloc[]` accesses data by integer positions (like NumPy arrays).*

---

### Question 5 (Code Completion)
Complete the code to select rows where Age is greater than 25 AND City is 'NYC':

```python
df_filtered = df[_________________]
```

A) `df['Age'] > 25 & df['City'] == 'NYC'`  
B) `(df['Age'] > 25) and (df['City'] == 'NYC')`  
C) `(df['Age'] > 25) & (df['City'] == 'NYC')`  
D) `df['Age'] > 25 && df['City'] == 'NYC'`  

**Answer: C**  
*Explanation: In Pandas, use `&` (not `and`) for element-wise logical AND operations, and parentheses are required around each condition.*

---

### Question 6 (Code Analysis)
Given a DataFrame `df`, what does the following code return?
```python
df.iloc[1:4, 0:2]
```

A) Rows 1 to 4 (inclusive) and columns 0 to 2 (inclusive)  
B) Rows 1 to 3 and columns 0 to 1  
C) The second, third, and fourth rows with the first two columns  
D) Both B and C are correct  

**Answer: D**  
*Explanation: `iloc[1:4, 0:2]` uses Python's slicing convention: rows 1, 2, 3 (not 4) and columns 0, 1 (not 2). This is the second through fourth rows with the first two columns.*

---

## Part 3: Query and Functions

### Question 7 (Multiple Choice)
Which method would you use to apply a custom function to each element in a DataFrame column?

A) `apply()`  
B) `map()`  
C) `transform()`  
D) Both A and B can work  

**Answer: D**  
*Explanation: Both `apply()` and `map()` can apply functions to Series (DataFrame columns). `apply()` is more versatile and works on DataFrames, while `map()` is specifically for Series.*

---

### Question 8 (Code Analysis)
What does the following query return?
```python
df.query('Age >= 30 and Salary < 80000')
```

A) A Boolean mask  
B) A DataFrame with rows where Age ≥ 30 AND Salary < 80000  
C) A Series with True/False values  
D) An error because the syntax is incorrect  

**Answer: B**  
*Explanation: The `query()` method returns a filtered DataFrame based on the boolean expression provided as a string.*

---

### Question 9 (Multiple Choice)
Which function would you use to get summary statistics (count, mean, std, min, max, etc.) for numeric columns?

A) `df.info()`  
B) `df.describe()`  
C) `df.summary()`  
D) `df.stats()`  

**Answer: B**  
*Explanation: `df.describe()` generates descriptive statistics for numerical columns, including count, mean, std, min, quartiles, and max.*

---

## Part 4: Concatenate DataFrames

### Question 10 (Multiple Choice)
What is the default axis for `pd.concat([df1, df2])`?

A) axis=0 (concatenate vertically/row-wise)  
B) axis=1 (concatenate horizontally/column-wise)  
C) axis='index'  
D) It depends on the shape of the DataFrames  

**Answer: A**  
*Explanation: By default, `pd.concat()` concatenates along axis=0, which means stacking DataFrames vertically (adding rows).*

---

### Question 11 (Code Analysis)
Given two DataFrames:
```python
df1 = pd.DataFrame({'A': [1, 2], 'B': [3, 4]})
df2 = pd.DataFrame({'A': [5, 6], 'B': [7, 8]})
result = pd.concat([df1, df2], ignore_index=True)
```

What will be the index of the resulting DataFrame?

A) [0, 1, 0, 1]  
B) [0, 1, 2, 3]  
C) [1, 2, 5, 6]  
D) [0, 0, 1, 1]  

**Answer: B**  
*Explanation: `ignore_index=True` creates a new continuous integer index [0, 1, 2, 3] instead of preserving the original indices.*

---

## Part 5: Merge & Join

### Question 12 (Multiple Choice)
What is the default join type for `pd.merge()`?

A) left  
B) right  
C) outer  
D) inner  

**Answer: D**  
*Explanation: The default join type for `pd.merge()` is 'inner', which keeps only the rows with matching keys in both DataFrames.*

---

### Question 13 (Scenario-Based)
You have two DataFrames:
- `customers`: columns [customer_id, name, city]
- `orders`: columns [order_id, customer_id, amount]

You want to keep ALL customers even if they have no orders. Which merge should you use?

A) `pd.merge(customers, orders, on='customer_id', how='inner')`  
B) `pd.merge(customers, orders, on='customer_id', how='left')`  
C) `pd.merge(customers, orders, on='customer_id', how='right')`  
D) `pd.merge(customers, orders, on='customer_id', how='outer')`  

**Answer: B**  
*Explanation: A left join keeps all rows from the left DataFrame (customers) and matches from the right DataFrame (orders), preserving customers without orders (with NaN for order fields).*

---

### Question 14 (Multiple Choice)
What's the difference between `merge()` and `join()`?

A) No difference, they do the same thing  
B) `merge()` joins on columns, `join()` joins on indices by default  
C) `merge()` is faster than `join()`  
D) `join()` can only do inner joins  

**Answer: B**  
*Explanation: `merge()` typically joins on column values (specified by 'on' parameter), while `join()` joins on index by default (though both can be configured differently).*

---

## Part 6: Aggregation and Grouping

### Question 15 (Multiple Choice)
What does the following code do?
```python
df.groupby('Department')['Salary'].mean()
```

A) Calculates the mean salary for the entire DataFrame  
B) Groups by Salary and calculates mean for each Department  
C) Groups by Department and calculates the mean salary for each group  
D) Returns a DataFrame with all columns  

**Answer: C**  
*Explanation: This groups the data by Department, selects the Salary column, and computes the mean for each department group.*

---

### Question 16 (Code Analysis)
Given:
```python
df.groupby('Category').agg({'Price': ['min', 'max'], 'Quantity': 'sum'})
```

What does this code return?

A) A Series with aggregated values  
B) A DataFrame with multi-level columns showing min/max price and sum of quantity per category  
C) An error because you can't use different aggregations  
D) Only the Price column aggregations  

**Answer: B**  
*Explanation: The `agg()` function allows multiple aggregation functions per column, returning a DataFrame with hierarchical columns.*

---

### Question 17 (Multiple Choice)
Which method would you use to apply multiple different aggregation functions to different columns after grouping?

A) `apply()`  
B) `agg()` or `aggregate()`  
C) `transform()`  
D) `combine()`  

**Answer: B**  
*Explanation: `agg()` (or its alias `aggregate()`) is designed for applying different aggregation functions to different columns in a grouped DataFrame.*

---

### Question 18 (True/False)
After using `groupby()`, the result always has the grouped column(s) as the index.

A) True  
B) False  

**Answer: B**  
*Explanation: While `groupby()` makes the grouped column(s) the index by default, you can use `as_index=False` parameter to keep them as regular columns.*

---

## Part 7: Pivot Tables

### Question 19 (Multiple Choice)
What is the main difference between `pivot()` and `pivot_table()` in Pandas?

A) `pivot()` is faster than `pivot_table()`  
B) `pivot_table()` can handle duplicate values and supports aggregation functions, while `pivot()` cannot  
C) `pivot()` can only work with numeric data  
D) There is no difference between them  

**Answer: B**  
*Explanation: `pivot()` requires unique index/column combinations and doesn't aggregate. `pivot_table()` can handle duplicates by applying aggregation functions (mean, sum, etc.) and is more flexible.*

---

### Question 20 (Code Analysis)
Given the following DataFrame:
```python
df = pd.DataFrame({
    'Date': ['2024-01', '2024-01', '2024-02', '2024-02'],
    'Product': ['A', 'B', 'A', 'B'],
    'Sales': [100, 150, 120, 180]
})
```

What does this code produce?
```python
result = df.pivot(index='Date', columns='Product', values='Sales')
```

A) A DataFrame with Date as rows, Product as columns, and Sales as values  
B) A DataFrame with Product as rows and Date as columns  
C) A Series with sales values  
D) An error because there are duplicate entries  

**Answer: A**  
*Explanation: `pivot()` reshapes the data with 'Date' as row index, 'Product' names as column headers, and 'Sales' values filling the cells. No error occurs here because each Date-Product combination is unique.*

---

## Advanced Interview Questions

### Question 21 (System Design - Memory Optimization)
You need to load a 10GB CSV file into a Pandas DataFrame, but your system only has 8GB RAM available. The file contains 50 columns, but you only need 5 specific columns for analysis. What strategies would you use to handle this efficiently?

**Expected Answer (Multiple strategies):**

1. **Use `usecols` parameter:**
```python
df = pd.read_csv('large_file.csv', usecols=['col1', 'col2', 'col3', 'col4', 'col5'])
```

2. **Specify optimal dtypes to reduce memory:**
```python
dtypes = {
    'col1': 'int32',      # instead of int64
    'col2': 'float32',    # instead of float64
    'col3': 'category',   # for categorical data
    'col4': 'int8',       # for small integers
    'col5': 'string'      # for text
}
df = pd.read_csv('large_file.csv', usecols=list(dtypes.keys()), dtype=dtypes)
```

3. **Read in chunks:**
```python
chunk_size = 100000
chunks = []
for chunk in pd.read_csv('large_file.csv', usecols=['col1', 'col2', 'col3', 'col4', 'col5'], 
                          chunksize=chunk_size):
    # Process each chunk
    processed_chunk = chunk[chunk['col1'] > 0]  # Example filter
    chunks.append(processed_chunk)
df = pd.concat(chunks, ignore_index=True)
```

4. **Use Dask or alternatives for out-of-core computation:**
```python
import dask.dataframe as dd
df = dd.read_csv('large_file.csv', usecols=['col1', 'col2', 'col3', 'col4', 'col5'])
result = df.compute()  # Only when needed
```

**Key Points:**
- Selecting only necessary columns can reduce memory by 90% (5/50 columns)
- Using appropriate dtypes: int32 uses 50% less memory than int64
- Category dtype for repeated strings can save 80-90% memory
- Chunking allows processing data larger than RAM
- Lazy evaluation (Dask) loads data only when needed

*Explanation: This tests understanding of memory management, practical problem-solving, and knowledge of Pandas optimization techniques - common in real-world data engineering interviews.*

---

### Question 22 (Code Interview - Data Transformation)
**Scenario:** You have a sales transaction log with the following structure:

```python
transactions = pd.DataFrame({
    'customer_id': [1, 1, 2, 2, 2, 3, 3, 1],
    'product': ['A', 'B', 'A', 'C', 'A', 'B', 'A', 'C'],
    'amount': [100, 150, 100, 200, 100, 150, 100, 200],
    'date': ['2024-01-01', '2024-01-02', '2024-01-01', 
             '2024-01-02', '2024-01-03', '2024-01-01', 
             '2024-01-02', '2024-01-03']
})
```

**Task:** Write code to find customers who:
1. Made purchases on at least 3 different dates
2. Bought at least 2 different products
3. Have total spending > $300

Return their customer_id, total_spending, num_dates, and num_products, sorted by total_spending descending.

**Expected Output:**
```
   customer_id  total_spending  num_dates  num_products
0            1             650          3             3
1            2             400          3             2
```

**Solution:**
```python
result = transactions.groupby('customer_id').agg(
    total_spending=('amount', 'sum'),
    num_dates=('date', 'nunique'),
    num_products=('product', 'nunique')
).reset_index()

result = result[
    (result['num_dates'] >= 3) & 
    (result['num_products'] >= 2) & 
    (result['total_spending'] > 300)
].sort_values('total_spending', ascending=False)

print(result)
```

**Alternative Solution (using query):**
```python
result = (transactions.groupby('customer_id')
          .agg(total_spending=('amount', 'sum'),
               num_dates=('date', 'nunique'),
               num_products=('product', 'nunique'))
          .reset_index()
          .query('num_dates >= 3 and num_products >= 2 and total_spending > 300')
          .sort_values('total_spending', ascending=False))
```

**Key Concepts Tested:**
- Complex aggregation with multiple conditions
- Using `agg()` with named aggregations (Pandas 0.25+)
- `nunique()` for counting distinct values
- Chaining multiple filtering conditions
- Method chaining for cleaner code

*Explanation: This is a typical data analyst/scientist interview question that tests groupby, aggregation, filtering, and ability to translate business logic into code.*

---

## Bonus Challenge Question

### Question 23 (Code Writing)
Write code to find the top 3 products with the highest average price in each category:

```python
# Given DataFrame df with columns: Category, Product, Price
result = df.groupby(['Category', 'Product'])['Price'].mean() \
           .groupby(level='Category') \
           .nlargest(3) \
           .reset_index()
```

**Alternative acceptable answer:**
```python
result = df.groupby(['Category', 'Product'])['Price'].mean() \
           .reset_index() \
           .groupby('Category') \
           .apply(lambda x: x.nlargest(3, 'Price')) \
           .reset_index(drop=True)
```

*Explanation: This groups by both Category and Product to get average prices, then within each Category finds the 3 products with highest average prices.*

---

## Quick Reference Summary

**Total Questions: 23**
- Part 1 (Fundamentals): 3 questions
- Part 2 (Indexing & Slicing): 3 questions  
- Part 3 (Query & Functions): 3 questions
- Part 4 (Concatenate): 2 questions
- Part 5 (Merge & Join): 3 questions
- Part 6 (Aggregation & Grouping): 4 questions
- Part 7 (Pivot Tables): 2 questions
- Advanced Interview Questions: 2 questions
- Bonus: 1 question

**Suggested Time:** 
- Regular Quiz (Q1-Q20): 30-35 minutes
- With Interview Questions (Q21-Q22): 45-50 minutes

---

## Answer Key (Quick Reference)

**Basic Questions (Q1-Q20):**
1. C | 2. C | 3. A | 4. B | 5. C | 6. D | 7. D | 8. B | 9. B | 10. A | 11. B | 12. D | 13. B | 14. B | 15. C | 16. B | 17. B | 18. B | 19. B | 20. A

**Interview Questions (Q21-Q22):** See detailed solutions above

**Bonus (Q23):** Code answer

---

## Usage Notes for Instructors

- **Q1-Q20**: Suitable for in-class quiz (30-35 minutes)
- **Q21-Q22**: Use for:
  - Advanced students seeking challenge
  - Job interview preparation sessions
  - Take-home assignments
  - Discussion topics for practical applications
- **Q23**: Optional bonus for extra credit
