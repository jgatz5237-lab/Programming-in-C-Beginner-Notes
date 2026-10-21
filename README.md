# Beginner Notes: Basic C

A concise study guide to C fundamentals for small projects, programming exercises, and algorithm practice. Examples use standard C and can be compiled with a C compiler such as GCC.

## Getting started

Save a program in a file ending in `.c`, then compile and run it:

```sh
gcc -std=c11 -Wall -Wextra -Wpedantic -o hello hello.c
./hello
```

Compiler warnings are useful: fix them rather than ignoring them. A minimal C program has a `main` function, which returns a status code to the operating system:

```c
#include <stdio.h>

int main(void)
{
    puts("Hello, world!");
    return 0;
}
```

## Variables and types

Declare a variable with a type before using it. Initialize values when possible.

| Type | Common use | Example |
| --- | --- | --- |
| `int` | Whole numbers | `int count = 3;` |
| `long` | Larger-range whole numbers | `long population = 8000000L;` |
| `float` | Approximate decimal values | `float ratio = 0.5f;` |
| `double` | More precise approximate decimal values | `double distance = 12.75;` |
| `char` | A single character | `char grade = 'A';` |
| `_Bool` | Boolean value (`0` or `1`) | `_Bool ready = 1;` |

Use `const` for a value that should not be reassigned. Use `size_t` (from `<stddef.h>`) for sizes and array indexes when appropriate. Integer division truncates: `7 / 2` is `3`; use `7.0 / 2` for a floating-point result. The exact ranges of integer types can vary by system.

## Input and output

`printf` writes formatted output; `scanf` can read simple input. The format specifier must match the pointed-to variable's type. Check whether input succeeded before using it.

```c
#include <stdio.h>

int main(void)
{
    int age;
    printf("Age: ");
    if (scanf("%d", &age) != 1) {
        fputs("Please enter a whole number.\n", stderr);
        return 1;
    }
    printf("Next year: %d\n", age + 1);
    return 0;
}
```

Common `printf` formats include `%d` for `int`, `%ld` for `long`, `%f` for `double`, and `%c` for `char`. In `scanf`, use `%f` for `float` and `%lf` for `double`; pass a variable's address with `&`. For whole lines or input that may contain spaces, use `fgets` and handle its return value rather than using `gets` (which is unsafe and removed from modern C).

## Decisions and loops

Conditions use comparisons such as `==`, `!=`, `<`, `<=`, `>`, and `>=`. Use `&&` for AND, `||` for OR, and `!` for NOT. In C, zero is false and nonzero is true. Remember that `=` assigns a value while `==` compares values.

```c
if (score >= 60) {
    puts("Pass");
} else {
    puts("Try again");
}
```

Use `for` when the iteration count or range is clear, `while` when continuing depends on a condition, and `do ... while` when the body must run at least once.

```c
for (int i = 0; i < 5; ++i) {
    printf("%d\n", i);
}
```

Check loop boundaries carefully. For an array of length `n`, valid indexes are `0` through `n - 1`; accessing beyond those bounds causes undefined behavior.

## Functions

Functions break a program into named, reusable operations. A declaration (prototype) tells the compiler a function's name, result type, and parameter types.

```c
#include <stdio.h>

int maximum(int a, int b);

int main(void)
{
    printf("%d\n", maximum(4, 9));
    return 0;
}

int maximum(int a, int b)
{
    return a > b ? a : b;
}
```

C passes arguments by value: a function receives a copy. To let a function modify a caller's variable, pass its address using a pointer.

## Arrays, strings, and pointers

An array stores a fixed number of values of one type. Its length is not automatically passed to a function, so provide the length separately.

```c
int sum(const int values[], size_t length)
{
    int total = 0;
    for (size_t i = 0; i < length; ++i) {
        total += values[i];
    }
    return total;
}
```

Include `<stddef.h>` when using `size_t`. A C string is a character array terminated by `'\0'`; reserve space for that terminator. Use functions from `<string.h>` such as `strlen` and `strcmp`, and ensure destination buffers are large enough.

A pointer stores an address. `&value` gets a variable's address, and `*pointer` accesses the value at that address. Initialize pointers before use and do not dereference a null, uninitialized, or expired pointer.

## Structures and dynamic memory

Use a `struct` to group related fields:

```c
struct Point {
    int x;
    int y;
};

struct Point origin = { .x = 0, .y = 0 };
printf("(%d, %d)\n", origin.x, origin.y);
```

For data whose size is decided at runtime, `<stdlib.h>` provides `malloc` and `free`. Check allocation results and release each successfully allocated block exactly once. For example:

```c
int *values = malloc(count * sizeof *values);
if (values == NULL) {
    /* Handle allocation failure. */
}
/* Use values only after successful allocation. */
free(values);
```

Include `<stdlib.h>` for these functions. Before allocating, ensure the requested element count is valid and that `count * sizeof *values` cannot overflow. Prefer fixed-size arrays or automatic storage when they meet the need.

## Problem solving and algorithms

For a programming problem:

1. Restate the inputs, required output, and constraints.
2. Work through a small example by hand; include empty, minimum, maximum, and unusual cases where relevant.
3. Choose a clear algorithm and data representation before writing code.
4. Split the solution into functions with focused responsibilities.
5. Test normal cases and edge cases, and compile with warnings enabled.

An algorithm's time complexity describes how its work grows with input size; space complexity describes extra memory use. Big-O gives an upper-bound growth rate: scanning `n` items is typically `O(n)`, while comparing every pair is typically `O(n²)`. For example, a linear search checks each element until it finds the target:

```c
int find(const int values[], size_t length, int target)
{
    for (size_t i = 0; i < length; ++i) {
        if (values[i] == target) {
            return (int)i;
        }
    }
    return -1;
}
```

This search is `O(n)` time and uses `O(1)` extra space. Ensure the returned index fits in `int` if using `-1` as the not-found result; for very large arrays, use a suitable result type or a separate success indicator.

## Common pitfalls

- Using an uninitialized variable or reading an array out of bounds.
- Confusing assignment (`=`) with equality (`==`).
- Mismatching a formatted I/O specifier and its argument type.
- Forgetting that C strings need a terminating null character.
- Using a pointer after its target's lifetime ends, or freeing memory twice.
- Assuming signed integer overflow wraps around; in C it has undefined behavior.
- Ignoring input and allocation failures.

Practice by changing the examples, then try small tasks such as finding a minimum, counting values that match a condition, reversing an array, or implementing a simple sort.
