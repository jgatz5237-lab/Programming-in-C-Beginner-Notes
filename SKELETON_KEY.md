# SKELETON KEY: 2D ARRAY DRIVER PROGRAM
## Complete Solutions & Answers

---

## EXERCISE 1: Modify the Array Dimensions

**Question:** Create an `Array2d` with dimensions 3×5 instead of 5×10. What output do you expect?

**Answer:**
```java
Array2d A = new Array2d(3, 5);  // 3 rows, 5 columns
fillArray(A);
A.printArray();
```

**Expected Output:**
```
0.00  0.10  0.20  0.30  0.40
1.00  1.10  1.20  1.30  1.40
2.00  2.10  2.20  2.30  2.40
```

**Why?**
- Row 0 (i=0): values are 0 + j/10 where j goes 0→4 → 0.0, 0.1, 0.2, 0.3, 0.4
- Row 1 (i=1): values are 1 + j/10 where j goes 0→4 → 1.0, 1.1, 1.2, 1.3, 1.4
- Row 2 (i=2): values are 2 + j/10 where j goes 0→4 → 2.0, 2.1, 2.2, 2.3, 2.4

---

## EXERCISE 2: Change the Formula

### **Option A: Multiplication `i * j`**

**Code:**
```java
A.arrayData[i][j] = i * j;
```

**Expected Output (5×10):**
```
0.00  0.00  0.00  0.00  0.00  0.00  0.00  0.00  0.00  0.00
0.00  1.00  2.00  3.00  4.00  5.00  6.00  7.00  8.00  9.00
0.00  2.00  4.00  6.00  8.00 10.00 12.00 14.00 16.00 18.00
0.00  3.00  6.00  9.00 12.00 15.00 18.00 21.00 24.00 27.00
0.00  4.00  8.00 12.00 16.00 20.00 24.00 28.00 32.00 36.00
```

**Pattern:**
- Row 0: All zeros (0 × anything = 0)
- Row 1: Counts by 1s (1×0=0, 1×1=1, 1×2=2, etc.)
- Row 2: Counts by 2s (2×0=0, 2×1=2, 2×2=4, etc.)
- Creates multiplication table

**Best for:** Learning multiplication, seeing product patterns

---

### **Option B: Average `(i + j) / 2.0`**

**Code:**
```java
A.arrayData[i][j] = (i + j) / 2.0;
```

**Expected Output (5×10):**
```
0.00  0.50  1.00  1.50  2.00  2.50  3.00  3.50  4.00  4.50
0.50  1.00  1.50  2.00  2.50  3.00  3.50  4.00  4.50  5.00
1.00  1.50  2.00  2.50  3.00  3.50  4.00  4.50  5.00  5.50
1.50  2.00  2.50  3.00  3.50  4.00  4.50  5.00  5.50  6.00
2.00  2.50  3.00  3.50  4.00  4.50  5.00  5.50  6.00  6.50
```

**Pattern:**
- Increases by 0.5 going right
- Increases by 0.5 going down
- Creates smooth diagonal gradient
- Symmetric pattern

**Best for:** Understanding averages, smooth gradients, diagonal patterns

---

### **Option C: Power `Math.pow(i, j)` ⚠️ CAREFUL!**

**Code:**
```java
A.arrayData[i][j] = Math.pow(i, j);
```

**Expected Output (5×10):**
```
1.00  0.00  0.00  0.00  0.00  0.00  0.00  0.00  0.00  0.00
1.00  1.00  1.00  1.00  1.00  1.00  1.00  1.00  1.00  1.00
1.00  2.00  4.00  8.00 16.00 32.00 64.00 128.00 256.00 512.00
1.00  3.00  9.00 27.00 81.00 243.00 729.00 2187.00 6561.00 19683.00
1.00  4.00 16.00 64.00 256.00 1024.00 4096.00 16384.00 65536.00 262144.00
```

**Explanation:**
- Row 0: 0^j = undefined, Java handles as 1 or 0
- Row 1: 1^j = always 1
- Row 2: 2^j = exponential (2, 4, 8, 16, 32, 64...)
- Row 3: 3^j = exponential (3, 9, 27, 81, 243...)
- Values grow VERY quickly!

**Best for:** Understanding exponential growth, power functions

---

## EXERCISE 3: Add New Methods

### **Solution A: Find Maximum Value**

**Code to Add to Array2d Class:**
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

**Usage in Main:**
```java
double maxVal = A.findMax();
System.out.println("Maximum value: " + maxVal);
```

**For 5×10 array (formula: i + j/10.0):**
- Maximum = array[4][9] = 4 + 9/10 = **4.9**

**Why This Works:**
1. Start with first element as the max
2. Loop through entire array
3. If find bigger number, update max
4. Return the largest number found

