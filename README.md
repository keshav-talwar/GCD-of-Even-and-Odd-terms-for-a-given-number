# GCD of the Sums of the First n Odd and Even Numbers

Semester 1 (Aug 2025) practice problem in Python, plus a C exercise.

## Problem

Given a positive integer `n`:

- `sumOdd = 1 + 3 + 5 + … + (2n − 1)`, the first n odd numbers
- `sumEven = 2 + 4 + 6 + … + 2n`, the first n even numbers

Return `gcd(sumOdd, sumEven)`.

## Solution (`test.py`)

`Solution.gcdOfOddEvenSums(n)` sums both series with loops, then tries every divisor from 1 to
`max(sumOdd, sumEven)` and keeps the largest one that divides both. It prints the two sums and
the GCD.

```bash
python3 test.py
# Enter a number: 4
# This is even-  20
# This is Odd 16
# 4
```

**The math shortcut:** `sumOdd = n²` and `sumEven = n(n + 1)`. Since `gcd(n, n + 1) = 1`,
`gcd(n², n(n+1)) = n`, so the answer is always `n`. The loop version is O(n²) work; the closed
form is O(1).

## `1.c`: maximum subarray sum (brute force)

A separate C exercise: checks every subarray of `{3, -4, 5, -6, 7}` with three nested loops
(O(n³)) and prints the largest sum.

```bash
cc 1.c -o maxsub && ./maxsub
```

**Known bug:** `max_sum` starts at `INT_MAX`, so `max_sum < sum` is never true and it prints
`INT_MAX`. It should start at `INT_MIN`; then it prints `7`. Kadane's algorithm does it in O(n).
