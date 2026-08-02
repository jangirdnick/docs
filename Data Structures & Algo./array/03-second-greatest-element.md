# Find the Second Greatest Element

---

# 📌 1. Question

> **Write a program that takes an integer `N`, creates an array of size `N`, and finds the second greatest (second largest) element in the array.**
>
> * Array ke sabhi elements ko check karna hai.
> * Sabse bada (Maximum) aur uske baad sabse bada (Second Maximum) element find karna hai.
> * JavaScript mein function sirf **second greatest element** return karega.

### Example

**Input**

```text
6
2 96 69 77 145 20
```

**Output**

```text
Second greatest element = 96
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

Second greatest element print ya return karo.

JavaScript mein:

```javascript
return secondGreatestElement;
```

---

## Constraints

```text
2 ≤ N ≤ 10³

-2³¹ ≤ arr[i] ≤ 2³¹

Second greatest element hamesha exist karega.
```

---

# 📖 2. Keyword Bank (English → Hindi)

| English Word   | Hindi / Simple Meaning      |
| -------------- | --------------------------- |
| Array          | Numbers ki list             |
| Maximum        | Sabse bada number           |
| Second Maximum | Dusra sabse bada number     |
| Traverse       | Array ko ek-ek karke dekhna |
| Compare        | Do values compare karna     |
| Update         | Nayi value assign karna     |
| Loop           | Baar-baar chalna            |
| Duplicate      | Same value dobara aana      |

> 💡 **Tip:** Is question mein ek hi loop mein **Maximum** aur **Second Maximum** dono find kiye ja sakte hain.

---

# 🧠 3. Question Ko Apne Shabdon Mein (Paraphrase)

> Is question mein array ka sabse bada number nahi, balki uske baad wala sabse bada number find karna hai.

Jab bhi koi naya maximum mile:

* Purana maximum second maximum ban jayega.
* Naya number maximum ban jayega.

Agar current number maximum nahi hai lekin second maximum se bada hai, to second maximum update hoga.

☑️ **Check:** Agar tum bol sako ki **"Maximum aur Second Maximum dono ko saath-saath update karna hai."**, to question samajh aa gaya.

---

# 🛠️ 4. Approach / Method

## Technique ka naam

**Single Traversal + Two Variables**

---

## Soch Hindi Mein

Do variables banao:

```text
Maximum

Second Maximum
```

Dono ko shuru mein:

```text
-Infinity
```

rakho.

Ab poori array ko traverse karo.

### Case 1

Agar current element maximum se bada hai

To:

* Second Maximum = Maximum
* Maximum = Current Element

---

### Case 2

Agar current element:

* Maximum se chhota hai
* Lekin Second Maximum se bada hai

To:

* Second Maximum update kar do.

Loop ke baad Second Maximum answer hoga.

---

## Algorithm

```text
Maximum = -Infinity

Second Maximum = -Infinity

Loop through every element

    Agar current > Maximum

        Second Maximum = Maximum

        Maximum = Current

    Else if current > Second Maximum

        Aur current ≠ Maximum

        Second Maximum = Current

Return Second Maximum
```

---

## Visualization

```
Array

[2, 96, 69, 77, 145, 20]

Start

Max = -∞

Second = -∞

↓

2

Max = 2

↓

96

Second = 2

Max = 96

↓

69

Second = 69

↓

77

Second = 77

↓

145

Second = 96

Max = 145

↓

20

Ignore

Answer = 96
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
Current = 10

Max = 10

Second = -∞
```

---

### Step 2

```
Current = 23

Second = 10

Max = 23
```

---

### Step 3

```
Current = 45

Second = 23

Max = 45
```

---

### Step 4

```
Current = 67

Second = 45

Max = 67
```

---

### Step 5

```
Current = 89

Second = 67

Max = 89
```

---

### Final Output

```text
Second greatest element = 67
```

---

# 💻 6. Actual Code / Answer

```javascript
function findSecondGreatestElement(arr) {

    let max = -Infinity;
    let secondMax = -Infinity;

    for (let i = 0; i < arr.length; i++) {

        if (arr[i] > max) {
            secondMax = max;
            max = arr[i];

        } else if (arr[i] > secondMax && arr[i] !== max) {
            secondMax = arr[i];
        }

    }

    return secondMax;
}

