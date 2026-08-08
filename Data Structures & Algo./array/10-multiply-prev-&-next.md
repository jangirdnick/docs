# Multiplication of Previous and Next

---

# 📌 1. Question

> **Given an array of integers, har element ko uske previous aur next element ke multiplication se replace karna hai.**
>
> Special cases:
>
> - **First element:** first × second
> - **Last element:** last × second-last
> - **Middle elements:** previous × next
>
> JavaScript mein result ke liye new array use kiya ja sakta hai.

### Example 1

**Input**

```text
3
2 3 4
```

**Output**

```text
6 8 12
```

### Explanation

```text
First:
2 × 3 = 6

Middle:
2 × 4 = 8

Last:
4 × 3 = 12
```

---

### Example 2

**Input**

```text
5
1 2 3 4 5
```

**Output**

```text
2 3 8 15 20
```

### Explanation

```text
First:
1 × 2 = 2

Second:
1 × 3 = 3

Third:
2 × 4 = 8

Fourth:
3 × 5 = 15

Last:
5 × 4 = 20
```

---

## Input Format

- First line mein integer `n` diya hoga.
- Second line mein `n` space-separated integers honge.

Example:

```text
5
1 2 3 4 5
```

---

## Output Format

New array mein har element ko required multiplication ke result se replace karo.

Example:

```text
2 3 8 15 20
```

---

## Constraints

```text
1 ≤ n ≤ 10^5

-10^9 ≤ arr[i] ≤ 10^9
```

> ⚠️ `n == 1` ke case mein array unchanged rehna chahiye.

---

# 📖 2. Keyword Bank (English → Hindi)

| English Word   | Hindi / Simple Meaning                  |
| -------------- | --------------------------------------- |
| Previous       | Pichhla element                         |
| Next           | Agla element                            |
| Multiplication | Guna / `×`                              |
| First Element  | Sabse pehla element                     |
| Last Element   | Sabse aakhri element                    |
| Middle Element | Beech ka element                        |
| Index          | Array ki position                       |
| Replace        | Purani value ki jagah new value rakhna  |
| Traverse       | Array ko ek-ek karke check karna        |
| Edge Case      | Special/boundary situation              |
| New Array      | Result store karne ke liye doosra array |

> 💡 **Tip:** Is question mein sabse important cheez hai **index ke basis par 3 cases identify karna**:
>
> ```text
> First → next ke saath
> Middle → previous × next
> Last → previous ke saath
> ```

---

# 🧠 3. Question Ko Apne Shabdon Mein (Paraphrase)

> Har position par current element ko ignore karke uske **left wale aur right wale element ka multiplication** karna hai.
>
> Lekin first aur last element ke paas ek hi neighbor hota hai, isliye unke liye special rule use hoga.

### Example

```text
[1, 2, 3, 4, 5]

Index:
 0  1  2  3  4
```

For index `2`:

```text
Previous = 2
Current  = 3
Next     = 4

2 × 4 = 8
```

So:

```text
[1,2,3,4,5]
      ↓
[1,2,8,4,5]
```

---

# 🛠️ 4. Approach / Method

## Technique ka naam

**Array Traversal + Index-Based Conditions**

Is question mein complex algorithm ki zarurat nahi hai.

Bas array ko ek baar traverse karke:

```text
i === 0
```

```text
i === arr.length - 1
```

```text
otherwise
```

in 3 cases ko handle karna hai.

---

## Soch Hindi Mein

Har index `i` ke liye:

### Case 1 — First Element

```javascript
i === 0;
```

First element ka previous nahi hota.

Isliye:

```text
arr[0] × arr[1]
```

---

### Case 2 — Last Element

```javascript
i === arr.length - 1;
```

Last element ka next nahi hota.

Isliye:

```text
arr[n-1] × arr[n-2]
```

---

### Case 3 — Middle Element

Baaki sab elements ke liye:

```text
arr[i - 1] × arr[i + 1]
```

Current element `arr[i]` use nahi hoga.

---

# 🧩 Algorithm

