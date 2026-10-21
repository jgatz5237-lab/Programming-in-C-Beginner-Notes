# 2D ARRAY DRIVER PROGRAM - STUDY SHEET

---

## CORE CONCEPTS TO MEMORIZE

### 1. **What is a 2D Array?**
- An **array of arrays** — like a table with rows and columns
- Declared as: `double[][] arrayData;`
- Accessed as: `arrayData[row][column]`
- Example: `arrayData[2][3]` = element at row 2, column 3

### 2. **Array2d Class Structure**
```
Array2d Class
├── Variables:
│   ├── double[][] arrayData    (the actual data)
│   ├── int rows                (number of rows)
│   └── int cols                (number of columns)
├── Constructor:
│   └── Array2d(int rows, int cols)
└── Methods:
    ├── printArray()
    └── (you add more methods here)
```

### 3. **Constructor: What It Does**
```
NEW ARRAY2D(5, 10)
    ↓
Creates a 2D array with 5 rows and 10 columns
    ↓
Total elements = 5 × 10 = 50 doubles
```

### 4. **Nested Loops: The Pattern**
```
for(i = 0; i < rows; i++)          ← outer loop: GO THROUGH EACH ROW
{
    for(j = 0; j < cols; j++)      ← inner loop: GO THROUGH EACH COLUMN IN THAT ROW
    {
        // Do something with arrayData[i][j]
    }
}
```

### 5. **The Key Formula: `i + j/10.0`**
- `i` = row number (0, 1, 2, 3, 4, ...)
- `j` = column number (0, 1, 2, 3, 4, ...)
- `j/10.0` = converts column to decimal (0.0, 0.1, 0.2, 0.3, ...)
- Result: arrayData[2][3] = 2 + 3/10 = **2.3**

### 6. **Print Formatting: `printf("%-7.2f", value)`**
```
%-7.2f
├─ % = start format command
├─ - = left-align
├─ 7 = field width (7 characters wide)
├─ .2 = 2 decimal places
└─ f = floating-point number

Example: 2.30 displays as "2.30  " (padded to 7 chars)
```

---

## MEMORIZATION CHECKLIST

- [ ] Understand 2D array = array of arrays
- [ ] Know how to access element: `array[row][col]`
- [ ] Understand nested loops (outer = rows, inner = cols)
- [ ] Know the formula creates pattern: row + col/10
- [ ] Understand printf formatting for output
- [ ] Can trace code mentally for small arrays (3×5)
- [ ] Understand constructor initializes dimensions and creates array

---

## QUICK REFERENCE TABLE

| Term | Definition | Example |
|------|-----------|---------|
| **2D Array** | Table of data with rows & columns | `double[][] data` |
| **Rows** | Horizontal lines (top to bottom) | Index `i` from 0 to rows-1 |
| **Columns** | Vertical lines (left to right) | Index `j` from 0 to cols-1 |
| **Index** | Position in array | [2][3] means row 2, col 3 |
| **Nested Loop** | Loop inside a loop | Outer loop rows, inner loop cols |
| **Constructor** | Initializes the object | `new Array2d(5, 10)` |
| **Casting** | Converting types | `j/10.0` (int to double) |

---

## VISUAL EXAMPLE: 3×5 Array

```
Array2d A = new Array2d(3, 5);
fillArray(A);
A.printArray();

OUTPUT:
┌─────────────────────────────────────┐
│  0.00  0.10  0.20  0.30  0.40     │  Row 0 (i=0)
│  1.00  1.10  1.20  1.30  1.40     │  Row 1 (i=1)
│  2.00  2.10  2.20  2.30  2.40     │  Row 2 (i=2)
└─────────────────────────────────────┘
   ↑     ↑     ↑     ↑     ↑
   j=0   j=1   j=2   j=3   j=4
   (columns)

Pattern:
- Each row starts with row number (0.00, 1.00, 2.00)
- Increases by 0.1 going left to right
```

---

## STEP-BY-STEP EXECUTION

### Step 1: Create Array
```java
Array2d A = new Array2d(5, 10);
```
→ Creates empty 5×10 array

### Step 2: Fill Array
```java
fillArray(A);
```
→ Nested loops fill each position [i][j] with i + j/10.0

### Step 3: Print Array
```java
A.printArray();
```
→ Nested loops print each position with formatting

---

## COMMON MISTAKES TO AVOID

1. ❌ **Confusing rows and columns**
   - ✅ Rows are horizontal (index `i`)
   - ✅ Columns are vertical (index `j`)

2. ❌ **Forgetting `.0` in division**
   - ❌ `j/10` = integer division = 0 or 1
   - ✅ `j/10.0` = decimal division = 0.1, 0.2, etc.

3. ❌ **Getting loop bounds wrong**
   - ✅ `i < rows` (not `i <= rows`)
   - ✅ `j < cols` (not `j <= cols`)

4. ❌ **Accessing out of bounds**
   - ❌ If rows=5, don't try array[5][0] (only 0-4 valid)

5. ❌ **Forgetting `this.` in class methods**
   - ✅ Use `this.arrayData`, `this.rows`, `this.cols` to refer to member variables

---

## KEY EQUATIONS TO MEMORIZE

```
Total Elements = rows × columns

For 5×10 array: 5 × 10 = 50 elements

Value at [i][j] = i + j/10.0

For [2][3]: 2 + 3/10 = 2 + 0.3 = 2.3
```

---

## SUMMARY IN ONE SENTENCE

**A 2D array is a table of data accessed by [row][column], filled using nested loops, and formatted for display.**

