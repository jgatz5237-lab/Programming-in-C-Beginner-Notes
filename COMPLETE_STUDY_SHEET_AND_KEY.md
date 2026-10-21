---
title: 2D Array Study Sheet & Skeleton Key - Coding Guide
author: GitHub Copilot Tutoring
date: September 1, 2026
geometry: margin=1in
documentclass: article
fontsize: 12pt
linestretch: 1.5
colorlinks: true
---

# 2D ARRAY STUDY SHEET & SKELETON KEY
## Complete Coding Guide for Java 2D Arrays

---

## TABLE OF CONTENTS

1. Core Concepts
2. Understanding the Code Structure
3. Practice Problems with Solutions
4. Method Writing Guide
5. Common Mistakes
6. Quick Reference

---

## PART 1: CORE CONCEPTS TO MEMORIZE

### What is a 2D Array?

A **2D array** is a table of data with rows and columns, like a spreadsheet.

```
Visual Example: 3 rows × 4 columns

     Col 0   Col 1   Col 2   Col 3
    ┌─────────────────────────────┐
Row 0│ [0][0] [0][1] [0][2] [0][3]│
Row 1│ [1][0] [1][1] [1][2] [1][3]│
Row 2│ [2][0] [2][1] [2][2] [2][3]│
    └─────────────────────────────┘
```

**Key Point:** Access elements with TWO indices: `array[row][column]`

### Declaration and Creation

```java
// Declare a 2D array
double[][] arrayData;

// Create it with specific dimensions
arrayData = new double[5][10];  // 5 rows, 10 columns

// Or declare and create in one line
double[][] data = new double[3][4];
```

### Understanding [i][j]

- **i** = row index (vertical position)
- **j** = column index (horizontal position)
- **array[i][j]** = element at row i, column j

**Example:**
```
array[2][3] means: Go to row 2, column 3
```

---

## PART 2: UNDERSTANDING THE CODE STRUCTURE

### The Array2d Class - Complete Code

```java
public class Array2d {
    // Member Variables
    public double[][] arrayData;    // The 2D array of numbers
    int rows;                        // Number of rows
    int cols;                        // Number of columns
    
    // Constructor
    public Array2d(int rows, int cols) {
        this.rows = rows;
        this.cols = cols;
        this.arrayData = new double[rows][cols];
    }
    
    // Print Method
    public void printArray() {
        int i, j;
        for(i = 0; i < this.rows; i++) {
            for(j = 0; j < this.cols; j++) {
                System.out.printf("%-7.2f", this.arrayData[i][j]);
            }
            System.out.println();
        }
    }
}
```

### Step-by-Step: Constructor

```java
Array2d A = new Array2d(3, 5);
```

**What happens:**

| Step | Action | Result |
|------|--------|--------|
| 1 | `new Array2d(3, 5)` | Creates new object |
| 2 | `this.rows = 3` | Sets rows to 3 |
| 3 | `this.cols = 5` | Sets columns to 5 |
| 4 | `new double[3][5]` | Creates 3×5 grid |
| Final | Object ready | Can store 15 doubles |

### Step-by-Step: fillArray() Method

```java
public static void fillArray(Array2d A) {
    int i, j;
    
    for(i = 0; i < A.rows; i++) {           // Loop rows
        for(j = 0; j < A.cols; j++) {       // Loop columns
            A.arrayData[i][j] = i + j/10.0; // Fill cell
        }
    }
}
```

**Complete Trace for 2×3 array:**

```
Starting with empty 2×3 array

OUTER LOOP: i=0
  INNER LOOP: j=0 → [0][0] = 0 + 0/10 = 0.0
  INNER LOOP: j=1 → [0][1] = 0 + 1/10 = 0.1
  INNER LOOP: j=2 → [0][2] = 0 + 2/10 = 0.2
  (Inner loop ends)

OUTER LOOP: i=1
  INNER LOOP: j=0 → [1][0] = 1 + 0/10 = 1.0
  INNER LOOP: j=1 → [1][1] = 1 + 1/10 = 1.1
  INNER LOOP: j=2 → [1][2] = 1 + 2/10 = 1.2
  (Inner loop ends)

FINAL ARRAY:
0.0  0.1  0.2
1.0  1.1  1.2
```

### Understanding printf("%-7.2f")