```text
Create newArray

Loop i from 0 to n-1

    If i == 0

        newArray.push(arr[i] × arr[i + 1])

    Else if i == n - 1

        newArray.push(arr[i] × arr[i - 1])

    Else

        newArray.push(arr[i - 1] × arr[i + 1])

Return newArray
```

---

# 🔍 Visualization

Input:

```text
[1, 2, 3, 4, 5]
```

### Index 0

```text
[1, 2, 3, 4, 5]
 ↑  ↑
 i next

1 × 2 = 2
```

---

### Index 1

```text
[1, 2, 3, 4, 5]
    ↑
    i

Previous = 1
Next     = 3

1 × 3 = 3
```

---

### Index 2

```text
[1, 2, 3, 4, 5]
       ↑
       i

Previous = 2
Next     = 4

2 × 4 = 8
```

---

### Index 3

```text
[1, 2, 3, 4, 5]
          ↑
          i

Previous = 3
Next     = 5

3 × 5 = 15
```

---

### Index 4

```text
[1, 2, 3, 4, 5]
             ↑
             i

Previous = 4

5 × 4 = 20
```

Final:

```text
[2, 3, 8, 15, 20]
```

---

# ✍️ 5. Dry Run

### Input

```text
[2, 3, 4]
```

---

### Step 1

```text
i = 0

First element

arr[0] × arr[1]

2 × 3 = 6
```

```text
newArray = [6]
```

---

### Step 2

```text
i = 1

Middle element

arr[0] × arr[2]

2 × 4 = 8
```

```text
newArray = [6, 8]
```

---

### Step 3

```text
i = 2

Last element

arr[2] × arr[1]

4 × 3 = 12
```

```text
newArray = [6, 8, 12]
```

---

### Final Output

```text
[6, 8, 12]
```

---

# 💻 6. Actual Code / Answer

```javascript
class Solution {
  multiplyPrevNext(arr) {
    if (arr.length === 1) {
      return arr;
    }

    let newArray = [];

    for (let i = 0; i < arr.length; i++) {
      if (i === 0) {
        newArray.push(arr[i] * arr[i + 1]);
      } else if (i === arr.length - 1) {
        newArray.push(arr[i] * arr[i - 1]);
      } else {
        newArray.push(arr[i - 1] * arr[i + 1]);
      }
    }

    return newArray;
  }
}

module.exports = { Solution };
```

```javascript
class Solution {
  multiplyPrevNext(arr) {
    const n = arr.length;
    const result = new Array(n);

    for (let i = 0; i < n; i++) {
      const prev = i === 0 ? arr[i] : arr[i - 1];
      const next = i === n - 1 ? arr[i] : arr[i + 1];

      result[i] = prev * next;
    }

    return result;
  }
}

module.exports = { Solution };
```

```javascript
class Solution {
  multiplyPrevNext(arr) {
    const n = arr.length;
    return arr.map(
      (val, i) =>
        (i === 0 ? val : arr[i - 1]) * (i === n - 1 ? val : arr[i + 1]),
    );
  }
}

module.exports = { Solution };
```

---

# 🧩 Code Explanation

## 1. `n == 1` Edge Case

```javascript
if (arr.length === 1) {
  return arr;
}
```

Agar array mein sirf ek element hai:

```text
[5]
```

Uska previous bhi nahi hai aur next bhi nahi hai.

Question ke constraint ke according array unchanged rehna chahiye.

```text
[5] → [5]
```

---

## 2. Result Array

```javascript
let newArray = [];
```

Har calculated value ko `newArray` mein store karenge.

Example:

```text
Input:
[1,2,3,4,5]

newArray:
[]

↓
[2]

↓
[2,3]

↓
[2,3,8]

↓
[2,3,8,15]

↓
[2,3,8,15,20]
```

---

## 3. Traverse Array

```javascript
for (let i = 0; i < arr.length; i++)
```

Har index ko ek-ek karke process karenge.

```text
i = 0
i = 1
i = 2
...
i = n-1
```

---

## 4. First Element

```javascript
if (i === 0)
```

First element ka previous nahi hota.

Isliye:

```javascript
arr[i] * arr[i + 1];
```

