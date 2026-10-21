# 2D ARRAY TUTORING SESSION - STEP BY STEP PRACTICE

## PART 1: FOUNDATIONAL CONCEPTS

### What is a 2D Array? (Step by Step)

**Think of it like this:**
- 1D Array = a single row of boxes 📦📦📦📦📦
- 2D Array = a grid/table of boxes

```
Example: 3 rows × 4 columns

     Col 0   Col 1   Col 2   Col 3
    ┌─────────────────────────────┐
Row 0│  [0][0] [0][1] [0][2] [0][3]│
Row 1│  [1][0] [1][1] [1][2] [1][3]│
Row 2│  [2][0] [2][1] [2][2] [2][3]│
    └─────────────────────────────┘
```

**Key Point:** Each cell is accessed by TWO numbers: [row][column]

---

## PART 2: UNDERSTANDING THE CODE STRUCTURE

### The Array2d Constructor - Step By Step

```java
Array2d A = new Array2d(3, 5);
```

**What happens:**
```
Step 1: new Array2d(3, 5) → Creates a new object
Step 2: Constructor runs → Sets this.rows = 3
Step 3: Sets this.cols = 5
Step 4: Creates arrayData = new double[3][5]
Result: A 3×5 grid ready to hold numbers
```

**Visual:**
```
BEFORE: Nothing
AFTER:  A 3×5 grid of empty cells (initialized to 0.0)

    [0][0]  [0][1]  [0][2]  [0][3]  [0][4]
    [1][0]  [1][1]  [1][2]  [1][3]  [1][4]
    [2][0]  [2][1]  [2][2]  [2][3]  [2][4]
```

---

### The fillArray() Method - Step By Step

```java
public static void fillArray(Array2d A) 
{
    int i, j;
    
    for(i = 0; i < A.rows; i++)              // Loop through ROWS
    {
        for(j = 0; j < A.cols; j++)          // Loop through COLUMNS
        {
            A.arrayData[i][j] = i + j/10.0;  // Fill each cell
        }
    }   
}
```

**Let me trace through it for a 2×3 array:**

```
A.rows = 2, A.cols = 3

ITERATION 1:
  i=0, j=0: A.arrayData[0][0] = 0 + 0/10.0 = 0.0
  i=0, j=1: A.arrayData[0][1] = 0 + 1/10.0 = 0.1
  i=0, j=2: A.arrayData[0][2] = 0 + 2/10.0 = 0.2
  (Inner loop ends, go to next row)

ITERATION 2:
  i=1, j=0: A.arrayData[1][0] = 1 + 0/10.0 = 1.0
  i=1, j=1: A.arrayData[1][1] = 1 + 1/10.0 = 1.1
  i=1, j=2: A.arrayData[1][2] = 1 + 2/10.0 = 1.2
  (Inner loop ends, outer loop ends)

FINAL ARRAY:
0.0  0.1  0.2
1.0  1.1  1.2
```

---

## PART 3: GUIDED PRACTICE PROBLEMS

### PRACTICE PROBLEM 1: Trace a Simple Array

**Question:** For a 2×3 array with formula `i + j/10.0`, what is:
- array[0][0] = ?
- array[1][2] = ?
- array[0][1] = ?

**Let me guide you through it:**

```
Formula: array[i][j] = i + j/10.0

array[0][0]:
  i = 0, j = 0
  = 0 + 0/10.0
  = 0.0
  ✓ ANSWER: 0.0

array[1][2]:
  i = 1, j = 2
  = 1 + 2/10.0
  = 1 + 0.2
  = 1.2
  ✓ ANSWER: 1.2

array[0][1]:
  i = 0, j = 1
  = 0 + 1/10.0
  = 0.1
  ✓ ANSWER: 0.1
```

**YOUR TURN - TRY THESE:**

Calculate these without looking at the answer (scroll down when ready):

1. array[2][3] = ?
2. array[1][0] = ?
3. array[3][5] = ?

<details>
<summary>Click to reveal answers</summary>

1. array[2][3] = 2 + 3/10 = 2.3 ✓
2. array[1][0] = 1 + 0/10 = 1.0 ✓
3. array[3][5] = 3 + 5/10 = 3.5 ✓

</details>

---

### PRACTICE PROBLEM 2: Predict the Full Output

**Question:** What will this code print?

```java
Array2d A = new Array2d(2, 4);
fillArray(A);
A.printArray();
```

**Step 1: What are the dimensions?**
- 2 rows, 4 columns
- Total cells = 2 × 4 = 8 cells

**Step 2: What formula fills it?**
- `array[i][j] = i + j/10.0`

**Step 3: Calculate each value:**