```
%-7.2f breakdown:
│ │ │ │ └─ f = floating point number
│ │ │ └─── .2 = 2 decimal places
│ │ └───── 7 = field width (7 characters)
│ └─────── - = left-align
└───────── % = start format specification

Example outputs:
0.0  becomes  "0.00  " (0.00 left-aligned, 7 chars total)
1.23 becomes  "1.23  " (1.23 left-aligned, 7 chars total)
```

---

## PART 3: PRACTICE PROBLEMS WITH SOLUTIONS

### Problem 1: Calculate Array Values

**Question:** For a 2×3 array with formula `i + j/10.0`, find:
- array[0][0] = ?
- array[1][2] = ?
- array[0][1] = ?

**Solution:**

```
Formula: array[i][j] = i + j/10.0

array[0][0]:
  i=0, j=0
  = 0 + 0/10.0 = 0.0 ✓

array[1][2]:
  i=1, j=2
  = 1 + 2/10.0 = 1.2 ✓

array[0][1]:
  i=0, j=1
  = 0 + 1/10.0 = 0.1 ✓
```

---

### Problem 2: Predict Full Output

**Question:** What will this code print?

```java
Array2d A = new Array2d(2, 4);
fillArray(A);
A.printArray();
```

**Solution:**

Step 1: Dimensions are 2×4 (2 rows, 4 columns)

Step 2: fillArray() uses formula: `i + j/10.0`

Step 3: Calculate each row:
```
Row 0 (i=0):
  [0][0] = 0.0, [0][1] = 0.1, [0][2] = 0.2, [0][3] = 0.3

Row 1 (i=1):
  [1][0] = 1.0, [1][1] = 1.1, [1][2] = 1.2, [1][3] = 1.3
```

Step 4: Output:
```
0.00  0.10  0.20  0.30
1.00  1.10  1.20  1.30
```

---

### Problem 3: Loop Counting

**Question:** For a 3×5 array, how many times does each line execute?

```java
for(int i = 0; i < A.rows; i++) {              // Line 1
    for(int j = 0; j < A.cols; j++) {          // Line 2
        A.arrayData[i][j] = i + j/10.0;        // Line 3
    }
    System.out.println();                      // Line 4
}
```

**Solution:**

| Line | Count | Why |
|------|-------|-----|
| Line 1 | 3 times | Outer loop: i goes 0→1→2 |
| Line 2 | 15 times | Inner loop: 5 per outer × 3 outer = 15 |
| Line 3 | 15 times | Inside inner loop: executes once per iteration |
| Line 4 | 3 times | After inner loop: executes once per outer iteration |

---

## PART 4: METHOD WRITING GUIDE

### Method Template: findMax()

**What it does:** Finds the largest value in the array

```java
public double findMax() {
    // Step 1: Initialize with first element
    double max = this.arrayData[0][0];
    
    // Step 2: Check every element
    for(int i = 0; i < this.rows; i++) {
        for(int j = 0; j < this.cols; j++) {
            
            // Step 3: Update if we find bigger
            if(this.arrayData[i][j] > max) {
                max = this.arrayData[i][j];
            }
        }
    }
    
    // Step 4: Return the maximum
    return max;
}
```

**Example Trace:**
```
Array:     0.0  0.1  0.2
           1.0  1.1  1.2

max = 0.0 (start)
Check 0.0: No → stays 0.0
Check 0.1: Yes → max = 0.1
Check 0.2: Yes → max = 0.2
Check 1.0: Yes → max = 1.0
Check 1.1: Yes → max = 1.1
Check 1.2: Yes → max = 1.2

return 1.2
```

---

### Method Template: findSum()

**What it does:** Adds up all elements

```java
public double findSum() {
    // Step 1: Start with sum of 0
    double sum = 0;
    
    // Step 2: Loop through every element
    for(int i = 0; i < this.rows; i++) {
        for(int j = 0; j < this.cols; j++) {
            
            // Step 3: Add to sum
            sum += this.arrayData[i][j];
        }
    }
    
    // Step 4: Return the sum
    return sum;
}
```

**Example Trace:**
```
Array:     1.0  2.0
           3.0  4.0

sum = 0
Add 1.0 → sum = 1.0
Add 2.0 → sum = 3.0
Add 3.0 → sum = 6.0
Add 4.0 → sum = 10.0

return 10.0
```

