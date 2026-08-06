# Copy Array and Reverse

---

# 📌 1. Question

> **Write a program that takes an array of size `n`, creates a new array containing the same elements in reverse order, and returns the reversed array.**
>
> - Original array ko change **nahi** karna hai.
> - Ek **naya array** banana hai.
> - JavaScript mein function ko **reversed array return** karna hai.

### Example 1

**Input**

```text
5
1 2 3 4 5
```

**Output**

```text
5 4 3 2 1
```

---

### Example 2

**Input**

```text
4
9 8 7 6
```

**Output**

```text
6 7 8 9
```

---

## Input Format

- First line mein integer `n` diya hoga.
- Second line mein `n` space-separated integers honge.

Example

```text
5
1 2 3 4 5
```

---

## Output Format

Reversed array return karo.

JavaScript mein:

```javascript
return reversedArray;
```

---

## Constraints

```text
1 ≤ n ≤ 1000

-2^31 ≤ arr[i] ≤ 2^31
```

---

# 📖 2. Keyword Bank (English → Hindi)

| English Word   | Hindi / Simple Meaning            |
| -------------- | --------------------------------- |
| Array          | Elements ka collection            |
| Reverse        | Ulta karna                        |
| Copy           | Naya duplicate banana             |
| Index          | Position number                   |
| Loop           | Baar-baar chalne wala code        |
| Push           | Array ke end mein value add karna |
| Original Array | Jo input mila hai                 |
| Reversed Array | Ulta order wala array             |

> 💡 **Tip:** Question original array ko reverse karne ka nahi, **copy karke reverse array banane** ka hai.

---

# 🧠 3. Question Ko Apne Shabdon Mein (Paraphrase)

> Ek array diya gaya hai. Mujhe uske elements ko last se first tak lekar ek naya array banana hai aur wahi return karna hai.

✅ **Check:** Agar tum bol sako ki **"Last element pehle aur first element last ho jayega"**, to question samajh aa gaya.

---

# 🛠️ 4. Approach / Method

## Technique ka naam

**Reverse Traversal + New Array**

---

## Soch Hindi Mein

- Ek empty array banao.
- Original array ko **last index se first index** tak traverse karo.
- Har element ko naye array mein `push()` karo.
- Loop khatam hone ke baad naya array return kar do.

---

## Algorithm

```text
Create an empty array

Loop from last index to first index

    Push current element into new array

Return new array
```

---

## Visualization

```
Original Array

[1, 2, 3, 4, 5]

↓

Start from last

5

↓

5 4

↓

5 4 3

↓

5 4 3 2

↓

5 4 3 2 1
```

---

# ✍️ 5. Dry Run (Chhota Example)

### Input

```text
[10, 20, 30]
```

---

### Step 1

```
copyArray = []

i = 2

Push 30

[30]
```

---

### Step 2

```
i = 1

Push 20

[30, 20]
```

---

### Step 3

```
i = 0

Push 10

[30, 20, 10]
```

---

### Final Output

```text
[30, 20, 10]
```

---

# 💻 6. Actual Code / Answer

```javascript
function copyAndReverseArray(arr) {
  let copyArray = [];

  for (let i = arr.length - 1; i >= 0; i--) {
    copyArray.push(arr[i]);
  }

  return copyArray;
}

module.exports = { copyAndReverseArray };
```

```javascript
function copyAndReverseArray(arr) {
  // Write your logic here

  let copyArray = [...arr].reverse();

  return copyArray;
}

module.exports = { copyAndReverseArray };
```

---

# 🧩 Code Explanation

### Create New Array

```javascript
let copyArray = [];
```

Yeh reversed elements store karega.

---

### Start From Last Index

```javascript
for (let i = arr.length - 1; i >= 0; i--)
```

Loop last element se shuru hota hai aur first element tak aata hai.

Example

```
Array

[1,2,3,4,5]

Indexes

0 1 2 3 4

Loop

4 → 3 → 2 → 1 → 0
```

---

### Add Element

```javascript
copyArray.push(arr[i]);
```

Har element ko naye array ke end mein add kar dete hain.

Example

```
Push 5

[5]

↓

Push 4

[5,4]

↓

Push 3

[5,4,3]
```

---

### Return Result

```javascript
return copyArray;
```

Final reversed array return ho jata hai.

---

# ⚠️ Common Mistakes

## ❌ Original array ko reverse kar dena

Wrong

```javascript
arr.reverse();

return arr;
```

Ye original array ko modify kar deta hai.

Correct

```javascript
let copyArray = [];

...

return copyArray;
```

---

## ❌ Loop ko first se last chalana

Wrong

```javascript
for (let i = 0; i < arr.length; i++)
```

Isse reverse order nahi milega.

Correct

```javascript
for (let i = arr.length - 1; i >= 0; i--)
```

---

## ❌ Push ki jagah wrong index use karna

Wrong

```javascript
copyArray.push(arr[0]);
```

Har baar same element add hoga.

Correct

```javascript
copyArray.push(arr[i]);
```

---

## ❌ Return bhool jana

Wrong

```javascript
copyArray;
```

Correct

```javascript
return copyArray;
```

---

# ⏱️ 7. Complexity

### Time Complexity

```text
O(N)
```

Har element sirf ek baar visit hota hai.

---

### Space Complexity

```text
O(N)
```

Ek naya array ban raha hai jisme `N` elements store honge.

---

# 🎯 Pattern Recognition

Is type ke questions dekhte hi socho:

```text
Given Array

↓

Create New Array

↓

Traverse Backward

↓

Push Elements

↓

Return Reversed Array
```

---

# 🔄 Similar Problems

- Reverse an Array
- Copy Array
- Reverse String
- Rotate Array
- Reverse Using Two Pointers
- Print Array in Reverse

---

# 🧩 Master Formula

```text
Create Empty Array

↓

Loop from Last Index

↓

Push Current Element

↓

Return New Array
```

---

# 🔑 8. Yaad Rakhne Wali Baat (One-Liner)

> **Reverse copy banane ke liye array ko last index se first index tak traverse karo aur har element ko naye array mein `push()` karte jao.**

---

# 📚 Cheat Sheet

```text
Create Array

let copyArray = []


Loop

i = arr.length - 1

↓

0


Push

copyArray.push(arr[i])


Return

copyArray


Time

O(N)


Space

O(N)
```

---

# 🏷️ Topic Tag

`#Array`
`#ReverseArray`
`#CopyArray`
`#ForLoop`
`#BasicProgramming`
`#LogicBuilding`
`#DSABasics`
