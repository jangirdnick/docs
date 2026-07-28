# Finding Prime Factors of a Number

---

# 📌 1. Question

> _Write a program to find and print all the prime factors of a given number.  
> A prime factor is a factor that is a prime number._
>
> _If the number is 0 or 1, print No prime factors._

---

## Example 1

### Input

```text
60
````

### Output

```text
2 2 3 5
```

### Explanation

```
60 = 2 × 2 × 3 × 5
```

All factors are prime numbers.

---

## Example 2

### Input

```text
45
```

### Output

```text
3 3 5
```

### Explanation

```
45 = 3 × 3 × 5
```

---

## Input Format

The input consists of a single integer `N`.

---

## Output Format

Print all prime factors of the number.

If:

```
N = 0 or N = 1
```

print:

```
No prime factors
```

---

## Constraints

```
1 ≤ N ≤ 10^6
```

Special Cases:

```
N = 0 or N = 1

Output:
No prime factors
```

---

# 📖 2. Keyword Bank (English → Hindi)

| English Word     | Hindi / Simple Meaning                                   |
| ---------------- | -------------------------------------------------------- |
| Prime Factor     | Aisa factor jo khud prime number ho                      |
| Factor           | Jo number ko completely divide kare                      |
| Prime Number     | Jiske sirf 2 factors hote hain (1 aur khud number)       |
| Factorization    | Kisi number ko factors ke multiplication form mein todna |
| Divisible        | Jiska remainder 0 aaye                                   |
| Repeated Factor  | Same factor ka multiple times aana                       |
| Composite Number | Jiske 2 se zyada factors hote hain                       |

> 💡 **Yaad Rakho:**
> Prime factorization ka matlab hai kisi number ko sirf prime numbers ke multiplication mein todna.

Example:

```
60

= 2 × 2 × 3 × 5
```

---

# 🧠 3. Question Ko Apne Shabdon Mein (Paraphrase)

> Is question mein hume ek number diya gaya hai. Hume us number ko chhote-chhote prime numbers se divide karna hai aur jitne bhi prime factors milte hain unhe print karna hai.

Example:

```
60
```

Pehle 2 se divide:

```
60 / 2 = 30
```

Fir:

```
30 / 2 = 15
```

Fir:

```
15 / 3 = 5
```

Fir:

```
5 / 5 = 1
```

Prime Factors:

```
2 2 3 5
```

---

# 🛠️ 4. Approach / Method

## Technique

**Prime Factorization using Trial Division**

---

## Soch Hindi Mein

Hum check karenge ki kaunsa number given number ko divide kar raha hai.

Start karenge:

```
divisor = 2
```

Kyuki 2 sabse chhota prime number hai.

Agar:

```javascript
n % divisor === 0
```

hai to iska matlab:

```
divisor ek prime factor hai
```

Usko result mein store karenge.

Fir number ko divide kar denge:

```
n = n / divisor
```

Same divisor dobara check karenge kyuki same factor multiple times aa sakta hai.

Example:

```
60

2 se divide

60 / 2 = 30

Dobara 2 se divide

30 / 2 = 15
```

Jab divisor divide nahi karega to next divisor check karenge.

Process tab tak chalega jab tak:

```
n = 1
```

na ho jaye.

---

# Algorithm

```
Start

If n == 0 or n == 1

    Print "No prime factors"

Else

    divisor = 2

    While n > 1

        If n % divisor == 0

            Store divisor

            n = n / divisor

        Else

            divisor++

    Print all factors

End
```

---

# 🔍 5. Dry Run

## Example

```
Input:

60
```

Initial:

```
n = 60

divisor = 2

result = []
```

---

## Step 1

Check:

```
60 % 2 == 0
```

Yes

Add:

```
result = [2]
```

Update:

```
n = 60 / 2

n = 30
```

---

## Step 2

Check:

```
30 % 2 == 0
```

Yes

Add:

```
result = [2,2]
```

Update:

```
n = 15
```

---

## Step 3

Check:

```
15 % 2 != 0
```

Increase divisor:

```
divisor = 3
```

---

## Step 4

Check:

```
15 % 3 == 0
```

Yes

Add:

```
result = [2,2,3]
```

Update:

```
n = 5
```

---

## Step 5

Check:

```
5 % 3 != 0
```

Increase:

```
divisor = 4
```

---

## Step 6

Check:

```
5 % 4 != 0
```

Increase:

```
divisor = 5
```

---

## Step 7

Check:

```
5 % 5 == 0
```

Add:

```
result = [2,2,3,5]
```

Update:

```
n = 1
```

Loop ends.

---

## Output

```
2 2 3 5
```

---

# 💻 6. Actual Code / Answer

```javascript
class Solution {

