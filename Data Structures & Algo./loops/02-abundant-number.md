# Abundant Number Checker

---

# 📌 1. Question

> _An Abundant Number is a number for which the sum of its proper divisors (divisors excluding the number itself) is greater than the number. Your task is to write a program to determine if a given number is an Abundant Number. Return "Yes" or "No"._

### Example 1

**Input**

```text
12
```

**Output**

```text
Yes
```

---

### Example 2

**Input**

```text
10
```

**Output**

```text
No
```

---

### Input Format

A single positive integer.

### Output Format

Print **"Yes"** if the given number is an **Abundant Number**.

Otherwise print **"No"**.

### Constraints

```text
1 ≤ number ≤ 10^6
```

---

# 📖 2. Keyword Bank (English → Hindi)

| English Word    | Hindi / Simple Meaning                                        |
| --------------- | ------------------------------------------------------------- |
| Abundant Number | Aisa number jiske proper divisors ka sum us number se bada ho |
| Proper Divisor  | Number ko chhodkar baaki divisor                              |
| Divisor         | Jo number ko bina remainder ke divide kare                    |
| Factor          | Divisor ka hi dusra naam                                      |
| Greater Than    | Bada hona ( > )                                               |
| Sum of Divisors | Sabhi proper divisors ka total                                |

> 💡 **Yaad Rakho:** Proper Divisor mein **number khud include nahi hota**.

---

# 🧠 3. Question Ko Apne Shabdon Mein (Paraphrase)

> Is question mein hume kisi number ke **proper divisors** ka sum nikalna hai. Agar un sab divisors ka total original number se **zyada** ho to `"Yes"` return karna hai, warna `"No"`.

### Example

```
12

Proper Divisors

1
2
3
4
6

Sum

1 + 2 + 3 + 4 + 6 = 16

16 > 12

=> Yes
```

---

# 🛠️ 4. Approach / Method

### Technique

**Factor / Divisor Traversal (Brute Force)**

### Soch Hindi Mein

Hum 1 se lekar `n - 1` tak loop chalayenge.

Har number ke liye check karenge

```
n % i == 0
```

Agar remainder zero hai,

to matlab `i` ek proper divisor hai.

Us divisor ko sum mein add kar denge.

Loop khatam hone ke baad

```
sum > n
```

agar true hai to

```
Yes
```

warna

```
No
```

---

## Algorithm

```
sum = 0

Loop from 1 to n-1

    Agar i divisor hai

        sum += i

Loop khatam

Check

sum > n

Yes -> Abundant Number

No -> Not Abundant Number
```

---

# 🔍 5. Dry Run

## Example 1

```
Input

12
```

### Initial

```
sum = 0
```

---

### Iteration 1

```
i = 1

12 % 1 = 0

sum = 1
```

---

### Iteration 2

```
i = 2

12 % 2 = 0

sum = 3
```

---

### Iteration 3

```
i = 3

12 % 3 = 0

sum = 6
```

---

### Iteration 4

```
i = 4

12 % 4 = 0

sum = 10
```

---

### Iteration 5

```
i = 5

Not Divisor

sum = 10
```

---

### Iteration 6

```
i = 6

12 % 6 = 0

sum = 16
```

Remaining numbers divisor nahi hain.

---

### Final Check

```
16 > 12

True
```

Output

```
Yes
```

---

## Example 2

```
Input

10
```

Proper Divisors

```
1
2
5
```

Sum

```
1 + 2 + 5 = 8
```

Check

```
8 > 10

False
```

Output

```
No
```

---

# 💻 6. Actual Code / Answer

```javascript
class Solution {
  checkAbundant(n) {
    let sum = 0;

    for (let i = 1; i < n; i++) {
      if (n % i === 0) {
        sum += i;
      }
    }

    return sum > n ? "Yes" : "No";
  }
}

module.exports = Solution;
```

