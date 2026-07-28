# Harshad Number Check

---

# 📌 1. Question

> _Write a program to check whether a given number is a Harshad Number or not.
> A Harshad Number (or Niven Number) is a number that is divisible by the sum of its digits.
> For example, 18 is a Harshad number because 1 + 8 = 9, and 18 % 9 == 0._

### Example 1

**Input**

```
18
```

**Output**

```
Harshad Number
```

---

### Example 2

**Input**

```
21
```

**Output**

```
Harshad Number
```

---

### Input Format

A single integer.

### Output Format

Print **Harshad Number** if the number is divisible by the sum of its digits.

Otherwise print **Not Harshad Number**.

### Constraints

```
0 ≤ number ≤ 10^6
```

---

# 📖 2. Keyword Bank (English → Hindi)

| English Word | Hindi / Simple Meaning |
|--------------|------------------------|
| Harshad Number | Aisi sankhya jo apne digits ke sum se completely divide ho jaye |
| Niven Number | Harshad Number ka dusra naam |
| Divisible | Puri tarah divide hona (remainder 0) |
| Digit | Number ka ek-ek ank |
| Sum of Digits | Sabhi digits ka total |
| Remainder | Division ke baad jo bach jaye |
| Modulus (%) | Remainder nikalne wala operator |

> 💡 **Yaad Rakho:** Har Harshad Number ek Niven Number bhi hota hai.

---

# 🧠 3. Question Ko Apne Shabdon Mein (Paraphrase)

> Is question mein hume kisi number ke saare digits ka sum nikalna hai. Fir check karna hai ki original number us sum se completely divide hota hai ya nahi. Agar hota hai to **Harshad Number**, warna **Not Harshad Number** print karna hai.

### Example

```
18

Digits:
1 + 8 = 9

18 % 9 = 0

=> Harshad Number
```

---

# 🛠️ 4. Approach / Method

### Technique

**Digit Extraction (Using Modulo and Division)**

### Soch Hindi Mein

Har digit ko ek-ek karke nikalenge.

Digit nikalne ke liye

```
digit = n % 10
```

Last digit mil jayegi.

Us digit ko sum mein add karenge.

Fir last digit hata denge.

```
n = Math.floor(n / 10)
```

Ye process tab tak chalega jab tak number 0 na ho jaye.

Finally,

```
originalNumber % sum == 0
```

agar true hai to Harshad Number.

---

## Algorithm

```
Store original number

sum = 0

Repeat while number > 0

    digit = number % 10

    sum += digit

    number = floor(number / 10)

Check

original % sum == 0

Yes -> Harshad Number

No -> Not Harshad Number
```

---

# 🔍 5. Dry Run

## Example 1

```
Input

18
```

### Initial

```
num = 18

sum = 0
```

---

### Iteration 1

```
digit = 18 % 10

digit = 8

sum = 8

n = 1
```

---

### Iteration 2

```
digit = 1

sum = 9

n = 0
```

---

### Final Check

```
18 % 9

= 0
```

Output

```
Harshad Number
```

---

## Example 2

```
Input

19
```

Digits

```
1 + 9 = 10
```

Check

```
19 % 10

= 9
```

Output

```
Not Harshad Number
```

---

# 💻 6. Actual Code / Answer

```javascript
class Solution {

    checkHarshad(n) {

        // Edge case
        if (n === 0) {
            return "Not Harshad Number";
        }

        const originalNumber = n;
        let sum = 0;

        while (n > 0) {
            sum += n % 10;
            n = Math.floor(n / 10);
        }

        return originalNumber % sum === 0
            ? "Harshad Number"
            : "Not Harshad Number";
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

```
sum = 1

1 % 1 = 0

Harshad Number
```

---

### Case 2

```
Input

12
```

```
1 + 2 = 3

12 % 3 = 0

Harshad Number
```

---

### Case 3

```
Input

13
```

```
1 + 3 = 4

13 % 4 = 1

Not Harshad Number
```

---

### Case 4

```
Input

100
```

```
1 + 0 + 0 = 1

100 % 1 = 0

Harshad Number
```

---

### Case 5

```
Input

0
```

Digit sum = 0

```
0 % 0
```

Ye mathematically undefined hai.

Isliye generally interview ya coding platforms mein **0 ko Harshad Number nahi maana jata** jab tak explicitly mention na ho.

---

# ⚠️ Common Mistakes

### ❌ Original number overwrite kar dena

Wrong

```javascript
while (n > 0) {
    ...
}

return n % sum;
```

Loop ke baad `n = 0` ho chuka hoga.

Always original number store karo.

```javascript
const original = n;
```

---

### ❌ Floor use na karna

Wrong

```javascript
n = n / 10;
```

Decimal aa jayega.

Correct

```javascript
n = Math.floor(n / 10);
```

---

### ❌ Sum ko reset na karna

Har test case ke liye

```javascript
let sum = 0;
```

se start karo.

---

# ⏱️ 7. Complexity

### Time Complexity

```
O(d)
```

Jahan

```
d = number of digits
```

Agar number

```
10^6
```

tak hai to maximum digits

```
7
```

hi hongi.

Isliye practically ye bahut fast solution hai.

---

### Space Complexity

```
O(1)
```

Koi extra array ya recursion use nahi ho rahi.

---

# 🎯 Interview Follow-up

Interviewer pooch sakta hai:

- Armstrong Number aur Harshad Number mein difference?
- Digit Sum ka reusable function kaise banaoge?
- Harshad Number ko string use kiye bina solve karo.
- 1 se N tak saare Harshad Numbers print karo.
- Recursive solution likho.

---

# 🔄 Similar Problems

- Sum of Digits
- Reverse Number
- Armstrong Number
- Neon Number
- Perfect Number
- Automorphic Number
- Strong Number
- Palindrome Number

Ye sab **Digit Extraction Pattern** follow karte hain.

---

# 🧩 Pattern Recognition

Agar question mein likha ho

- Sum of digits
- Product of digits
- Reverse digits
- Count digits
- Last digit
- First digit

To turant yaad karo:

```
digit = n % 10

n = Math.floor(n / 10)
```

Ye DSA ka **Digit Extraction Pattern** hai.

---

# 🔑 8. Yaad Rakhne Wali Baat (One-Liner)

> **Harshad Number wahi hota hai jo apne digits ke sum se completely divide ho jaye. Is pattern ka core hai: `% 10` se digit nikaalo aur `/ 10` se number chhota karo.**

---

# 📚 Cheat Sheet

```
Digit

digit = n % 10

Remove Digit

n = Math.floor(n / 10)

Condition

original % digitSum == 0

Time

O(number of digits)

Space

O(1)
```

---

# 🏷️ Topic Tag

`#Math`
`#NumberTheory`
`#DigitExtraction`
`#Modulo`
`#BasicMath`
`#Loop`