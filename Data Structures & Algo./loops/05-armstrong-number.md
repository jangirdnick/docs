# Armstrong Number Checker

---

# 📌 1. Question

> You are given an integer as input.
> Your task is to check whether the given number is an Armstrong number or not.
> An Armstrong number is a number that is equal to the sum of its own digits raised to the power of the number of digits.

For example,

```
153 = 1³ + 5³ + 3³ = 153
```

Therefore, 153 is an Armstrong number.

```
9474 = 9⁴ + 4⁴ + 7⁴ + 4⁴ = 9474
```

Therefore, 9474 is also an Armstrong number.

If the number is Armstrong, print:

```
Armstrong
```

Otherwise print:

```
Not Armstrong
```

---

## Example 1

### Input

```
153
```

### Output

```
Armstrong
```

---

## Example 2

### Input

```
370
```

### Output

```
Armstrong
```

---

## Input Format

A single integer `n`.

---

## Output Format

Print:

```
Armstrong
```

if the number satisfies Armstrong condition.

Otherwise print:

```
Not Armstrong
```

---

## Constraints

```
-10^6 ≤ n ≤ 10^6
````

---

# 📖 2. Keyword Bank (English → Hindi)

| English Word | Hindi / Simple Meaning |
|--------------|------------------------|
| Armstrong Number | Aisa number jisme digits ke power ka sum original number ke equal hota hai |
| Digit | Number ka ek-ek ank |
| Power | Kisi number ko baar-baar multiply karna |
| Exponent | Power ki value |
| Raise to Power | Kisi number ki power calculate karna |
| Sum | Total / Addition |
| Original Number | Starting wala actual number |
| Length of Number | Number mein total digits ki count |
| Condition | Check karne wali shart |
| Armstrong Property | Digits ke power ka sum number ke equal hona |

> 💡 **Yaad Rakho:** Armstrong Number ka main idea hai:
>
> ```
> digit^numberOfDigits ka sum = original number
> ```

---

# 🧠 3. Question Ko Apne Shabdon Mein (Paraphrase)

> Ye question mujhse keh raha hai ki mujhe ek number diya gaya hai. Pehle mujhe us number ke total digits count karne hain. Fir har digit ki power (digits count ke according) nikal kar unka sum karna hai. Agar ye sum original number ke equal hai to number Armstrong hai, warna nahi.

### Example

````

153

Total digits = 3

1³ + 5³ + 3³

= 1 + 125 + 27

= 153

Therefore Armstrong

```

---

# 🛠️ 4. Approach / Method

## Technique

**Digit Extraction Pattern**

---

## Soch Hindi Mein

Armstrong number check karne ke liye hume 3 steps follow karne hain:

### Step 1: Digits Count Karna

Pehle pata karenge number mein kitne digits hain.

Example:

```

153

Length = 3

````

---

### Step 2: Har Digit Nikalna

Last digit nikalne ke liye:

```javascript
digit = n % 10
````

Example:

```
153 % 10

= 3
```

Digit remove karne ke liye:

```javascript
n = Math.floor(n / 10)
```

Example:

```
153 / 10

= 15
```

---

### Step 3: Power Sum Calculate Karna

Har digit ki power calculate karenge.

Formula:

```
sum += digit ^ numberOfDigits
```

Finally:

```
sum === originalNumber
```

Agar true hai:

```
Armstrong
```

Otherwise:

```
Not Armstrong
```

---

## Algorithm

```
Store original number

Find total digits count

sum = 0

Repeat while number > 0

    digit = number % 10

    sum += digit ^ digitCount

    number = floor(number / 10)


Compare

sum == original number

Yes -> Armstrong

No -> Not Armstrong
```

---

# 🔍 5. Dry Run

## Example

```
Input:

153
```

---

## Step 1: Store Values

```
originalNumber = 153

digitCount = 3

sum = 0
```

---

## Iteration 1

Number:

```
153
```

Get digit:

```
digit = 153 % 10

digit = 3
```

Power:

```
3³ = 27
```

Add:

```
sum = 27
```

Remove digit:

```
153 / 10

n = 15
```

---

## Iteration 2

Number:

```
15
```

Get digit:

```
digit = 15 % 10

digit = 5
```

Power:

```
5³ = 125
```

Add:

```
sum = 27 + 125

sum = 152
```

Remove digit:

```
n = 1
```

---

## Iteration 3

Number:

```
1
```

Get digit:

```
digit = 1
```

Power:

```
1³ = 1
```

Add:

```
sum = 153
```

---

## Final Check

```
sum === originalNumber

153 === 153
```

Output:

```
Armstrong
```

---

# 💻 6. Actual Code / Answer

