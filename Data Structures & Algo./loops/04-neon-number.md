# Check if a Number is a Neon Number

---

# 📌 1. Question

> _Write a program that checks if a given number is a Neon number.  
> A Neon number is a number where the sum of the digits of the square of the number is equal to the number itself._

---

## Example 1

### Input

```text
9
````

### Process

Square of number:

```text
9² = 81
```

Sum of digits:

```text
8 + 1 = 9
```

Comparison:

```text
9 == 9
```

### Output

```text
Yes
```

---

## Example 2

### Input

```text
10
```

### Process

Square:

```text
10² = 100
```

Digit Sum:

```text
1 + 0 + 0 = 1
```

Comparison:

```text
1 != 10
```

### Output

```text
No
```

---

## Input Format

A single integer `N`.

---

## Output Format

Print:

```
Yes
```

if the number is a Neon Number.

Otherwise print:

```
No
```

---

## Constraints

```
0 ≤ n ≤ 10^6
```

---

# 📖 2. Keyword Bank (English → Hindi)

| English Word    | Hindi / Simple Meaning                                        |
| --------------- | ------------------------------------------------------------- |
| Neon Number     | Jis number ke square ke digits ka sum wahi original number ho |
| Square          | Kisi number ko usi se multiply karna (n × n)                  |
| Digit Sum       | Number ke sabhi digits ka total                               |
| Extract Digit   | Number se ek-ek digit nikalna                                 |
| Compare         | Do values ko check karna equal hai ya nahi                    |
| Original Number | Starting wala given number                                    |

> 💡 **Yaad Rakho:**
> Neon Number check karne ke liye pehle number ka square nikalte hain, fir uske digits ka sum karte hain.

Example:

```
9

Square:

9 × 9 = 81

Digit Sum:

8 + 1 = 9
```

---

# 🧠 3. Question Ko Apne Shabdon Mein (Paraphrase)

> Is question mein hume ek number diya hai. Pehle us number ka square nikalna hai. Fir square ke digits ka sum nikalna hai. Agar digit sum original number ke equal hai to wo **Neon Number** hai.

Example:

```
Input:

9

Square:

81

Digits:

8 + 1 = 9

Answer:

Yes
```

---

# 🛠️ 4. Approach / Method

## Technique

**Digit Extraction Using Modulo and Division**

---

## Soch Hindi Mein

Sabse pehle number ka square calculate karenge.

```
square = n * n
```

Ab square ke digits ko ek-ek karke nikalenge.

Last digit nikalne ke liye:

```javascript
digit = square % 10
```

Digit sum mein add karenge.

Fir last digit remove karenge:

```javascript
square = Math.floor(square / 10)
```

Ye process tab tak chalega jab tak square `0` nahi ho jata.

Finally:

```
digitSum == originalNumber
```

check karenge.

Agar equal hai:

```
Yes
```

warna:

```
No
```

---

# Algorithm

```
Store original number

Find square

sum = 0

While square > 0

    digit = square % 10

    sum += digit

    square = square / 10

Check

sum == original number

Yes -> Neon Number

No -> Not Neon Number
```

---

# 🔍 5. Dry Run

## Example

```
Input:

9
```

---

## Step 1

Square calculate karo:

```
square = 9 × 9

square = 81
```

---

## Step 2

Initial:

```
sum = 0
```

---

## Iteration 1

Extract digit:

```
digit = 81 % 10

digit = 1
```

Add:

```
sum = 0 + 1

sum = 1
```

Remove digit:

```
81 / 10

= 8
```

---

## Iteration 2

Extract digit:

```
digit = 8 % 10

digit = 8
```

Add:

```
sum = 1 + 8

sum = 9
```

Remove digit:

```
8 / 10

= 0
```

Loop ends.

---

## Final Check

```
sum == n

9 == 9
```

True

Output:

```
Yes
```

---

# 💻 6. Actual Code / Answer

```javascript
class Solution {

    checkNeon(n) {

        const originalNumber = n;

        let square = n * n;
        let sum = 0;

        while (square > 0) {

            sum += square % 10;

            square = Math.floor(square / 10);

        }

        return sum === originalNumber ? "Yes" : "No";

    }

}

