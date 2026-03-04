# NumPy Class Exercises
## Based on Chapter 3 Slides

---

## Exercise 1: Create 1D Array (Slide 6)
**Difficulty**: ⭐

Create a 1D array with values [5, 10, 15, 20, 25].
Then print:
1. The first element
2. The last element
3. Elements from index 1 to 3

**Expected Output**:
```
First element: 5
Last element: 25
Elements [1:3]: [10 15]
```

**Solution**:
```python
import numpy as np

x = np.array([5, 10, 15, 20, 25])
print("First element:", x[0])
print("Last element:", x[-1])
print("Elements [1:3]:", x[1:3])
```

---

## Exercise 2: Create 2D Array (Slide 7)
**Difficulty**: ⭐

Create a 2D array:
```
[[1, 2, 3],
 [4, 5, 6],
 [7, 8, 9]]
```

Then print:
1. The shape of the array
2. The element at row 1, column 2
3. The entire second row

**Expected Output**:
```
Shape: (3, 3)
Element at [1,2]: 6
Second row: [4 5 6]
```

**Solution**:
```python
import numpy as np

arr = np.array([[1, 2, 3],
                [4, 5, 6],
                [7, 8, 9]])

print("Shape:", arr.shape)
print("Element at [1,2]:", arr[1, 2])
print("Second row:", arr[1])
```

---

## Exercise 3: Array Slicing (Slide 5 & 7)
**Difficulty**: ⭐⭐

Given this array:
```python
arr = np.array([[10, 20, 30, 40],
                [50, 60, 70, 80],
                [90, 100, 110, 120]])
```

Extract:
1. The first two rows and first two columns
2. All elements in column 2
3. Elements in the last row

**Expected Output**:
```
First 2x2:
[[10 20]
 [50 60]]

Column 2: [30 70 110]

Last row: [90 100 110 120]
```

**Solution**:
```python
import numpy as np

arr = np.array([[10, 20, 30, 40],
                [50, 60, 70, 80],
                [90, 100, 110, 120]])

print("First 2x2:")
print(arr[:2, :2])

print("\nColumn 2:", arr[:, 2])

print("\nLast row:", arr[-1])
# or arr[2]
```

---

## Exercise 4: Array Copy (Slides 9-10)
**Difficulty**: ⭐⭐