---

### Method Template: findAverage()

**What it does:** Finds the average of all elements

```java
public double findAverage() {
    // Step 1: Sum all elements
    double sum = 0;
    for(int i = 0; i < this.rows; i++) {
        for(int j = 0; j < this.cols; j++) {
            sum += this.arrayData[i][j];
        }
    }
    
    // Step 2: Calculate total elements
    double totalElements = this.rows * this.cols;
    
    // Step 3: Divide sum by total
    return sum / totalElements;
}
```

**Important:** Must divide by `rows × cols`, NOT just `rows`!

---

### Method Template: countAbove()

**What it does:** Counts how many values exceed a threshold

```java
public int countAbove(double threshold) {
    // Step 1: Start count at 0
    int count = 0;
    
    // Step 2: Check every element
    for(int i = 0; i < this.rows; i++) {
        for(int j = 0; j < this.cols; j++) {
            
            // Step 3: Increment if above threshold
            if(this.arrayData[i][j] > threshold) {
                count++;
            }
        }
    }
    
    // Step 4: Return the count
    return count;
}
```

**Example:**
```
Array:       1.0  2.0  3.0
             4.0  5.0  6.0

countAbove(3.5) = 3
(counts 4.0, 5.0, 6.0)
```

---

### Method Template: rowSum()

**What it does:** Sums a specific row

```java
public double rowSum(int row) {
    // Step 1: Start sum at 0
    double sum = 0;
    
    // Step 2: Loop through columns in that row
    for(int j = 0; j < this.cols; j++) {
        sum += this.arrayData[row][j];
    }
    
    // Step 3: Return sum
    return sum;
}
```

**Key Difference from findSum():**
- Only loops through ONE row (parameter)
- Still loops through ALL columns
- No outer loop for i

---

### Method Template: colSum()

**What it does:** Sums a specific column

```java
public double colSum(int col) {
    // Step 1: Start sum at 0
    double sum = 0;
    
    // Step 2: Loop through rows in that column
    for(int i = 0; i < this.rows; i++) {
        sum += this.arrayData[i][col];
    }
    
    // Step 3: Return sum
    return sum;
}
```

**Key Difference from rowSum():**
- Loops through ALL rows
- Only ONE column (parameter)
- Access as [i][col]

---

## PART 5: COMMON MISTAKES TO AVOID

### Mistake 1: Confusing Rows and Columns

**❌ WRONG:**
```java
Array2d A = new Array2d(10, 5);  // Which is rows? Which is cols?
```

**✓ RIGHT:**
```java
Array2d A = new Array2d(5, 10);  // rows=5, cols=10
                                  // Read left to right: 5 rows, 10 cols
```

---

### Mistake 2: Forgetting .0 in Division

**❌ WRONG:**
```java
A.arrayData[i][j] = i + j/10;  // Integer division! j/10 = 0 or 1
```

**✓ RIGHT:**
```java
A.arrayData[i][j] = i + j/10.0;  // Decimal division! j/10.0 = 0.1, 0.2, etc
```

**Why?**
```
7/10 in Java = 0 (integer division, discards decimal)
7/10.0 in Java = 0.7 (decimal division, keeps decimal)
```

---

### Mistake 3: Wrong Loop Bounds

**❌ WRONG:**
```java
for(int i = 0; i <= A.rows; i++)      // Goes 0, 1, 2, 3, 4, 5 (but only 0-4 exist!)
for(int j = 0; j <= A.cols; j++)      // ArrayIndexOutOfBoundsException!
```

**✓ RIGHT:**
```java
for(int i = 0; i < A.rows; i++)       // Goes 0, 1, 2, 3, 4 (exactly right!)
for(int j = 0; j < A.cols; j++)       // Safe access
```

---

### Mistake 4: Dividing by Wrong Number in Average

**❌ WRONG:**
```java
return sum / this.rows;  // Only divides by rows, not total elements!
```

**✓ RIGHT:**
```java
return sum / (this.rows * this.cols);  // Total number of elements
```

**Example of error:**
```
2×3 array: 6 elements total
Wrong: sum / 2 (divides by rows)
Right: sum / 6 (divides by rows × cols)
```

---

### Mistake 5: Starting Max at 0

**❌ WRONG:**
```java
double max = 0;  // What if array has all negative numbers?
```

