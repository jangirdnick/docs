# Sort First Half Ascending and Second Half Descending

---

# 📌 1. Question

> **Given an array of integers, sort the first half in ascending order and the second half in descending order.**
>
> - Array ka size **even ya odd**, dono ho sakta hai.
> - Agar `n` odd hai, to **middle element second half** ka part hoga.
> - Original array ko final sorted form mein return karna hai.
> - First half → **Ascending**
> - Second half → **Descending**

### Example 1

**Input**

```text
2 6 3 1 9 8 5
```

Array length:

```text
n = 7
```

Middle:

```text
mid = 7 >> 1 = 3
```

So:

```text
First Half  → [2, 6, 3]
Second Half → [1, 9, 8, 5]
```

First half ascending:

```text
[2, 3, 6]
```

Second half descending:

```text
[9, 8, 5, 1]
```

**Output**

```text
2 3 6 9 8 5 1
```

---

### Example 2

**Input**

```text
1 2 3 4
```

```text
First Half  → [1, 2]
Second Half → [3, 4]
```

First half ascending:

```text
[1, 2]
```

Second half descending:

```text
[4, 3]
```

**Output**

```text
1 2 4 3
```

---

# 📖 2. Keyword Bank (English → Hindi)

| English Word     | Hindi / Simple Meaning                      |
| ---------------- | ------------------------------------------- |
| Sort             | Values ko order mein arrange karna          |
| First Half       | Array ka pehla part                         |
| Second Half      | Array ka doosra part                        |
| Ascending        | Chhote se bade: `1, 2, 3`                   |
| Descending       | Bade se chhote: `3, 2, 1`                   |
| Middle           | Array ka beech wala element                 |
| Split            | Array ko parts mein divide karna            |
| Compare Function | Sort ko batata hai values kaise order hongi |

> 💡 **Tip:** Question mein agar **“first half ascending + second half descending”** dikhe, to pehle **middle index** find karo, phir dono halves ko separately sort karo.

---

# 🧠 3. Question Ko Apne Shabdon Mein

> Array ko middle se do parts mein divide karna hai. Pehle part ko small-to-large sort karna hai aur doosre part ko large-to-small sort karna hai.

### Simple Logic

```text
Original

[2, 6, 3 | 1, 9, 8, 5]

       ↓

First Half
[2, 3, 6]

Second Half
[9, 8, 5, 1]

       ↓

[2, 3, 6, 9, 8, 5, 1]
```

✅ **Check:** Agar tum bol sako:

> **"Middle find karo, left half ascending sort karo aur right half descending sort karo."**

to question samajh aa gaya.

---

# 🛠️ 4. Approach / Method

## Technique ka naam

**Array Splitting + Separate Sorting**

---

## Soch Hindi Mein

### Step 1 — Middle Find Karo

```javascript
let mid = arr.length >> 1;
```

`>> 1` ka matlab integer ko approximately `/ 2` karna.

Example:

```text
n = 7

7 >> 1

= 3
```

So:

```text
Indexes:

0 1 2 | 3 4 5 6
-------|---------
First  | Second
Half   | Half
```

Important:

> Odd length hone par middle element second half mein jayega.

---

### Step 2 — First Half Sort

```javascript
arr.slice(0, mid);
```

First half mil jayega.

Ascending ke liye:

```javascript
.sort((a, b) => a - b)
```

Example:

```text
[6, 2, 3]

↓

[2, 3, 6]
```

---

### Step 3 — Second Half Sort

```javascript
arr.slice(mid);
```

Second half mil jayega.

Descending ke liye:

```javascript
.sort((a, b) => b - a)
```

Example:

```text
[1, 9, 8, 5]

↓

[9, 8, 5, 1]
```

---

### Step 4 — Original Array Update

Sorted values ko original array mein wapas place karna hai.

```text
First half  → arr[0 ... mid-1]

Second half → arr[mid ... n-1]
```

---

# 🔢 Algorithm

```text
mid = n / 2

firstHalf = arr[0 ... mid-1]
secondHalf = arr[mid ... n-1]

Sort firstHalf ascending

Sort secondHalf descending

Copy firstHalf back to arr

Copy secondHalf back to arr

Return arr
```

---

# ✍️ 5. Dry Run