```javascript
class Solution {

    checkArmstrong(n) {

        const originalNumber = n;

        const digitCount = String(n).length;

        let sum = 0;

        while (n > 0) {

            const digit = n % 10;

            sum += digit ** digitCount;

            n = Math.floor(n / 10);
        }


        return sum === originalNumber
            ? "Armstrong"
            : "Not Armstrong";

    }

}

module.exports = Solution;
```


```javascript
class Solution {

    checkArmstrong(n) {

        let inputNumber = n
        let inputNumberLength = n.toString().length
        let sum = 0;

        while (n > 0) {
            sum += Math.pow(n % 10, inputNumberLength);
            n = Math.floor(n / 10)
        }

        return sum === inputNumber ? 'Armstrong' : 'Not Armstrong'


    }

}

module.exports = Solution;
```

---

# ⚠️ Edge Cases

## Case 1: Single Digit Number

Input:

```
5
```

Calculation:

```
5¹ = 5
```

Output:

```
Armstrong
```

---

## Case 2: Zero

Input:

```
0
```

Calculation:

```
0¹ = 0
```

Output:

```
Armstrong
```

---

## Case 3: Negative Number

Input:

```
-153
```

Negative numbers generally Armstrong number nahi maane jaate.

Output:

```
Not Armstrong
```

---

## Case 4: Non Armstrong Number

Input:

```
123
```

Calculation:

```
1³ + 2³ + 3³

= 1 + 8 + 27

= 36
```

```
36 != 123
```

Output:

```
Not Armstrong
```

---

# ⚠️ Common Mistakes

## ❌ Original number lose kar dena

Wrong:

```javascript
while(n > 0){
    ...
}

return sum === n;
```

Problem:

Loop ke baad:

```
n = 0
```

ho jayega.

Correct:

```javascript
const originalNumber = n;
```

---

## ❌ Digit count galat nikalna

Wrong:

```
power = 3
```

Hardcode karna.

Kyunki:

```
9474
```

mein power:

```
4
```

hogi.

Correct:

```javascript
String(n).length
```

---

## ❌ Normal sum karna

Wrong:

```
1 + 5 + 3
```

Armstrong mein:

```
1³ + 5³ + 3³
```

karna hota hai.

---

## ❌ Decimal issue

Wrong:

```javascript
n = n / 10
```

Correct:

```javascript
n = Math.floor(n / 10)
```

---

# ⏱️ 7. Complexity

## Time Complexity

```
O(d)
```

Where:

```
d = number of digits
```

Kyunki har digit ko ek baar process karte hain.

Example:

```
1000000
```

mein maximum 7 digits hain.

---

## Space Complexity

```
O(1)
```

Kyunki hum sirf kuch variables use kar rahe hain.

Koi extra array ya recursion nahi use ho raha.

---

# 🎯 Interview Follow-up

Interviewer pooch sakta hai:

### 1. Armstrong Number ko string use kiye bina solve karo.

Answer:

Modulo `% 10` aur division `/ 10` use karke.

---

### 2. 1 se N tak Armstrong Numbers find karo.

Approach:

Har number ke liye Armstrong check function call karo.

---

### 3. Armstrong aur Palindrome Number mein difference?

Palindrome:

```
Number reverse hone ke baad same hota hai.
```

Armstrong:

```
Digits ke power ka sum original number ke equal hota hai.
```

---

### 4. Armstrong check ko optimize kaise karoge?

Repeated digit counting avoid karne ke liye helper functions bana sakte hain.

---

# 🔄 Similar Problems

* Harshad Number
* Neon Number
* Strong Number
* Perfect Number
* Palindrome Number
* Reverse Number
* Sum of Digits
* Automorphic Number

Ye sab problems:

```
Digit Extraction Pattern
```

follow karti hain.

---

# 🧩 Pattern Recognition

Agar question mein aaye:

* Digits ka sum
* Digits ka product
* Digits ki power
* Reverse number
* Count digits
* Last digit find karna

To yaad rakho:

### Digit Extract

```javascript
digit = n % 10
```

### Remove Digit

```javascript
n = Math.floor(n / 10)
```

Ye number-based DSA problems ka basic pattern hai.

---

# 🔑 8. Yaad Rakhne Wali Baat (One-Liner)

> **Armstrong Number mein har digit ko total digits ki power dete hain aur unka sum agar original number ke equal ho jaye to number Armstrong hota hai.**

---

# 📚 Cheat Sheet

```
Digit Count

String(n).length


Extract Digit

digit = n % 10


Remove Digit

n = Math.floor(n / 10)


Armstrong Condition

sum(digit ^ digitCount) == original


Time Complexity

O(number of digits)


Space Complexity

O(1)
```

---

# 🏷️ Topic Tag

`#Math`
`#NumberTheory`
`#DigitExtraction`
`#Modulo`
`#Loop`
`#BasicMath`