Example:

```text
[2,3,4]

2 × 3 = 6
```

---

## 5. Last Element

```javascript
else if (i === arr.length - 1)
```

Last element ka next nahi hota.

Isliye:

```javascript
arr[i] * arr[i - 1];
```

Example:

```text
[2,3,4]

4 × 3 = 12
```

---

## 6. Middle Element

```javascript
else {
  newArray.push(arr[i - 1] * arr[i + 1]);
}
```

Middle element ke liye:

```text
Previous × Next
```

Example:

```text
[2,3,4]

      i
      ↓
[2, 3, 4]

Previous = 2
Next = 4

2 × 4 = 8
```

---

# ⚠️ Common Mistakes

## ❌ Current Element Ko Multiply Karna

Wrong:

```javascript
arr[i - 1] * arr[i];
```

Question mein **current element use nahi karna** hai.

Correct:

```javascript
arr[i - 1] * arr[i + 1];
```

---

## ❌ First Element Ko Normal Middle Logic Dena

Wrong:

```javascript
arr[i - 1] * arr[i + 1];
```

For:

```text
i = 0
```

`arr[-1]` invalid hai.

Correct:

```javascript
if (i === 0)
```

---

## ❌ Last Element Ko Normal Logic Dena

Wrong:

```javascript
arr[i - 1] * arr[i + 1];
```

Last index par:

```text
arr[i + 1]
```

undefined hoga.

Correct:

```javascript
else if (i === arr.length - 1)
```

---

## ❌ Original Array Ko Directly Modify Karna

Agar tum directly:

```javascript
arr[i] = arr[i - 1] * arr[i + 1];
```

karoge, to problem ho sakti hai.

Example:

```text
[1,2,3,4,5]
```

Agar index `1` modify kar diya:

```text
[1,3,3,4,5]
```

Ab next calculation ke liye original `arr[1]` nahi milega.

Isliye **new array approach safe hai**.

---

# ⏱️ 7. Complexity

### Time Complexity

```text
O(N)
```

Array ko sirf ek baar traverse kar rahe hain.

---

### Space Complexity

```text
O(N)
```

Result store karne ke liye:

```javascript
let newArray = [];
```

use kiya hai.

> Yahan **extra space allowed hai**, isliye `O(N)` space acceptable hai.

---

# 🎯 Pattern Recognition

Is question ko dekhte hi:

```text
Array

↓

Every element needs neighbor information

↓

First / Middle / Last

↓

Index-based conditions

↓

One traversal

↓

O(N)
```

### Important Pattern

```text
First
↓
current × next

Middle
↓
previous × next

Last
↓
current × previous
```

---

# 🔄 Similar Problems

Is pattern ke similar questions:

- Previous and Next Element
- Product of Neighbors
- Sum of Previous and Next
- Replace Element with Neighbor Sum
- Array Neighbor Operations
- Left and Right Element Problems
- Boundary Element Handling
- Array Traversal Problems

---

# 🧩 Master Formula

```text
if i == 0

    arr[i] × arr[i + 1]

else if i == n - 1

    arr[i] × arr[i - 1]

else

    arr[i - 1] × arr[i + 1]
```

Yaad rakhne ka easiest way:

```text
FIRST
current × next

MIDDLE
previous × next

LAST
current × previous
```

---

# 🔑 8. Yaad Rakhne Wali Baat (One-Liner)

> **Har element ke liye uske neighbors ka product nikalna hai; first aur last element ke liye boundary condition alag handle karni hai.**

---

# 📚 Cheat Sheet

```text
Problem
Previous × Next


First
arr[0] × arr[1]


Middle
arr[i-1] × arr[i+1]


Last
arr[n-1] × arr[n-2]


Technique
Array Traversal


Time
O(N)


Space
O(N)


Important
First / Middle / Last


Edge Case
N = 1
```

---

# 🏷️ Topic Tag

`#Array`
`#ArrayTraversal`
`#PreviousNext`
`#IndexBasedLogic`
`#NeighborOperations`
`#EdgeCases`
`#DSABasics`
`#LogicBuilding`
