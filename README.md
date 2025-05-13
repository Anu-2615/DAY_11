# DAY_11  Factorial Trailing Zeroes



# Trailing Zeroes in Factorial – Java Solution

This project contains a concise and efficient Java implementation to calculate the number of trailing zeroes in the factorial of a given number `n`.

## 📘 Problem Statement

Given an integer `n`, return the number of trailing zeroes in `n!` (n factorial).

### Example:

Input: 5
Output: 1
Explanation: 5! = 120 → has 1 trailing zero

---

## 🧠 Approach

Trailing zeroes in a factorial are caused by the multiplication of 10s, and each 10 is formed by a pair of 2 and 5. Since factorials have more 2s than 5s, we only need to count the number of 5s in the prime factorization of `n!`.

This is achieved by:
- Dividing `n` by 5, 25, 125, and so on.
- Summing up the results to get the total number of trailing zeroes.

---

## 💡 Algorithm

1. Initialize a result counter `l` to 0.
2. Start with `m = 5` and continue dividing `n` by `m`.
3. Add the result of `n / m` to `l`.
4. Multiply `m` by 5 and repeat until `n / m` becomes zero.
5. Return `l`.

---

## 🧾 Java Code

```java
class Solution {
    public int trailingZeroes(int n) {
        int l = 0;
        long m = 5;

        while (n / m > 0) {
            l += n / m;
            m *= 5;
        }

        return l;
    }
}
🧪 Test Cases
Input	Output	Explanation
5	1	5! = 120
10	2	10! = 3628800
25	6	Extra factors from 25
100	24	Includes 25, 125 etc.

🚀 Complexity Analysis
Time Complexity: O(log₅(n)) – because we divide n by increasing powers of 5.

Space Complexity: O(1) – constant space used.