**✓ RIGHT:**
```java
double max = this.arrayData[0][0];  // Start with actual element
```

**Example of error:**
```
Array: -5.0  -3.0  -2.0  -1.0
Wrong max = 0 (returns 0, but max should be -1.0!)
Right max = -5.0, then updates to -1.0
```

---

### Mistake 6: Forgetting this. Keyword

**❌ WRONG:**
```java
public double findMax() {
    double max = arrayData[0][0];  // Where does arrayData come from?
}
```

**✓ RIGHT:**
```java
public double findMax() {
    double max = this.arrayData[0][0];  // Refers to member variable
}
```

---

## PART 6: QUICK REFERENCE

### Key Formulas

| Task | Formula | Example |
|------|---------|---------|
| Total elements | rows × cols | 5 × 10 = 50 |
| Access element | array[i][j] | array[2][3] |
| Fill with formula | array[i][j] = formula | i + j/10.0 |
| Count iterations | outer × inner | 3 × 4 = 12 |

### Common Loop Patterns

**Loop through entire array:**
```java
for(int i = 0; i < this.rows; i++) {
    for(int j = 0; j < this.cols; j++) {
        // Process array[i][j]
    }
}
```

**Loop through one row:**
```java
for(int j = 0; j < this.cols; j++) {
    // Process array[row][j]
}
```

**Loop through one column:**
```java
for(int i = 0; i < this.rows; i++) {
    // Process array[i][col]
}
```

**Loop through diagonal:**
```java
for(int i = 0; i < Math.min(this.rows, this.cols); i++) {
    // Process array[i][i]
}
```

---

### Method Return Types

| Method | Returns | Example |
|--------|---------|---------|
| findMax() | double | 4.9 |
| findMin() | double | 0.0 |
| findSum() | double | 50.25 |
| findAverage() | double | 3.5 |
| countAbove() | int | 15 |
| rowSum() | double | 7.5 |
| colSum() | double | 12.3 |

---

### Variable Naming Convention

| Name | Meaning | Type |
|------|---------|------|
| i | row index | int |
| j | column index | int |
| rows | number of rows | int |
| cols | number of columns | int |
| arrayData | the 2D array | double[][] |
| max | maximum value | double |
| sum | sum of elements | double |
| count | number of items | int |

---

## STUDY CHECKLIST

- [ ] Can explain what a 2D array is
- [ ] Can access element at [i][j]
- [ ] Can trace nested loops
- [ ] Can calculate values with formula i + j/10.0
- [ ] Can predict array output
- [ ] Can write findMax() from memory
- [ ] Can write findSum() from memory
- [ ] Can write findAverage() from memory
- [ ] Can identify common mistakes
- [ ] Can explain why ≤ is wrong but < is right
- [ ] Can explain why j/10 is wrong but j/10.0 is right
- [ ] Can explain why start with arrayData[0][0] for max

---

## ADDITIONAL PRACTICE PROBLEMS

### Problem A: Different Formula

**Question:** For a 3×3 array with formula `i * j`, what is the output?

**Answer:**
```
0.00  0.00  0.00
0.00  1.00  2.00
0.00  2.00  4.00
```

---

### Problem B: Identify the Formula

**Given output:**
```
0.00  1.00  2.00  3.00
1.00  2.00  3.00  4.00
2.00  3.00  4.00  5.00
```

**What's the formula?** `i + j`

---

### Problem C: Count Method Calls

**Code:**
```java
Array2d A = new Array2d(4, 6);
fillArray(A);
A.printArray();
```

**How many times does printf() execute?** `4 × 6 = 24 times`

---

## FINAL TIPS FOR SUCCESS

1. **Always use < not ≤** in loops for arrays
2. **Always use /10.0 not /10** for decimal division
3. **Always start max with first element** not 0
4. **Always divide by rows × cols** for average, not just rows
5. **Always use this.** to refer to member variables
6. **Always trace code on paper** before running it
7. **Always check loop bounds** match array dimensions

---

## CONCLUSION

You now have:
- ✅ Complete understanding of 2D arrays
- ✅ Step-by-step methods for common tasks
- ✅ Common mistakes to avoid
- ✅ Quick reference for formulas and patterns

**Practice the problems, memorize the templates, and you'll master 2D arrays!**

