# Minimum Value to Add for Balanced Array

---

# 📌 1. Question

> **Given an even-sized array, make the sum of the left half and right half equal by adding a minimum value to exactly one element.**
>
> - Array ka size even hai.
> - Left half ka sum aur right half ka sum compare karna hai.
> - Sirf **ek element** mein value add kar sakte hain.
> - Minimum required value return karna hai.
> - Agar dono halves already equal hain, answer `0` hoga.

### Example 1

**Input**

```text
1 2 1 2 1 3
```

Left half:

```text
1 + 2 + 1 = 4
```

Right half:

```text
2 + 1 + 3 = 6
```

Difference:

```text
6 - 4 = 2
```

So, left half ke kisi ek element mein `2` add karenge.

**Output**

```text
2
```

---

### Example 2

**Input**

```text
2 2 2 2
```

Left half:

```text
2 + 2 = 4
```

Right half:

```text
2 + 2 = 4
```

Already balanced.

**Output**

```text
0
```

---

# 📖 2. Keyword Bank (English → Hindi)

| English Word   | Hindi / Simple Meaning                         |
| -------------- | ---------------------------------------------- |
| Balanced Array | Dono halves ka sum equal hona                  |
| Left Half      | Array ka pehla half                            |
| Right Half     | Array ka doosra half                           |
| Sum            | Sabhi values ka total                          |
| Difference     | Do values ke beech ka antar                    |
| Add            | Kisi value mein number jodna                   |
| Minimum        | Sabse chhoti required value                    |
| Half           | Array ka aadha part                            |
| Even Size      | Jiska size 2 se completely divide ho           |
| Mid            | Left aur right half ko divide karne wala index |

> 💡 **Tip:** Question mein **left half vs right half ka sum** diya ho, to sabse pehle dono sums calculate karne ke baare mein socho.

---

# 🧠 3. Question Ko Apne Shabdon Mein

> Array ko do equal parts mein divide karo. Dono parts ka sum nikalo. Jo sum bada hai, chhote sum mein utni value add karni padegi jitni dono sums ke beech difference hai.

### Simple Logic

```text
Left Sum  = 4
Right Sum = 6

Difference = 6 - 4

Answer = 2
```

✅ **Check:** Agar tum bol sako:

> **"Dono halves ka sum nikalo aur unka absolute difference return karo."**

to question samajh aa gaya.

---

# 🛠️ 4. Approach / Method

## Technique ka naam

**Array Splitting + Sum Difference**

---

## Soch Hindi Mein

Sabse pehle array ka middle index nikalo:

```javascript
const mid = Math.floor(arr.length / 2);
```

Example:

```text
[1, 2, 1, 2, 1, 3]
          ↑
         mid
```

Array ko do parts mein divide karo:

```text
Left Half

[1, 2, 1]
```

```text
Right Half

[2, 1, 3]
```

Phir dono ka sum:

```text
leftSum  = 4
rightSum = 6
```

Difference:

```text
|4 - 6| = 2
```

Answer:

```text
2
```

---

## Algorithm

```text
mid = n / 2

leftSum = sum of first half

rightSum = sum of second half

answer = |leftSum - rightSum|

return answer
```

---

# ✍️ 5. Dry Run

### Input

```text
[1, 2, 1, 2, 1, 3]
```

### Step 1 — Find Middle

```text
n = 6

mid = 6 / 2

mid = 3
```

So:

```text
Left  = [1, 2, 1]
Right = [2, 1, 3]
```

---

### Step 2 — Calculate Left Sum

```text
1 + 2 + 1 = 4
```

```text
firstHalf = 4
```

---

### Step 3 — Calculate Right Sum

```text
2 + 1 + 3 = 6
```

```text
secondHalf = 6
```

---

### Step 4 — Difference

```text
|4 - 6|
```

```text
= 2
```

---

### Final Answer

```text
2
```

---

# 💻 6. Actual Code / Answer

Aapka current solution **logic ke according correct hai**:

```javascript
class Solution {
  minAddForBalance(arr) {
    const mid = Math.floor(arr.length / 2);

    const firstHalf = arr.slice(0, mid).reduce((a, b) => a + b, 0);

    const secondHalf = arr.slice(mid).reduce((a, b) => a + b, 0);

    return Math.abs(firstHalf - secondHalf);
  }
}

module.exports = { Solution };
```

```javascript
class Solution {
  minAddForBalance(arr) {
    const mid = Math.floor(arr.length / 2);
    let firstHalf = 0;
    let secondHalf = 0;

    for (let i = 0; i < arr.length; i++) {
      if (i < mid) firstHalf += arr[i];
      else secondHalf += arr[i];
    }

    return Math.abs(firstHalf - secondHalf);
  }
}

module.exports = { Solution };
```

```javascript
class Solution {
  minAddForBalance(arr) {
    let firstHalf = 0;
    let secondHalf = 0;
    const mid = arr.length >> 1; // bit version of Math.floor(/2)

    for (let i = 0; i < mid; i++) firstHalf += arr[i];
    for (let i = mid; i < arr.length; i++) secondHalf += arr[i];

    return Math.abs(firstHalf - secondHalf);
  }
}

module.exports = { Solution };
```

