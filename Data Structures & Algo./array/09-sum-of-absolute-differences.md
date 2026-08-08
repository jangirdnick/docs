# Sum of Absolute Differences of All Pairs

---

# 📌 1. Question

> **Given an array, calculate the sum of absolute differences between every possible pair of elements.**
>
> - Har pair `(i, j)` sirf **ek baar** consider karna hai.
> - Same element ke saath pair nahi banana hai.
> - `i < j` condition follow karni hai.
> - Difference ka absolute value lena hai.
> - JavaScript mein final sum return karna hai.

### Example 1

**Input**

```text
3
10 20 30
```

**Pairs**

```text
|10 - 20| = 10
|10 - 30| = 20
|20 - 30| = 10
```

**Output**

```text
40
```

---

### Example 2

**Input**

```text
4
1 5 3 7
```

**Pairs**

```text
|1 - 5| = 4
|1 - 3| = 2
|1 - 7| = 6
|5 - 3| = 2
|5 - 7| = 2
|3 - 7| = 4
```

**Output**

```text
20
```

---

## Input Format

- First line mein integer `n` diya hoga.
- Second line mein `n` space-separated integers honge.

Example:

```text
4
1 5 3 7
```

---

## Output Format

Sabhi unique pairs ke absolute differences ka sum return karo.

JavaScript mein:

```javascript
return totalSum;
```

---

## Constraints

```text
1 ≤ n ≤ 10^5

-10^9 ≤ arr[i] ≤ 10^9
```

> ⚠️ Agar values bahut badi ho sakti hain, to JavaScript mein `Number` ke instead `BigInt` useful ho sakta hai.

---

# 📖 2. Keyword Bank (English → Hindi)

| English Word        | Hindi / Simple Meaning                   |       |     |
| ------------------- | ---------------------------------------- | ----- | --- |
| Pair                | Do elements ka group                     |       |     |
| Difference          | Do values ka antar                       |       |     |
| Absolute            | Negative sign hata kar positive value    |       |     |
| Absolute Difference | `                                        | a - b | `   |
| Sum                 | Sab values ko add karna                  |       |     |
| Unique Pair         | Same pair ko dobara consider na karna    |       |     |
| Nested Loop         | Loop ke andar doosra loop                |       |     |
| Index               | Array ki position                        |       |     |
| Traversal           | Array ke elements ko visit karna         |       |     |
| BigInt              | Bahut bade integers ke liye JS data type |       |     |

> 💡 **Tip:** Agar question mein **"every pair"**, **"all pairs"** aur **"absolute difference"** aaye, to pehle pair formation aur `|a-b|` ko identify karo.

---

# 🧠 3. Question Ko Apne Shabdon Mein (Paraphrase)

> Array ke har do different elements ka difference nikalna hai, uska absolute value lena hai aur sabhi unique pairs ke differences ko add karna hai.

Example:

```text
[10, 20, 30]

Pairs:

10,20
10,30
20,30
```

Phir:

```text
10 + 20 + 10 = 40
```

✅ **Check:** Agar tum samajh gaye ki **"har pair ko sirf ek baar calculate karna hai"**, to question clear hai.

---

# 🛠️ 4. Approach / Method

## Technique ka naam

**Nested Loop + Pair Traversal + Absolute Difference**

---

## Soch Hindi Mein

Humein har possible pair check karna hai.

Isliye:

- Pehla loop `i` ko control karega.
- Dusra loop `j` ko `i + 1` se start karega.
- `i + 1` se start karne ki wajah se same pair dobara nahi aayega.
- Difference calculate karo.
- Agar difference negative hai to usko positive karo.
- Difference ko total sum mein add karo.

---

## Algorithm

```text
totalSum = 0

Loop i from 0 to n-1

    Loop j from i+1 to n-1

        diff = arr[i] - arr[j]

        If diff < 0

            diff = -diff

        Add diff to totalSum

Return totalSum
```

---

# 🔍 Why `j = i + 1`?

Ye is question ka important part hai.

Agar array hai:

```text
[10, 20, 30]
```

To pairs:

```text
(10,20)
(10,30)
(20,30)
```

Humein ye nahi chahiye:

```text
(20,10)
(30,10)
(30,20)
```

Kyuki:

```text
|10 - 20| = |20 - 10|
```

Dono same result denge.

Isliye:

```javascript
for (let j = i + 1; j < arr.length; j++)
```

use karte hain.

---

# 🧮 Visualization

Array:

```text
[10, 20, 30, 40]
```

### `i = 0`

```text
10

↓

10 with 20
10 with 30
10 with 40
```

### `i = 1`

```text
20

↓

20 with 30
20 with 40
```

### `i = 2`

```text
30

↓

30 with 40
```

### `i = 3`

```text
40

↓

No pair
```

Total pairs:

```text
(10,20)
(10,30)
(10,40)
(20,30)
(20,40)
(30,40)
```

---

# ✍️ 5. Dry Run (Chhota Example)

### Input

```text
[10, 20, 30]
```

Initially:

```text
totalSum = 0
```

---

### Step 1

```text
i = 0
j = 1

arr[i] = 10
arr[j] = 20
```

Difference:

```text
10 - 20 = -10
```

Absolute difference:

```text
10
```

Add:

```text
totalSum = 10
```

---

### Step 2

```text
i = 0
j = 2
```

Difference:

```text
10 - 30 = -20
```

Absolute difference:

```text
20
```

Add:

```text
totalSum = 30
```

---

### Step 3

```text
i = 1
j = 2
```

Difference:

```text
20 - 30 = -10
```

Absolute difference:

```text
10
```

Add:

```text
totalSum = 40
```

---

### Final Output

```text
40
```

---

# 💻 6. Actual Code / Answer

```javascript
class Solution {
  sumOfAbsDiff(arr) {
    let totalSum = 0n;

    for (let i = 0; i < arr.length; i++) {
      for (let j = i + 1; j < arr.length; j++) {
        let diff = arr[i] - arr[j];

        if (diff < 0n) {
          diff = -diff;
        }

        totalSum += diff;
      }
    }

    return totalSum;
  }
}

module.exports = { Solution };
```

```javascript
class Solution {
  sumOfAbsDiff(arr) {
    // Sort the array
    arr.sort((a, b) => (a < b ? -1 : a > b ? 1 : 0));

    let total = 0n;
    let prefix = 0n;

    for (let i = 0n; i < BigInt(arr.length); i++) {
      // contribution of current element with all previous
      total += arr[i] * i - prefix;
      prefix += arr[i];
    }

    return total;
  }
}

module.exports = { Solution };
```

```javascript
class Solution {
  sumOfAbsDiff(arr) {
    arr.sort((a, b) => (a < b ? -1 : a > b ? 1 : 0));

    let total = 0n;
    const n = BigInt(arr.length);

    for (let i = 0n; i < n; i++) {
      // each element contributes: (2*i - n + 1) * arr[i]
      total += (2n * i - n + 1n) * arr[i];
    }

    return total;
  }
}

module.exports = { Solution };
```

---

# 🧩 Code Explanation

## Step 1 — Create Total Sum

```javascript
let totalSum = 0n;
```

`totalSum` mein sabhi pair differences ka total store hoga.

`0n` ka matlab hai **BigInt zero**.

Example:

```text
10n
20n
30n
```

---

## Step 2 — First Loop

```javascript
for (let i = 0; i < arr.length; i++)
```

Ye first element select karta hai.

Example:

```text
i = 0 → 10
i = 1 → 20
i = 2 → 30
```

---

## Step 3 — Second Loop

```javascript
for (let j = i + 1; j < arr.length; j++)
```

Second element ko select karta hai.

Important:

```text
j = i + 1
```

Isliye same pair repeat nahi hota.

---

## Step 4 — Difference Calculate

```javascript
let diff = arr[i] - arr[j];
```

Example:

```text
arr[i] = 10
arr[j] = 30

diff = 10 - 30

diff = -20
```

---

## Step 5 — Absolute Value