module.exports = Solution;
```

---

# 🧩 Code Breakdown

## Step 1: Store Original Number

```javascript
const originalNumber = n;
```

Square nikalne ke baad bhi hume original number ki zarurat padegi.

---

## Step 2: Calculate Square

```javascript
let square = n * n;
```

Neon number ka first step square calculate karna hai.

---

## Step 3: Extract Digits

```javascript
square % 10
```

Last digit return karta hai.

Example:

```
81 % 10

= 1
```

---

## Step 4: Remove Last Digit

```javascript
Math.floor(square / 10)
```

Example:

```
81 / 10

= 8.1

Math.floor

= 8
```

---

## Step 5: Compare Result

```javascript
sum === originalNumber
```

Agar square ke digits ka sum original number ke equal hai to Neon Number hai.

---

# ⚠️ Edge Cases

## Case 1

```
Input:

0
```

Square:

```
0² = 0
```

Digit Sum:

```
0
```

Check:

```
0 == 0
```

Output:

```
Yes
```

---

## Case 2

```
Input:

1
```

Square:

```
1² = 1
```

Digit Sum:

```
1
```

Output:

```
Yes
```

---

## Case 3

```
Input:

10
```

Square:

```
100
```

Digit Sum:

```
1+0+0 = 1
```

Check:

```
1 != 10
```

Output:

```
No
```

---

## Case 4

```
Input:

9
```

Square:

```
81
```

Digit Sum:

```
8+1=9
```

Output:

```
Yes
```

---

# ⚠️ Common Mistakes

## ❌ Original number lose kar dena

Wrong:

```javascript
let n = n * n;
```

Agar original number overwrite kar diya to final comparison nahi kar paoge.

Correct:

```javascript
const originalNumber = n;
```

---

## ❌ Square ke digits nahi nikalna

Wrong:

```
square == n
```

Neon Number mein square equal nahi check karna hota.

Check hota hai:

```
sum of square digits == original number
```

---

## ❌ Division mein decimal handle na karna

Wrong:

```javascript
square = square / 10;
```

Correct:

```javascript
square = Math.floor(square / 10);
```

---

# ⏱️ 7. Complexity

## Time Complexity

```
O(d)
```

Where:

```
d = digits in n²
```

Kyuki hum square ke har digit ko ek baar process karte hain.

---

## Space Complexity

```
O(1)
```

Sirf variables use ho rahe hain.

Koi extra array ya recursion nahi hai.

---

# 🎯 Interview Follow-up

Interviewer pooch sakta hai:

* Neon Number kya hota hai?
* Digit extraction kaise karte ho?
* String ke bina digits ka sum kaise nikaloge?
* 1 se N tak saare Neon Numbers kaise find karoge?
* Armstrong Number aur Neon Number mein difference kya hai?

---

# 🔄 Similar Problems

* Harshad Number
* Armstrong Number
* Strong Number
* Automorphic Number
* Palindrome Number
* Sum of Digits
* Reverse Number

Ye sab **Digit Extraction Pattern** follow karte hain.

---

# 🧩 Pattern Recognition

Agar question mein likha ho:

* Digits ka sum
* Digits count karna
* Reverse number
* Last digit find karna
* Number ke digits par operation

To turant yaad karo:

```javascript
digit = n % 10

n = Math.floor(n / 10)
```

Example:

```
1234
```

Extraction:

```
1234 % 10 = 4

123 / 10 = 123
```

Ye **Digit Extraction Pattern** hai.

---

# 🔑 8. Yaad Rakhne Wali Baat (One-Liner)

> **Neon Number mein number ka square nikalte hain aur us square ke digits ka sum agar original number ke equal ho to Neon Number hota hai.**

---

# 📚 Cheat Sheet

```
Step 1:

square = n * n


Step 2:

digit = square % 10


Step 3:

square = Math.floor(square / 10)


Step 4:

sum == originalNumber


Complexity:

Time: O(number of digits)

Space: O(1)
```

---

# 🏷️ Topic Tag

`#Math`
`#NumberTheory`
`#DigitExtraction`
`#Modulo`
`#BasicMath`
`#Loop`
`#NumberPattern`