```
Row 0 (i=0):
  [0][0] = 0 + 0/10 = 0.0
  [0][1] = 0 + 1/10 = 0.1
  [0][2] = 0 + 2/10 = 0.2
  [0][3] = 0 + 3/10 = 0.3

Row 1 (i=1):
  [1][0] = 1 + 0/10 = 1.0
  [1][1] = 1 + 1/10 = 1.1
  [1][2] = 1 + 2/10 = 1.2
  [1][3] = 1 + 3/10 = 1.3
```

**Step 4: Format the output (7.2f means 7 chars wide, 2 decimals):**

```
0.00  0.10  0.20  0.30
1.00  1.10  1.20  1.30
```

**YOUR TURN:**

Try predicting the output for a 3×3 array. Write out what you think it will print.

<details>
<summary>Answer</summary>

```
0.00  0.10  0.20
1.00  1.10  1.20
2.00  2.10  2.20
```

Did you get it? If yes, you're understanding the pattern! 🎉

</details>

---

### PRACTICE PROBLEM 3: Understand the Loop Structure

**Question:** What does this loop do?

```java
for(i = 0; i < A.rows; i++) {
    for(j = 0; j < A.cols; j++) {
        System.out.print(A.arrayData[i][j] + " ");
    }
    System.out.println();
}
```

**Break it down:**

```
OUTER LOOP: for(i = 0; i < A.rows; i++)
  Purpose: Go through each ROW
  Example: If A.rows = 3, i goes 0 → 1 → 2

  INNER LOOP: for(j = 0; j < A.cols; j++)
    Purpose: Go through each COLUMN in that row
    Example: If A.cols = 4, j goes 0 → 1 → 2 → 3
    
    Action: Print the value at [i][j]
  
  After inner loop finishes: System.out.println()
    Effect: Move to next line (new row in output)
```

**YOUR TURN:**

If A.rows = 2 and A.cols = 3, how many times will:
- The outer loop run? ___
- The inner loop run total? ___
- The print statement execute? ___

<details>
<summary>Answers</summary>

- Outer loop: **2 times** (i = 0, 1)
- Inner loop: **2 × 3 = 6 times total** (3 times per outer loop iteration)
- Print statement: **6 times** (once per inner loop)

</details>

---

## PART 4: MODIFICATION CHALLENGES

### CHALLENGE 1: Change the Formula

**Your Task:** Modify the formula to create a multiplication table.

**Current formula:**
```java
A.arrayData[i][j] = i + j/10.0;
```

**What to change it to:**
```java
A.arrayData[i][j] = i * j;
```

**What will happen:**

```
For a 4×5 array:

Row 0: 0×0=0, 0×1=0, 0×2=0, 0×3=0, 0×4=0
Row 1: 1×0=0, 1×1=1, 1×2=2, 1×3=3, 1×4=4
Row 2: 2×0=0, 2×1=2, 2×2=4, 2×3=6, 2×4=8
Row 3: 3×0=0, 3×1=3, 3×2=6, 3×3=9, 3×4=12

Output:
0.00  0.00  0.00  0.00  0.00
0.00  1.00  2.00  3.00  4.00
0.00  2.00  4.00  6.00  8.00
0.00  3.00  6.00  9.00 12.00
```

**YOUR TURN:**

What would the output be for a 3×3 array with formula `i * j`?

<details>
<summary>Answer</summary>

```
0.00  0.00  0.00
0.00  1.00  2.00
0.00  2.00  4.00
```

</details>

---

### CHALLENGE 2: Add a Method to Find Maximum

**Your Task:** Add this method to the Array2d class

```java
public double findMax() {
    double max = this.arrayData[0][0];  // Start with first element
    
    for(int i = 0; i < this.rows; i++) {
        for(int j = 0; j < this.cols; j++) {
            if(this.arrayData[i][j] > max) {
                max = this.arrayData[i][j];
            }
        }
    }
    return max;
}
```

**Step-by-step explanation:**

```
Step 1: double max = this.arrayData[0][0];
  → Save the first element (0.0) as current max

Step 2: Loop through EVERY cell in the array
  → Compare each value with max

Step 3: if(value > max)
  → If we find a bigger number, update max

Step 4: return max;
  → Give back the largest number found
```

**Example trace (2×3 array with formula i + j/10.0):**

```
Array values:
0.0  0.1  0.2
1.0  1.1  1.2

Execution:
  max = 0.0 (start)
  Check 0.0: 0.0 > 0.0? No
  Check 0.1: 0.1 > 0.0? Yes → max = 0.1
  Check 0.2: 0.2 > 0.1? Yes → max = 0.2
  Check 1.0: 1.0 > 0.2? Yes → max = 1.0
  Check 1.1: 1.1 > 1.0? Yes → max = 1.1
  Check 1.2: 1.2 > 1.1? Yes → max = 1.2
  return 1.2
```