```javascript
if (diff < 0n) {
  diff = -diff;
}
```

Agar difference negative hai:

```text
-20
```

to:

```text
20
```

ban jayega.

Iska matlab:

```text
|10 - 30| = 20
```

---

## Step 6 — Add To Total

```javascript
totalSum += diff;
```

Har pair ka difference total mein add hota jayega.

Example:

```text
10
+
20
+
10

= 40
```

---

## Step 7 — Return

```javascript
return totalSum;
```

Finally sabhi pairs ke differences ka total return ho jayega.

---

# ⚠️ Common Mistakes

## ❌ Same Pair Ko Do Baar Calculate Karna

Wrong:

```javascript
for (let j = 0; j < arr.length; j++)
```

Isse:

```text
(10,20)
(20,10)
```

dono calculate honge.

Correct:

```javascript
for (let j = i + 1; j < arr.length; j++)
```

---

## ❌ Same Element Ko Pair Banana

Wrong:

```text
(10,10)
(20,20)
```

Correct:

```javascript
j = i + 1;
```

---

## ❌ Absolute Value Na Lena

Wrong:

```javascript
let diff = arr[i] - arr[j];

totalSum += diff;
```

Agar:

```text
10 - 30 = -20
```

to negative value add ho jayegi.

Correct:

```javascript
if (diff < 0n) {
  diff = -diff;
}
```

---

## ❌ `Number` Aur `BigInt` Mix Karna

Wrong:

```javascript
let totalSum = 0n;

let diff = arr[i] - arr[j];
```

Agar `arr` ke elements `Number` hain aur `totalSum` `BigInt` hai, to JavaScript error dega.

For example:

```javascript
0n + 10;
```

❌ Allowed nahi hai.

Agar solution BigInt use kar raha hai to array values bhi BigInt honi chahiye:

```javascript
[10n, 20n, 30n];
```

---

# ⏱️ 7. Complexity

### Time Complexity

```text
O(N²)
```

Kyuki nested loops use ho rahe hain.

Number of pairs approximately:

```text
N × (N - 1) / 2
```

Example:

```text
N = 5

Pairs = 5 × 4 / 2
      = 10
```

---

### Space Complexity

```text
O(1)
```

Koi extra array ya data structure use nahi hua.

Sirf:

```javascript
totalSum;
diff;
i;
j;
```

jaise variables use ho rahe hain.

---

# 🎯 Pattern Recognition

Agar question mein ye words dikhein:

```text
Every pair
All pairs
Each pair
Pairwise
Absolute difference
Sum of differences
```

to pehle ye pattern identify karo:

```text
Array

↓

Choose first element

↓

Choose every element after it

↓

Calculate difference

↓

Take absolute value

↓

Add to answer
```

---

# 🔄 Similar Problems

- Sum of Pair Differences
- Sum of Absolute Differences
- Maximum Pair Difference
- Minimum Pair Difference
- Count All Pairs
- Pair Sum
- Count Pairs With Given Difference
- Maximum Difference Between Two Elements

---

# 🧩 Master Formula

```text
total = 0

↓

for i = 0 → n-1

    ↓

    for j = i+1 → n-1

        ↓

        diff = |arr[i] - arr[j]|

        ↓

        total += diff

↓

Return total
```

---

# 🔑 8. Yaad Rakhne Wali Baat (One-Liner)

> **Har unique pair ke liye `i` ke baad wale elements ko `j = i + 1` se traverse karo, `|arr[i] - arr[j]|` calculate karo aur sabhi differences ko total mein add kar do.**

---

# 📚 Cheat Sheet

```text
Pair Start

j = i + 1


Difference

diff = arr[i] - arr[j]


Absolute

if diff < 0

    diff = -diff


Add

totalSum += diff


Time

O(N²)


Space

O(1)
```

---

# 🏷️ Topic Tag

`#Array`
`#NestedLoop`
`#Pair`
`#AbsoluteDifference`
`#BruteForce`
`#BigInt`
`#DSABasics`
`#LogicBuilding`