### Input

```text
[2, 6, 3, 1, 9, 8, 5]
```

---

### Step 1 — Find Middle

```text
n = 7

mid = 7 >> 1

mid = 3
```

Array:

```text
[2, 6, 3 | 1, 9, 8, 5]
  ←────→   ←─────────→
  First      Second
  Half       Half
```

---

### Step 2 — First Half

```text
[2, 6, 3]
```

Ascending sort:

```text
[2, 3, 6]
```

---

### Step 3 — Second Half

```text
[1, 9, 8, 5]
```

Descending sort:

```text
[9, 8, 5, 1]
```

---

### Step 4 — Combine

```text
[2, 3, 6] + [9, 8, 5, 1]
```

Final:

```text
[2, 3, 6, 9, 8, 5, 1]
```

---

# 💻 6. Actual Code / Answer

Aapka solution **correct hai** aur given problem ko properly solve karta hai.

```javascript
class Solution {
  sortHalves(arr) {
    let mid = arr.length >> 1;

    arr
      .slice(0, mid)
      .sort((a, b) => a - b)
      .forEach((val, i) => {
        arr[i] = val;
      });

    arr
      .slice(mid)
      .sort((a, b) => b - a)
      .forEach((val, i) => {
        arr[mid + i] = val;
      });

    return arr;
  }
}

module.exports = Solution;
```

```javascript
class Solution {
  sortHalves(arr) {
    const mid = arr.length >> 1;

    for (let i = 0; i < mid - 1; i++) {
      for (let j = 0; j < mid - i - 1; j++) {
        if (arr[j] > arr[j + 1]) {
          [arr[j], arr[j + 1]] = [arr[j + 1], arr[j]];
        }
      }
    }

    for (let i = mid; i < arr.length - 1; i++) {
      for (let j = mid; j < arr.length - (i - mid) - 1; j++) {
        if (arr[j] < arr[j + 1]) {
          [arr[j], arr[j + 1]] = [arr[j + 1], arr[j]];
        }
      }
    }

    return arr;
  }
}

module.exports = Solution;
```

```javascript
class Solution {
  sortHalves(arr) {
    const mid = arr.length >> 1;

    const left = arr.slice(0, mid).sort((a, b) => a - b);
    const right = arr.slice(mid).sort((a, b) => b - a);

    for (let i = 0; i < mid; i++) arr[i] = left[i];
    for (let i = 0; i < right.length; i++) arr[mid + i] = right[i];

    return arr;
  }
}

module.exports = Solution;
```

---

# 🧩 Code Explanation

## 1. Find Middle

```javascript
let mid = arr.length >> 1;
```

Example:

```text
arr.length = 7

7 >> 1 = 3
```

Therefore:

```text
First Half  → indexes 0, 1, 2

Second Half → indexes 3, 4, 5, 6
```

---

## 2. Extract First Half

```javascript
arr.slice(0, mid);
```

Example:

```text
arr = [2, 6, 3, 1, 9, 8, 5]

slice(0, 3)

↓

[2, 6, 3]
```

---

## 3. Ascending Sort

```javascript
.sort((a, b) => a - b)
```

Example:

```text
[6, 2, 3]

↓

[2, 3, 6]
```

### Why `a - b`?

JavaScript ka default `.sort()` numbers ko strings ki tarah sort kar sakta hai.

```javascript
[10, 2, 5].sort();
```

can produce:

```text
[10, 2, 5]
```

Numeric ascending ke liye:

```javascript
(a, b) => a - b;
```

use karte hain.

---

## 4. Put First Half Back

```javascript
.forEach((val, i) => {
  arr[i] = val;
});
```

Example:

```text
Sorted:

[2, 3, 6]

↓

arr[0] = 2
arr[1] = 3
arr[2] = 6
```

Original array:

```text
[2, 3, 6, 1, 9, 8, 5]
```

---

## 5. Extract Second Half

```javascript
arr.slice(mid);
```

```text
mid = 3

slice(3)

↓

[1, 9, 8, 5]
```

---

## 6. Descending Sort

```javascript
.sort((a, b) => b - a)
```

Example:

```text
[1, 9, 8, 5]

↓

[9, 8, 5, 1]
```

### Yaad Rakho