    primeFactors(n) {

        if (n === 0 || n === 1) {
            return "No prime factors";
        }

        const result = [];

        let divisor = 2;

        while (n > 1) {

            if (n % divisor === 0) {

                result.push(divisor);

                n = n / divisor;

            } else {

                divisor++;

            }

        }

        return result.join(" ");

    }

}

module.exports = Solution;
```

---

# 🧩 Code Breakdown

## Step 1: Edge Case Handle

```javascript
if (n === 0 || n === 1)
```

0 aur 1 ke prime factors nahi hote.

---

## Step 2: Result Array

```javascript
const result = [];
```

Saare prime factors store karne ke liye.

---

## Step 3: Start Divisor

```javascript
let divisor = 2;
```

2 sabse chhota prime number hai.

---

## Step 4: Factor Check

```javascript
n % divisor === 0
```

Agar true hai to divisor factor hai.

---

## Step 5: Divide Number

```javascript
n = n / divisor;
```

Number ko chhota karte hain.

---

## Step 6: Next Factor

Agar divide nahi hua:

```javascript
divisor++;
```

Next possible factor check karte hain.

---

# ⚠️ Edge Cases

## Case 1

```
Input

1
```

Output

```
No prime factors
```

Reason:

```
1 prime number nahi hai.
```

---

## Case 2

```
Input

2
```

Process:

```
2 / 2 = 1
```

Output:

```
2
```

---

## Case 3

```
Input

13
```

13 ek prime number hai.

Output:

```
13
```

---

## Case 4

```
Input

36
```

Calculation:

```
36 = 2 × 2 × 3 × 3
```

Output:

```
2 2 3 3
```

---

## Case 5

```
Input

100
```

Calculation:

```
100 = 2 × 2 × 5 × 5
```

Output:

```
2 2 5 5
```

---

# ⚠️ Common Mistakes

## ❌ Har factor ko prime samajh lena

Wrong:

```
60 ke factors:

2 3 4 5 6
```

Sahi:

```
2 2 3 5
```

Kyuki:

```
4 aur 6 prime nahi hain.
```

---

## ❌ Factor milne ke baad divisor increase kar dena

Wrong:

```
60

2 mila

divisor = 3
```

Isse repeated factors miss ho sakte hain.

Correct:

```
Same divisor se dobara check karo.
```

---

## ❌ Original number save na karna

Prime factorization mein number gradually reduce hota hai.

Example:

```
60 → 30 → 15 → 5 → 1
```

Isliye process ko dhyan se handle karo.

---

# ⏱️ 7. Complexity

## Time Complexity

Current Solution:

```
O(n)
```

Worst case mein hume kaafi divisors check karne pad sakte hain.

---

## Optimized Approach

Agar hum sirf:

```
√n
```

tak check karein:

```
O(√n)
```

ho jayega.

Reason:

Factors pair mein aate hain.

Example:

```
36

1 × 36

2 × 18

3 × 12

4 × 9

6 × 6
```

---

## Space Complexity

```
O(k)
```

Jahan:

```
k = number of prime factors
```

Kyuki hum result array mein factors store kar rahe hain.

---

# 🎯 Interview Follow-up

Interviewer pooch sakta hai:

* Prime factor aur normal factor mein difference?
* Prime factorization ko optimize kaise karoge?
* Kisi number ke unique prime factors kaise nikaloge?
* Prime factors ki frequency kaise count karoge?
* Sieve of Eratosthenes ka use kahan hota hai?

---

# 🔄 Similar Problems

* Prime Number Check
* Count Factors
* Find All Factors
* Greatest Common Divisor (GCD)
* Least Common Multiple (LCM)
* Perfect Number
* Abundant Number
* Unique Prime Factors

Ye sab **Factor / Number Theory Pattern** follow karte hain.

---

# 🧩 Pattern Recognition

Agar question mein likha ho:

* Factor
* Divisor
* Prime Factor
* Prime Decomposition
* HCF / GCD
* LCM

To turant yaad karo:

```
Factors ke saath kaam karna hai.
```

Basic pattern:

```javascript
for(let i = 2; i <= n; i++){

    while(n % i === 0){

        // i is a factor

        n = n / i;

    }

}
```

Optimization:

```
Loop till √n
```

---

# 🔑 8. Yaad Rakhne Wali Baat (One-Liner)

> **Prime Factorization ka matlab hai kisi number ko sirf prime numbers ke multiplication form mein todna. Core idea: factor milte hi number ko divide karo aur repeat check karo.**

---

# 📚 Cheat Sheet

```
Start Factor

divisor = 2


Check Factor

n % divisor == 0


Remove Factor

n = n / divisor


Repeat

while n > 1


Example

60

2 × 2 × 3 × 5


Complexity

Normal: O(n)

Optimized: O(√n)


Space

O(k)
```

---

# 🏷️ Topic Tag

`#Math`
`#NumberTheory`
`#Prime`
`#PrimeFactorization`
`#Factors`
`#Divisor`
`#Modulo`
`#Loop`