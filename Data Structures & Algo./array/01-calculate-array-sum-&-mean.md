# Calculate Sum and Mean of Array Elements

---

# 📌 1. Question

> **Write a program that takes an integer `n`, creates an array of size `n`, accepts `n` integer inputs, and returns the sum and mean (average) of all array elements.**
>
> * Pehle array ke saare elements ka **sum** nikalo.
> * Phir **mean (average)** calculate karo.
> * JavaScript mein function ko **`[sum, mean]`** return karna hai.
> * Mean ko **1 decimal place** tak return karna hai.

### Example

**Input**

```text
5
1 2 3 4 5
```

**Output**

```text
Sum: 15
Mean: 3.0
```

---

## Input Format

* First line mein integer `n` diya hota hai.
* Second line mein `n` space-separated integers diye hote hain.

Example

```text
5
1 2 3 4 5
```

---

## Output Format

* Sum of array elements.
* Mean (Average) till **1 decimal place**.

JavaScript mein return karo:

```javascript
[sum, mean]
```

---

## Constraints

```text
1 ≤ n ≤ 10^6

-2^31 ≤ arr[i] ≤ 2^31
```

---

# 📖 2. Keyword Bank (English → Hindi)

| English Word   | Hindi / Simple Meaning          |
| -------------- | ------------------------------- |
| Array          | Numbers ki list                 |
| Element        | Array ka ek value               |
| Sum            | Sabhi numbers ka total          |
| Mean           | Average                         |
| Traverse       | Array ko ek-ek karke dekhna     |
| Loop           | Baar-baar chalne wala code      |
| Index          | Array ki position               |
| Floating Point | Decimal number                  |
| Accumulator    | Total store karne wala variable |

> 💡 **Tip:** Mean nikalne ka formula hamesha **Sum ÷ Total Elements** hota hai.

---

# 🧠 3. Question Ko Apne Shabdon Mein (Paraphrase)

> Ye question mujhse array ke saare numbers ka total nikalne ko keh raha hai aur uske baad us total ko array ke size se divide karke average (mean) return karna hai.

☑️ **Check:** Agar tum bol sako ki **"Pehle sum, phir sum ko n se divide karna hai."**, to question samajh aa gaya.

---

# 🛠️ 4. Approach / Method

## Technique ka naam

**Array Traversal + Accumulation**

---

## Soch Hindi Mein

Is question mein:

* Ek variable `sum` ko `0` se initialize karenge.
* Loop chalayenge aur har element ko `sum` mein add karenge.
* Loop ke baad:

```text
Mean = Sum / n
```

* Mean ko `1 decimal place` tak convert karenge.
* Last mein `[sum, mean]` return karenge.

---

## Algorithm

```text
Initialize sum = 0

Loop from 0 to n-1

    sum = sum + arr[i]

mean = sum / n

Return [sum, mean]
```

---

## Visualization

```
Array

[1,2,3,4,5]

↓

Sum

1+2+3+4+5

↓

15

↓

Mean

15 / 5

↓

3.0
```

---

# ✍️ 5. Dry Run (Chhota Example)

### Input

```text
4
10 20 30 40
```

---

### Step 1

```
sum = 0
```

---

### Step 2

```
sum = sum + 10

sum = 10
```

---

### Step 3

```
sum = 10 + 20

sum = 30
```

---

### Step 4

```
sum = 30 + 30

sum = 60
```

---

### Step 5

```
sum = 60 + 40

sum = 100
```

---

### Mean

```
100 / 4

25.0
```

---

### Final Output

```text
Sum: 100
Mean: 25.0
```

---

# 💻 6. Actual Code / Answer

```javascript
function calculateSumAndMean(arr, n) {
    let sum = 0;

    for (let i = 0; i < n; i++) {
        sum += arr[i];
    }

    let mean = sum / n;

    return [sum, mean.toFixed(1)];
}

module.exports = { calculateSumAndMean };
```

---

# 🧩 Code Explanation

### Initialize Sum

```javascript
let sum = 0;
```

Shuru mein total `0` hota hai.

---

### Traverse Array

```javascript
for (let i = 0; i < n; i++)
```

Ye loop array ke saare elements visit karta hai.

---

### Add Every Element

```javascript
sum += arr[i];
```

Har element ko sum mein add kar deta hai.

Example

```
sum = 0

↓

1

↓

3

↓

6

↓

10

↓

15
```

---

### Calculate Mean

```javascript
let mean = sum / n;
```

Average nikalne ka formula:

```text
Mean = Sum / Total Elements
```

---

### Convert to One Decimal Place

```javascript
mean.toFixed(1)
```

Example

```
3

↓

3.0
```

```
25

↓

25.0
```

```
2.6666

↓

2.7
```

---

### Return Answer

```javascript
return [sum, mean.toFixed(1)];
```

Question ke according array return karna hai.

---

# ⚠️ Common Mistakes

## ❌ Sum ko initialize na karna

Wrong

```javascript
let sum;
```

Correct

```javascript
let sum = 0;
```

---

## ❌ Mean loop ke andar calculate karna

Wrong

```javascript
for (...) {
    mean = sum / n;
}
```

Mean sirf loop complete hone ke baad calculate karo.

---

## ❌ `toFixed()` bhool jana

Wrong

```javascript
return [sum, mean];
```

Correct

```javascript
return [sum, mean.toFixed(1)];
```

---

## ❌ `n` ki jagah `arr.length` aur `n` ko mix kar dena

Agar question `n` deta hai to usi ka use karo.

---

# ⏱️ 7. Complexity

### Time Complexity

```text
O(N)
```

Array sirf ek baar traverse ho raha hai.

---

### Space Complexity

```text
O(1)
```

Sirf do variables (`sum` aur `mean`) use hue hain.

---

# 🎯 Pattern Recognition

Is type ke question ko dekhte hi ye socho:

```text
Array

↓

Loop

↓

Sum

↓

Mean = Sum / N

↓

Return Answer
```

---

# 🔄 Similar Problems

* Find Array Sum
* Find Average of Numbers
* Maximum Element in Array
* Minimum Element in Array
* Count Positive Numbers
* Find Even and Odd Count

---

# 🧩 Master Formula

```text
Initialize Sum = 0

↓

Loop Through Array

↓

Sum += arr[i]

↓

Mean = Sum / N

↓

Return [Sum, Mean]
```

---

# 🔑 8. Yaad Rakhne Wali Baat (One-Liner)

> **Array ka Mean nikalna ho to pehle Sum nikalo, phir us Sum ko Total Elements (`n`) se divide kar do.**

---

# 📚 Cheat Sheet

```text
Initialize

sum = 0


Loop

i = 0 → n-1


Add

sum += arr[i]


Mean

sum / n


One Decimal

mean.toFixed(1)


Return

[sum, mean]


Time

O(N)


Space

O(1)
```

---

# 🏷️ Topic Tag

`#Array`
`#ArrayTraversal`
`#Sum`
`#Mean`
`#Average`
`#ForLoop`
`#BasicProgramming`
`#DSABasics`