```text
Ascending

a - b
```

```text
Descending

b - a
```

---

## 7. Put Second Half Back

```javascript
arr[mid + i] = val;
```

Agar:

```text
mid = 3
```

to indexes honge:

```text
i = 0 → arr[3]
i = 1 → arr[4]
i = 2 → arr[5]
i = 3 → arr[6]
```

So:

```text
[2, 3, 6, 9, 8, 5, 1]
```

---

# ⚠️ Common Mistakes

## ❌ First Half ko descending kar dena

Wrong:

```javascript
.sort((a, b) => b - a)
```

First half ke liye correct:

```javascript
.sort((a, b) => a - b)
```

---

## ❌ Second Half ko ascending kar dena

Wrong:

```javascript
.sort((a, b) => a - b)
```

Second half ke liye:

```javascript
.sort((a, b) => b - a)
```

---

## ❌ Odd Array Mein Middle Galat Lena

Input:

```text
[2, 6, 3, 1, 9, 8, 5]
```

`n = 7`

```text
mid = 3
```

Correct split:

```text
[2, 6, 3] | [1, 9, 8, 5]
```

**Index `3` second half mein jayega.**

---

## ❌ Default `.sort()` Use Karna

Avoid:

```javascript
arr.sort();
```

Numbers ke liye explicitly comparator do:

```javascript
arr.sort((a, b) => a - b);
```

or:

```javascript
arr.sort((a, b) => b - a);
```

---

## ❌ Sorted Half Ko Original Array Mein Copy Na Karna

Sirf:

```javascript
arr.slice(0, mid).sort(...)
```

karne se original `arr` change nahi hota, kyunki `slice()` new array deta hai.

Isliye sorted values ko original array mein place karna zaroori hai.

---

# ⏱️ 7. Complexity

Aapke solution mein:

### First Half

```text
slice()      → O(N)
sort()       → O(N log N)
forEach()    → O(N)
```

### Second Half

```text
slice()      → O(N)
sort()       → O(N log N)
forEach()    → O(N)
```

Overall:

```text
Time Complexity → O(N log N)
```

### Space Complexity

`slice()` dono halves ke liye new arrays create karta hai:

```text
Space Complexity → O(N)
```

---

# 🎯 Pattern Recognition

Question mein ye words dekho:

```text
Array
+
First Half
+
Second Half
+
Ascending
+
Descending
```

Immediately socho:

```text
Find Mid
    ↓
Split Array
    ↓
First Half → Ascending
    ↓
Second Half → Descending
    ↓
Put Back
```

---

# 🧠 Important Pattern

### Even Length

```text
[1, 5, 3, 8, 2, 7]

mid = 3

[1, 5, 3] | [8, 2, 7]
```

Both halves equal size.

---

### Odd Length

```text
[1, 5, 3, 8, 2, 7, 4]

mid = 3

[1, 5, 3] | [8, 2, 7, 4]
```

Second half mein **one extra element** hoga.

---

# 🔄 Similar Problems

- Sort First Half Ascending
- Sort Second Half Descending
- Sort Odd/Even Positions
- Sort Array in Two Parts
- Ascending + Descending Array
- Array Partition + Sorting
- Half-wise Array Transformation

---

# 🧩 Master Formula

```text
mid = n >> 1

↓

First Half
[0 ... mid-1]

↓

sort(a, b => a - b)

↓

Second Half
[mid ... n-1]

↓

sort(a, b => b - a)

↓

Put Both Back
```

---

# 🔑 8. Yaad Rakhne Wali Baat

> **Pehle `mid` nikalo. `0` se `mid-1` tak ascending sort karo aur `mid` se end tak descending sort karo. Odd length mein `mid` wala element second half ka part hoga.**

---

# 📚 Cheat Sheet

```text
Middle

mid = n >> 1


First Half

0 → mid - 1


Ascending

(a, b) => a - b


Second Half

mid → n - 1


Descending

(a, b) => b - a


Final

First Half + Second Half


Time

O(N log N)


Space

O(N)
```

---

# 🏷️ Topic Tag

`#Array`
`#Sorting`
`#Ascending`
`#Descending`
`#ArrayPartition`
`#JavaScriptSort`
`#LogicBuilding`
`#DSABasics`