Create an array and demonstrate the difference between:
1. Copying by reference (changes affect original)
2. Using .copy() method (changes don't affect original)

**Task**:
```python
original = np.array([1, 2, 3, 4, 5])
```

Create two copies:
- One using simple assignment
- One using .copy()

Change the first element to 99 in both copies and observe what happens.

**Solution**:
```python
import numpy as np

original = np.array([1, 2, 3, 4, 5])
print("Original:", original)

# Copy by reference
ref_copy = original
ref_copy[0] = 99
print("\nAfter changing ref_copy[0] to 99:")
print("Original:", original)  # Changed!
print("ref_copy:", ref_copy)

# Reset
original = np.array([1, 2, 3, 4, 5])

# Copy using .copy()
real_copy = original.copy()
real_copy[0] = 99
print("\nAfter changing real_copy[0] to 99:")
print("Original:", original)  # Not changed!
print("real_copy:", real_copy)
```

---

## Exercise 5: Using np.arange() (Slide 13)
**Difficulty**: ⭐⭐

Use `np.arange()` to create an array from 0 to 20 with step 2.
Then reshape it into a 2x5 array.

**Expected Output**:
```
Original: [ 0  2  4  6  8 10 12 14 16 18]
Reshaped:
[[ 0  2  4  6  8]
 [10 12 14 16 18]]
```

**Solution**:
```python
import numpy as np

arr = np.arange(0, 20, 2)
print("Original:", arr)

reshaped = arr.reshape(2, 5)
print("Reshaped:")
print(reshaped)
```

---

## Exercise 6: Array Math Functions (Slide 11)
**Difficulty**: ⭐⭐

Given this array of test scores:
```python
scores = np.array([85, 92, 78, 90, 88, 76, 95, 89])
```

Calculate:
1. The sum of all scores
2. The mean (average) score
3. The maximum score
4. The minimum score

**Expected Output**:
```
Sum: 693
Mean: 86.625
Max: 95
Min: 76
```

**Solution**:
```python
import numpy as np

scores = np.array([85, 92, 78, 90, 88, 76, 95, 89])

print("Sum:", np.sum(scores))
print("Mean:", np.mean(scores))
print("Max:", np.max(scores))
print("Min:", np.min(scores))
```

---

## Exercise 7: Working with Columns and Rows
**Difficulty**: ⭐⭐

Given a 2D array representing student scores in 3 subjects:
```python
# Rows: students, Columns: [Math, English, Science]
scores = np.array([[85, 90, 78],
                   [92, 88, 95],
                   [78, 85, 82],
                   [88, 92, 90]])
```

Calculate:
1. Average score for each student (row-wise)
2. Average score for each subject (column-wise)

**Hint**: Use `axis=0` for columns, `axis=1` for rows

**Expected Output**:
```
Student averages: [84.33 91.67 81.67 90.0]
Subject averages: [85.75 88.75 86.25]
```

**Solution**:
```python
import numpy as np

scores = np.array([[85, 90, 78],
                   [92, 88, 95],
                   [78, 85, 82],
                   [88, 92, 90]])

student_avg = np.mean(scores, axis=1)
print("Student averages:", student_avg)

subject_avg = np.mean(scores, axis=0)
print("Subject averages:", subject_avg)
```

---

## Exercise 8: Find Maximum Position
**Difficulty**: ⭐⭐

Create an array of random numbers and find:
1. The maximum value
2. The index of the maximum value

**Example**:
```python
data = np.array([23, 45, 12, 67, 34, 89, 56])
```

**Expected Output**:
```
Maximum value: 89
Index of max: 5
```

**Solution**:
```python
import numpy as np

data = np.array([23, 45, 12, 67, 34, 89, 56])

max_value = np.max(data)
max_index = np.argmax(data)

print("Maximum value:", max_value)
print("Index of max:", max_index)
```

---

## Exercise 9: Temperature Analysis
**Difficulty**: ⭐⭐⭐

You have temperature readings for 5 days (morning, noon, evening):
```python
temps = np.array([[15, 22, 18],  # Day 1
                  [16, 24, 19],  # Day 2
                  [14, 23, 17],  # Day 3
                  [17, 25, 20],  # Day 4
                  [15, 23, 18]]) # Day 5
```

Find:
1. The average temperature for each day
2. The highest temperature recorded
3. Which day had the highest average temperature

**Solution**:
```python
import numpy as np

temps = np.array([[15, 22, 18],
                  [16, 24, 19],
                  [14, 23, 17],
                  [17, 25, 20],
                  [15, 23, 18]])

# 1. Average per day
daily_avg = np.mean(temps, axis=1)
print("Daily averages:", daily_avg)

# 2. Highest temperature
highest = np.max(temps)
print("Highest temperature:", highest)

# 3. Day with highest average
best_day = np.argmax(daily_avg)
print("Day with highest average: Day", best_day + 1)
print("Average temperature:", daily_avg[best_day])
```

---

## Exercise 10: Create Special Arrays
**Difficulty**: ⭐

Create the following arrays:
1. Array of 5 zeros
2. Array of 4 ones
3. Identity matrix (3x3)
4. Array of 6 elements all equal to 7

**Solution**:
```python
import numpy as np

# 1. Zeros
zeros = np.zeros(5)
print("Zeros:", zeros)

# 2. Ones
ones = np.ones(4)
print("Ones:", ones)

# 3. Identity matrix
identity = np.eye(3)
print("Identity matrix:")
print(identity)

# 4. Array of 7s
sevens = np.full(6, 7)
print("Sevens:", sevens)
```

---

## Challenge Exercise: Grade Calculator
**Difficulty**: ⭐⭐⭐

You have scores for 4 students in 3 exams:
```python
exam_scores = np.array([[85, 78, 92],  # Student 1
                        [90, 88, 85],  # Student 2
                        [75, 80, 78],  # Student 3
                        [95, 92, 98]]) # Student 4
```

Write code to:
1. Find each student's average score
2. Find which student has the highest average
3. Find the class average for each exam
4. Count how many students have an average above 85

**Solution**:
```python
import numpy as np

exam_scores = np.array([[85, 78, 92],
                        [90, 88, 85],
                        [75, 80, 78],
                        [95, 92, 98]])

# 1. Each student's average
student_avg = np.mean(exam_scores, axis=1)
print("Student averages:", student_avg)

# 2. Student with highest average
best_student = np.argmax(student_avg)
print(f"Best student: Student {best_student + 1}")
print(f"Average: {student_avg[best_student]:.2f}")

# 3. Class average per exam
exam_avg = np.mean(exam_scores, axis=0)
print("Exam averages:", exam_avg)

# 4. Count students with average > 85
high_performers = np.sum(student_avg > 85)
print(f"Students with average > 85: {high_performers}")
```

---

## Quick Reference

**Important Functions (from Slide 11)**:
- `np.array()` - Create array
- `np.arange()` - Create range of values
- `np.reshape()` - Change array shape
- `np.sum()` - Sum of elements
- `np.mean()` - Average of elements
- `np.max()` - Maximum value
- `np.min()` - Minimum value
- `np.argmax()` - Index of maximum value
- `.copy()` - Create a real copy

**Indexing Tips**:
- `arr[0]` - First element
- `arr[-1]` - Last element
- `arr[1:4]` - Elements from index 1 to 3
- `arr[:, 0]` - First column (2D)
- `arr[0, :]` - First row (2D)

**Axis Parameter**:
- `axis=0` - Operates on rows (column-wise calculation)
- `axis=1` - Operates on columns (row-wise calculation)