**YOUR TURN:**

For a 3×2 array with formula `i * j`, what would findMax() return?

Array:
```
0  0
0  1
0  2
```

<details>
<summary>Answer</summary>

**findMax() = 2.0**

The largest value in the array is 3×1 = 3... wait let me recalculate:
- [0][0] = 0×0 = 0
- [0][1] = 0×1 = 0
- [1][0] = 1×0 = 0
- [1][1] = 1×1 = 1
- [2][0] = 2×0 = 0
- [2][1] = 2×1 = 2

**Maximum = 2.0** ✓

</details>

---

### CHALLENGE 3: Filter and Print Values

**Your Task:** Modify printArray() to only show values ≥ 1.0

```java
public void printArrayFiltered(double threshold) {
    int i, j;
    
    for(i = 0; i < this.rows; i++) {
        for(j = 0; j < this.cols; j++) {
            if(this.arrayData[i][j] >= threshold) {
                System.out.printf("%-7.2f", this.arrayData[i][j]);
            } else {
                System.out.printf("%-7s", "---");
            }
        }
        System.out.println();
    }
}
```

**How it works:**

```
For each value in the array:
  → IF value >= threshold: print the number
  → ELSE: print "---"
```

**Example: 3×4 array, threshold = 1.0**

Original array:
```
0.0  0.1  0.2  0.3
1.0  1.1  1.2  1.3
2.0  2.1  2.2  2.3
```

After filtering (threshold = 1.0):
```
---   ---   ---   ---
1.00  1.10  1.20  1.30
2.00  2.10  2.20  2.30
```

**YOUR TURN:**

What would the output be for a 2×3 array with threshold = 0.15?

Original:
```
0.0  0.1  0.2
1.0  1.1  1.2
```

<details>
<summary>Answer</summary>

```
---   ---   0.20
1.00  1.10  1.20
```

Explanation:
- Row 0: 0.0 < 0.15 (---), 0.1 < 0.15 (---), 0.2 >= 0.15 (0.20)
- Row 1: 1.0 >= 0.15 (1.00), 1.1 >= 0.15 (1.10), 1.2 >= 0.15 (1.20)

</details>

---

## PART 5: FREE-FORM PROBLEMS (Try on Your Own)

### Problem 1: What's the output?

```java
Array2d A = new Array2d(3, 2);
fillArray(A);  // Uses formula: i + j/10.0
A.printArray();
```

**Write out what you think prints:**

_________________________________

<details>
<summary>Answer</summary>

```
0.00  0.10
1.00  1.10
2.00  2.10
```

</details>

---

### Problem 2: Find the Missing Index

**Given:** Formula is `i + j/10.0`

**If array[?][?] = 3.4, what are the indices?**

Hint: Think about what i and j must be.

<details>
<summary>Answer</summary>

array[3][4] = 3 + 4/10 = 3.4

So i=3 and j=4

</details>

---

### Problem 3: Write the Code

**Task:** Write a method that finds the SUM of all elements in the array.

Hint: Similar to findMax(), but use += instead of >

<details>
<summary>Answer</summary>

```java
public double findSum() {
    double sum = 0;
    
    for(int i = 0; i < this.rows; i++) {
        for(int j = 0; j < this.cols; j++) {
            sum += this.arrayData[i][j];
        }
    }
    return sum;
}
```

</details>

---

### Problem 4: Create a Checkerboard Pattern

**Task:** Change fillArray to create this pattern (for any size array):

```
1.00  0.00  1.00  0.00
0.00  1.00  0.00  1.00
1.00  0.00  1.00  0.00
0.00  1.00  0.00  1.00
```

**Hint:** Use modulo operator `%` or check if (i + j) is even/odd

<details>
<summary>Answer</summary>

```java
public static void fillArray(Array2d A) {
    int i, j;
    
    for(i = 0; i < A.rows; i++) {
        for(j = 0; j < A.cols; j++) {
            // If (i + j) is even, put 1.0, else put 0.0
            A.arrayData[i][j] = ((i + j) % 2 == 0) ? 1.0 : 0.0;
        }
    }   
}
```

Or simpler:
```java
A.arrayData[i][j] = (i + j) % 2;
```

</details>

---

## SUMMARY: Key Takeaways

✅ **2D arrays** = tables with [row][column]

✅ **Nested loops** = outer for rows, inner for columns

✅ **Formula** `i + j/10.0` = row + (column as decimal)

✅ **Constructor** creates and initializes the array

✅ **Methods** use loops to access all elements

✅ **Conditions** let us filter or check values

**How are you feeling about this material? Ready for more challenges?**