---

### **Solution B: Find Sum of All Elements**

**Code to Add to Array2d Class:**
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

**Usage in Main:**
```java
double total = A.findSum();
System.out.println("Sum of all elements: " + total);
```

**For 3×5 array (formula: i + j/10.0):**
```
Sum = (0.0 + 0.1 + 0.2 + 0.3 + 0.4)
    + (1.0 + 1.1 + 1.2 + 1.3 + 1.4)
    + (2.0 + 2.1 + 2.2 + 2.3 + 2.4)
    = 1.0 + 6.0 + 11.0 = 18.0
```

**Why This Works:**
1. Start sum at 0
2. Loop through entire array
3. Add each element to sum (sum += element)
4. Return total

---

## EXERCISE 4: Filter and Print

**Question:** Modify `printArray()` to only print values ≥ a threshold. Print "---" for others.

**Solution:**
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

**Usage in Main:**
```java
A.printArrayFiltered(3.5);
```

**Output for 5×10 (formula: i + j/10.0, threshold: 3.5):**
```
---    ---    ---    ---    ---    ---    ---    ---    ---    ---
---    ---    ---    ---    ---    ---    ---    ---    ---    ---
---    ---    ---    ---    ---    ---    ---    ---    ---    ---
---    ---    ---    ---    ---    ---    ---    3.60  3.70  3.80
---    ---    ---    ---    ---    ---    3.60  3.70  3.80  3.90
```

**Logic:**
- Check if value >= threshold
- If YES: print the number
- If NO: print "---"
- Use `%-7s` for string formatting to match number width

---

## EXERCISE 5: Trace the Output

**Question:** For a 3×5 array with formula `i + j/10.0`:
- What is array[0][0]?
- What is array[2][4]?
- What pattern do you notice?

**Answers:**

| Position | Calculation | Result |
|----------|-------------|--------|
| array[0][0] | 0 + 0/10 | **0.0** |
| array[0][4] | 0 + 4/10 | **0.4** |
| array[2][4] | 2 + 4/10 | **2.4** |
| array[1][2] | 1 + 2/10 | **1.2** |

**Pattern Observed:**
1. **Each row starts with the row index** → 0.0, 1.0, 2.0
2. **Values increase by 0.1 going left to right** → each column adds 0.1
3. **Rows increase by exactly 1.0** → each row adds 1.0
4. **Creates diagonal stripes** → visually shows i and j components
5. **Predictable and linear** → every position can be calculated: position [i][j] = i.j

---

## ADDITIONAL PRACTICE

### **Challenge 1: Calculate Without Running Code**
For array[3][7] with formula `i + j/10.0`:
- What's the value?
- **Answer: 3 + 7/10 = 3.7**

### **Challenge 2: Reverse Engineer**
If array[i][j] = 2.5, what are possible [i][j]?
- **Answer: i=2, j=5 (since 2 + 5/10 = 2.5)**

### **Challenge 3: Find All Cells with Value 1.5**
In a 5×10 array with formula `i + j/10.0`, find all positions equal to 1.5
- **Answers: [1][5], [2][15] (oops, j can't be 15), [3][25] (oops), etc.**
- **Correct: [1][5] only (1 + 5/10 = 1.5)**

### **Challenge 4: What Formula Creates All 2s?**
```
2.00  2.00  2.00  2.00
2.00  2.00  2.00  2.00
2.00  2.00  2.00  2.00
```
- **Answer: `A.arrayData[i][j] = 2;` or `A.arrayData[i][j] = i + 2 - i;`**

### **Challenge 5: Checkerboard Pattern**
Create alternating 1s and 0s
- **Answer: `A.arrayData[i][j] = (i + j) % 2;`**

---

## QUICK ANSWERS REFERENCE

| Formula | Max Value (5×10) | Pattern |
|---------|-----------------|---------|
| `i + j/10.0` | 4.9 | Diagonal increase |
| `i * j` | 36 | Multiplication table |
| `(i+j)/2.0` | 6.5 | Smooth gradient |
| `Math.pow(i, j)` | 262144 | Exponential explosion |
| `i - j` | 4 | Rows all same value |
| `(i + j) % 2` | 1 | Checkerboard |

---

## SELF-CHECK QUESTIONS

- [ ] Can you trace array[2][3] for formula `i + j/10.0`?
- [ ] Can you write nested loops to iterate through a 2D array?
- [ ] Do you understand why we use `j/10.0` not `j/10`?
- [ ] Can you explain what the constructor does?
- [ ] Can you write a method to find the maximum value?
- [ ] Can you modify `printArray()` to add filtering?
- [ ] Do you understand `%-7.2f` format specifier?

**If you answered YES to all, you've mastered this material! 🎉**

