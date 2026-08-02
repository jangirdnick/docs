# Find the Greatest Element and Its Index

---

# 📌 1. Question

> **Write a program that takes an integer `N`, creates an array of size `N`, and finds the greatest (maximum) element along with its zero-based index.**
>
> * Array ke sabhi elements ko check karna hai.
> * Sabse bada element (Maximum) aur uska **0-based index** return karna hai.
> * JavaScript mein function **`[maxElement, index]`** return karega.

### Example

**Input**

```text
6
2 96 69 77 145 20
```

**Output**

```text
Max element = 145 found at index 4
```

---

## Input Format

Pehli line mein integer `N` diya hota hai.

Dusri line mein `N` space-separated integers diye hote hain.

Example

```text
6
2 96 69 77 145 20
```

---

## Output Format

Maximum element aur uska zero-based index print ya return karo.

JavaScript mein:

```javascript
return [maxElement, index];
```

---

## Constraints

```text
1 ≤ N ≤ 10⁴

-2³¹ ≤ arr[i] ≤ 2³¹
```

---

# 📖 2. Keyword Bank (English → Hindi)

| English Word     | Hindi / Simple Meaning        |
| ---------------- | ----------------------------- |
| Array            | Numbers ki list               |
| Maximum          | Sabse bada number             |
| Index            | Position                      |
| Zero Based Index | Position 0 se start hoti hai  |
| Traverse         | Array ko ek-ek karke dekhna   |
| Compare          | Do values ka comparison karna |
| Update           | Nayi value assign karna       |
| Loop             | Baar-baar chalna              |

> 💡 **Tip:** Maximum find karte waqt sirf ek hi pass (loop) kaafi hota hai.

---

# 🧠 3. Question Ko Apne Shabdon Mein (Paraphrase)

> Is question mein array ke har element ko check karna hai aur jo sabse bada number mile usko yaad rakhna hai. Saath hi us number ki position (index) bhi store karni hai.

☑️ **Check:** Agar tum bol sako ki **"Jab bhi bada number mile, max aur index dono update kar denge."**, to question samajh aa gaya.

---

# 🛠️ 4. Approach / Method

## Technique ka naam

**Array Traversal + Maximum Tracking**

---

## Soch Hindi Mein

Sabse pehle:

* Pehla element hi maximum maan lo.
* Uska index `0` maan lo.

Ab poori array ko traverse karo.

Har element ke liye check karo:

* Agar current element maximum se bada hai

  * Maximum update karo.
  * Index bhi update karo.

Loop khatam hone ke baad maximum aur uska index return kar do.

---

## Algorithm

```text
Maximum = First Element

Index = 0

Loop through every element

    Agar current element > maximum

        Maximum update karo

        Index update karo

Loop ke baad

Return [Maximum, Index]
```

---

## Visualization

```
Array

[2, 96, 69, 77, 145, 20]

Start

Max = 2

↓

96 > 2

Max = 96
Index = 1

↓

69 < 96

Ignore

↓

77 < 96

Ignore

↓

145 > 96

Max = 145
Index = 4

↓

20 < 145

Ignore
```

---

# ✍️ 5. Dry Run (Chhota Example)

### Input

```text
5

10 23 45 67 89
```

---

### Step 1

```
Max = 10

Index = 0
```

---

### Step 2

```
23 > 10

Max = 23

Index = 1
```

---

### Step 3

```
45 > 23

Max = 45

Index = 2
```

---

### Step 4

```
67 > 45

Max = 67

Index = 3
```

---

### Step 5

```
89 > 67

Max = 89

Index = 4
```

---

### Final Output

```text
Max element = 89 found at index 4
```

---

# 💻 6. Actual Code / Answer

```javascript
function findGreatestElementAndIndex(arr) {
    let max = arr[0];
    let index = 0;

    for (let i = 0; i < arr.length; i++) {
        if (arr[i] > max) {
            max = arr[i];
            index = i;
        }
    }

    return [max, index];
}

module.exports = { findGreatestElementAndIndex };
```

---

# 🧩 Code Explanation

### Maximum Initialization

```javascript
let max = arr[0];
```

Pehla element maximum maan liya.

---

### Index Initialization

```javascript
let index = 0;
```

Pehle element ka index `0` hota hai.

---

### Loop

```javascript
for (let i = 0; i < arr.length; i++)
```

Ye poori array ko traverse karta hai.

---

### Comparison

```javascript
if (arr[i] > max)
```

Agar current element bada hai to maximum update hoga.

---

### Update Maximum

```javascript
max = arr[i];
```

Naya maximum store kar diya.

---

### Update Index

```javascript
index = i;
```

Maximum ki position bhi store kar li.

---

### Return Answer

```javascript
return [max, index];
```

JavaScript mein expected output isi format mein return karna hai.

---

# ⚠️ Common Mistakes

## ❌ Maximum ko `0` se initialize karna

Wrong

```javascript
let max = 0;
```

Negative numbers ke case mein galat answer dega.

Correct

```javascript
let max = arr[0];
```

---

## ❌ Index update na karna

Wrong

```javascript
if (arr[i] > max) {
    max = arr[i];
}
```

Correct

```javascript
if (arr[i] > max) {
    max = arr[i];
    index = i;
}
```

---

## ❌ `>=` use karna

Wrong

```javascript
if (arr[i] >= max)
```

Ye duplicate maximum hone par last index dega.

Correct

```javascript
if (arr[i] > max)
```

Isse first occurrence ka index milega.

---

## ❌ Array ki length ki jagah `n` galat use karna

Agar function mein sirf `arr` diya hai to:

```javascript
arr.length
```

use karo.

---

# ⏱️ 7. Complexity

### Time Complexity

```text
O(N)
```

Har element sirf ek baar check hota hai.

---

### Space Complexity

```text
O(1)
```

Sirf do variables (`max` aur `index`) use hue hain.

---

# 🎯 Pattern Recognition

Is question ko dekhte hi socho:

```text
Array

↓

Maximum Find

↓

Comparison

↓

Update Value

+

Update Index

↓

Return Answer
```

---

# 🔄 Similar Problems

* Find Minimum Element
* Second Largest Element
* First Occurrence of Maximum
* Largest and Smallest Element
* Find Peak Element
* Array Traversal Basics

---

# 🧩 Master Formula

```text
Start

↓

Maximum = First Element

↓

Index = 0

↓

Loop Through Array

↓

Current > Maximum

↓

Update Maximum

+

Update Index

↓

Return [Maximum, Index]
```

---

# 🔑 8. Yaad Rakhne Wali Baat (One-Liner)

> **Maximum find karte waqt pehla element initial maximum hota hai. Jab bhi bada element mile, maximum aur uska index dono update kar do.**

---

# 📚 Cheat Sheet

```text
Initial Maximum

arr[0]


Initial Index

0


Loop

0 → arr.length - 1


Comparison

arr[i] > max


Update Maximum

max = arr[i]


Update Index

index = i


Return

[max, index]


Time

O(N)


Space

O(1)
```

---

# 🏷️ Topic Tag

`#Array`
`#MaximumElement`
`#ArrayTraversal`
`#LinearSearch`
`#DSABasics`
`#JavaScript`
`#LogicBuilding`
`#BeginnerProgramming`