### Lekin DSA perspective se better approach

`slice()` unnecessary extra arrays create karta hai. Is question mein direct traversal better hai:

```javascript
class Solution {
  minAddForBalance(arr) {
    const mid = Math.floor(arr.length / 2);

    let leftSum = 0;
    let rightSum = 0;

    for (let i = 0; i < mid; i++) {
      leftSum += arr[i];
    }

    for (let i = mid; i < arr.length; i++) {
      rightSum += arr[i];
    }

    return Math.abs(leftSum - rightSum);
  }
}

module.exports = { Solution };
```

---

# 🧩 Code Explanation

### 1. Middle Find Karna

```javascript
const mid = Math.floor(arr.length / 2);
```

Agar:

```text
arr.length = 6
```

to:

```text
mid = 3
```

Isliye:

```text
0 1 2 | 3 4 5
---------
Left  | Right
```

---

### 2. Sum Variables

```javascript
let leftSum = 0;
let rightSum = 0;
```

Dono halves ka sum separately store karenge.

---

### 3. Left Half

```javascript
for (let i = 0; i < mid; i++) {
  leftSum += arr[i];
}
```

Example:

```text
[1, 2, 1 | 2, 1, 3]
 ↑     ↑
 0     2
```

Ye calculate karega:

```text
1 + 2 + 1 = 4
```

---

### 4. Right Half

```javascript
for (let i = mid; i < arr.length; i++) {
  rightSum += arr[i];
}
```

Ye calculate karega:

```text
2 + 1 + 3 = 6
```

---

### 5. Absolute Difference

```javascript
return Math.abs(leftSum - rightSum);
```

```text
Math.abs(4 - 6)

= 2
```

Agar:

```text
leftSum = 10
rightSum = 7
```

to:

```text
Math.abs(10 - 7)
= 3
```

Isliye hume manually decide nahi karna padta ki kaunsa half bada hai.

---

# ⚠️ Common Mistakes

## ❌ `slice()` ko zaroori samajhna

```javascript
arr.slice(0, mid);
```

Kaam karega, lekin ek naya array create karta hai.

Better:

```javascript
for (...)
```

Direct original array se sum calculate karo.

---

## ❌ Sirf `rightSum - leftSum`

Wrong:

```javascript
return rightSum - leftSum;
```

Agar left sum bada hua to negative answer aa jayega.

Correct:

```javascript
return Math.abs(leftSum - rightSum);
```

---

## ❌ Middle Index Galat Lena

Array:

```text
[1, 2, 1, 2, 1, 3]
```

Correct:

```text
mid = 3
```

Left:

```text
0 → 2
```

Right:

```text
3 → 5
```

---

## ❌ Actual Array Modify Karna

Is question mein array ko modify karne ki requirement nahi hai.

Sirf answer calculate karna hai.

So unnecessary mutation mat karo:

```javascript
arr[i] += difference;
```

---

# ⏱️ 7. Complexity

### Aapka Current Solution

```javascript
slice();
reduce();
```

Time:

```text
O(N)
```

Space:

```text
O(N)
```

Kyuki `slice()` new arrays create karta hai.

---

### Better Solution

```javascript
for loop
```

Time:

```text
O(N)
```

Space:

```text
O(1)
```

### Recommended

```text
Time  → O(N)
Space → O(1)
```

---

# 🎯 Pattern Recognition

Aise questions mein keywords dekho:

```text
Array
+
Even Size
+
Left Half
+
Right Half
+
Sum
+
Balance
```

To immediately socho:

```text
Find Mid
    ↓
Calculate Left Sum
    ↓
Calculate Right Sum
    ↓
Absolute Difference
```

---

# 🔄 Similar Problems

- Sum of Left and Right Half
- Balanced Array
- Equal Sum Partition
- Difference Between Two Halves
- Array Partition
- Prefix/Suffix Sum
- Running Sum Problems

---

# 🧩 Master Formula

```text
mid = n / 2

        ↓

leftSum = sum(arr[0 ... mid-1])

        ↓

rightSum = sum(arr[mid ... n-1])

        ↓

answer = |leftSum - rightSum|
```

---

# 🔑 8. Yaad Rakhne Wali Baat

> **Even-sized array ko middle se divide karo, dono halves ka sum nikalo aur unka absolute difference return karo. Wahi minimum value hai jo chhote half mein add karke array ko balanced bana sakti hai.**

---

# 📚 Cheat Sheet

```text
Step 1
mid = n / 2

Step 2
leftSum = first half ka sum

Step 3
rightSum = second half ka sum

Step 4
difference = Math.abs(leftSum - rightSum)

Step 5
return difference


Time  → O(N)
Space → O(1)
```

---

# 🏷️ Topic Tag

`#Array`
`#ArraySum`
`#BalancedArray`
`#Math`
`#ArrayPartition`
`#LogicBuilding`
`#DSABasics`