```javascript
class Solution {
  checkAbundant(n) {
    const copyVal = n;
    let sum = 0,
      index = 1;
    while (index < copyVal) {
      if (copyVal % index === 0) {
        sum += index;
      }
      n--;
      index++;
    }

    return sum > copyVal ? "Yes" : "No";
  }
}

module.exports = Solution;
```

---

# ⚠️ Edge Cases

### Case 1

```
Input

1
```

Proper divisors

```
None
```

Sum

```
0
```

Check

```
0 > 1

False
```

Output

```
No
```

---

### Case 2

```
Input

6
```

Proper divisors

```
1
2
3
```

Sum

```
6
```

Check

```
6 > 6

False
```

Output

```
No
```

> 6 ek **Perfect Number** hai, Abundant Number nahi.

---

### Case 3

```
Input

18
```

Proper divisors

```
1
2
3
6
9
```

Sum

```
21
```

Check

```
21 > 18

True
```

Output

```
Yes
```

---

### Case 4

```
Input

13
```

Proper divisors

```
1
```

Sum

```
1
```

Check

```
1 > 13

False
```

Output

```
No
```

---

### Case 5

```
Input

20
```

Proper divisors

```
1
2
4
5
10
```

Sum

```
22
```

Check

```
22 > 20

True
```

Output

```
Yes
```

---

# ⚠️ Common Mistakes

### ❌ Number ko bhi divisor maan lena

Wrong

```
1 + 2 + 3 + 4 + 6 + 12
```

Correct

```
1 + 2 + 3 + 4 + 6
```

---

### ❌ Loop n tak chalana

Wrong

```javascript
for(let i = 1; i <= n; i++)
```

Correct

```javascript
for(let i = 1; i < n; i++)
```

---

### ❌ Comparison galat kar dena

Wrong

```javascript
sum >= n;
```

Correct

```javascript
sum > n;
```

Question clearly bol raha hai

```
Greater Than
```

---

# ⏱️ 7. Complexity

### Time Complexity

```
O(n)
```

Kyuki hum

```
1 → n-1
```

tak har number ko divisor ke liye check kar rahe hain.

---

### Space Complexity

```
O(1)
```

Sirf ek variable `sum` use ho raha hai.

---

# 🎯 Interview Follow-up

Interviewer pooch sakta hai:

- Proper divisor kya hota hai?
- Perfect Number aur Abundant Number mein difference?
- Is solution ko O(√n) mein optimize kaise karoge?
- 1 se N tak saare Abundant Numbers print karo.
- Deficient Number kya hota hai?

---

# 🔄 Similar Problems

- Perfect Number
- Prime Number
- Composite Number
- Deficient Number
- Count Factors
- Sum of Factors
- GCD
- LCM

Ye sab **Factor / Divisor Pattern** follow karte hain.

---

# 🧩 Pattern Recognition

Agar question mein likha ho

- Divisors
- Factors
- Proper Divisors
- Count Factors
- Sum of Factors
- Perfect Number
- Abundant Number
- Deficient Number

To turant yaad karo

```javascript
for (let i = 1; i < n; i++) {
  if (n % i === 0) {
    // Factor mil gaya
  }
}
```

Agar optimization maange,

to yaad karo

```
Loop till √n
```

Kyuki factors pair mein aate hain.

Example

```
36

1 × 36
2 × 18
3 × 12
4 × 9
6 × 6
```

Ye **Factor Traversal Pattern** hai.

---

# 🔑 8. Yaad Rakhne Wali Baat (One-Liner)

> **Abundant Number wahi hota hai jiske proper divisors ka sum original number se bada ho. Is pattern ka core hai: factors find karo, unka sum nikalo aur `sum > number` check karo.**

---

# 📚 Cheat Sheet

```
Factor Check

n % i == 0

Loop

1 → n-1

Condition

sum > n

Time

O(n)

Optimized

O(√n)

Space

O(1)
```

---

# 🏷️ Topic Tag

`#Math`
`#NumberTheory`
`#Factors`
`#Divisors`
`#Modulo`
`#BasicMath`
`#Loop`