module.exports = { findSecondGreatestElement };
```

---

# 🧩 Code Explanation

### Maximum Initialization

```javascript
let max = -Infinity;
```

Shuru mein maximum ko sabse chhoti possible value di.

---

### Second Maximum Initialization

```javascript
let secondMax = -Infinity;
```

Second maximum bhi sabse chhoti value se start hoga.

---

### Loop

```javascript
for (let i = 0; i < arr.length; i++)
```

Ye poori array ko traverse karta hai.

---

### New Maximum

```javascript
if (arr[i] > max)
```

Agar current element maximum se bada hai.

---

### Update Maximum

```javascript
secondMax = max;
max = arr[i];
```

Purana maximum second maximum ban gaya.

Naya number maximum ban gaya.

---

### Update Second Maximum

```javascript
else if (arr[i] > secondMax && arr[i] !== max)
```

Agar current element:

* Maximum nahi hai
* Lekin second maximum se bada hai

To second maximum update hoga.

---

### Return Answer

```javascript
return secondMax;
```

Function second greatest element return karta hai.

---

# ⚠️ Common Mistakes

## ❌ Sirf Maximum find karna

Wrong

```javascript
if (arr[i] > max) {
    max = arr[i];
}
```

Second maximum kabhi update hi nahi hoga.

---

## ❌ Duplicate Maximum ko Second Maximum bana dena

Wrong

```javascript
else if (arr[i] > secondMax)
```

Agar array ho:

```text
10 20 20
```

To answer galat aa sakta hai.

Correct

```javascript
else if (arr[i] > secondMax && arr[i] !== max)
```

---

## ❌ `0` se initialize karna

Wrong

```javascript
let max = 0;
let secondMax = 0;
```

Negative numbers ke case mein answer galat hoga.

Correct

```javascript
let max = -Infinity;
let secondMax = -Infinity;
```

---

## ❌ Do loops use karna

Ye bhi sahi hai, lekin efficient solution nahi.

Ek hi loop mein dono values mil sakti hain.

---

# ⏱️ 7. Complexity

### Time Complexity

```text
O(N)
```

Sirf ek baar array traverse hoti hai.

---

### Space Complexity

```text
O(1)
```

Sirf do variables use hue hain.

---

# 🎯 Pattern Recognition

Is question ko dekhte hi socho:

```text
Array

↓

Maximum

+

Second Maximum

↓

Compare

↓

Update

↓

Return Second Maximum
```

---

# 🔄 Similar Problems

* Find Greatest Element
* Find Smallest Element
* Find Second Smallest Element
* Third Largest Element
* Kth Largest Element
* Array Traversal

---

# 🧩 Master Formula

```text
Start

↓

Maximum = -Infinity

↓

Second Maximum = -Infinity

↓

Loop Through Array

↓

Current > Maximum

↓

Second = Maximum

↓

Maximum = Current

↓

Else

Current > Second

AND

Current ≠ Maximum

↓

Second = Current

↓

Return Second Maximum
```

---

# 🔑 8. Yaad Rakhne Wali Baat (One-Liner)

> **Jab bhi naya maximum mile, purana maximum automatically second maximum ban jata hai. Agar current number maximum nahi hai lekin second maximum se bada hai, to second maximum update kar do.**

---

# 📚 Cheat Sheet

```text
Maximum

-Infinity


Second Maximum

-Infinity


Loop

0 → arr.length - 1


Current > Maximum

Second = Maximum

Maximum = Current


Else If

Current > Second

AND

Current ≠ Maximum


Update

Second = Current


Return

Second Maximum


Time

O(N)


Space

O(1)
```

---

# 🏷️ Topic Tag

`#Array`
`#SecondLargest`
`#MaximumElement`
`#ArrayTraversal`
`#LinearSearch`
`#DSABasics`
`#JavaScript`
`#LogicBuilding`
