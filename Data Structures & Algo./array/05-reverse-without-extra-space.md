# Array Reverse Without Using Extra Space

---

# 📌 1. Question

> **Write a program that reverses the elements of an integer array in-place, without using any extra space.**
>
> - Original array ko **directly modify** karna hai.
> - **Naya array nahi banana hai.**
> - JavaScript mein **kuch return ya print nahi karna**, sirf original array ko reverse karna hai.

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
3
7 8 9
```

**Output**

```text
9 8 7
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

Original array ko reverse karo.

JavaScript mein:

```javascript
// Do not return anything
// Modify the original array only
```

---

## Constraints

```text
1 ≤ n ≤ 100000

-10^9 ≤ arr[i] ≤ 10^9
```

---

# 📖 2. Keyword Bank (English → Hindi)

| English Word       | Hindi / Simple Meaning                 |
| ------------------ | -------------------------------------- |
| In-place           | Usi array mein change karna            |
| Reverse            | Ulta karna                             |
| Swap               | Do values ki jagah badalna             |
| Left Pointer       | Left side wala index                   |
| Right Pointer      | Right side wala index                  |
| Temporary Variable | Value ko thodi der ke liye store karna |
| Array              | Elements ka collection                 |
| Index              | Position Number                        |

> 💡 **Tip:** Is question ka main point hai **extra array use nahi karna**.

---

# 🧠 3. Question Ko Apne Shabdon Mein (Paraphrase)

> Mujhe ek array ko ulta karna hai, lekin naya array nahi banana. Sirf original array ke andar hi elements ki position change karni hai.

✅ **Check:** Agar tum bol sako ki **"First aur Last ko swap karte jao"**, to question samajh aa gaya.

---

# 🛠️ 4. Approach / Method

## Technique ka naam

**Two Pointers + Swapping**

---

## Soch Hindi Mein

- Ek pointer beginning par rakho.
- Dusra pointer end par rakho.
- Dono values ko swap karo.
- Left pointer ko aage badhao.
- Right pointer ko peeche lao.
- Jab dono pointers mil jayein tab stop.

---

## Algorithm

```text
Start from first index

Start another pointer from last index

While left < right

    Swap both elements

    Move left forward

    Move right backward
```

---

## Visualization

```
Original

[1,2,3,4,5]

↓

Swap

5 2 3 4 1

↓

Swap

5 4 3 2 1

↓

Done
```

---

# ✍️ 5. Dry Run (Chhota Example)

### Input

```text
[10,20,30,40]
```

---

### Step 1

```
Left = 0

Right = 3

Swap

[40,20,30,10]
```

---

### Step 2

```
Left = 1

Right = 2

Swap

[40,30,20,10]
```

---

### Step 3

```
Left = 2

Right = 1

Stop
```

---

### Final Output

```text
[40,30,20,10]
```

---

# 💻 6. Actual Code / Answer

```javascript
function reverseArray(arr) {
  for (let i = 0; i < Math.floor(arr.length / 2); i++) {
    let temp = arr[i];

    arr[i] = arr[arr.length - 1 - i];

    arr[arr.length - 1 - i] = temp;
  }

  return arr;
}

module.exports = { reverseArray };
```

```javascript
function reverseArray(arr) {
  let left = 0;
  let right = arr.length - 1;

  while (left < right) {
    let temp = arr[left];
    arr[left] = arr[right];
    arr[right] = temp;

    left++;
    right--;
  }

  return arr;
}

module.exports = { reverseArray };
```

```javascript
function reverseArray(arr) {
  return arr.reverse();
}

module.exports = { reverseArray };
```

---

# 🧩 Code Explanation

### Loop Half Array Tak

```javascript
for (let i = 0; i < Math.floor(arr.length / 2); i++)
```

Sirf half array tak jaana padta hai.

Example

```
1 2 3 4 5

^

|

0

↓

1

↓

Stop
```

Dusra half automatically swap ho jata hai.

---

### Store Current Element

```javascript
let temp = arr[i];
```

Left side ki value temporary variable mein save karte hain.

---

### Move Last Element Forward

```javascript
arr[i] = arr[arr.length - 1 - i];
```

Right side ki value left side par aa jaati hai.

Example

```
1 2 3 4 5

↓

5 2 3 4 5
```

---

### Put Temp Value at End

```javascript
arr[arr.length - 1 - i] = temp;
```

Ab jo pehle left side par thi woh right side par chali jaati hai.

Result

```
5 2 3 4 1
```

---

# ⚠️ Common Mistakes

## ❌ Extra Array Banana

Wrong

```javascript
let newArray = [];
```

Question ne mana kiya hai.

Correct

```javascript
Swap inside original array.
```

---

## ❌ Pura Array Traverse Karna

Wrong

```javascript
for (let i = 0; i < arr.length; i++)
```

Isse elements dobara swap ho jayenge.

Correct

```javascript
i < Math.floor(arr.length / 2);
```

---

## ❌ Temp Variable Use Na Karna

Wrong

```javascript
arr[i] = arr[j];

arr[j] = arr[i];
```

Original value lose ho jaayegi.

Correct

```javascript
let temp = arr[i];

arr[i] = arr[j];

arr[j] = temp;
```

---

## ❌ Return New Array

Wrong

```javascript
return newArray;
```

Correct

```javascript
Modify original array only.
```

---

# ⏱️ 7. Complexity

### Time Complexity

```text
O(N)
```

Half array traverse hota hai.

---

### Space Complexity

```text
O(1)
```

Sirf ek temporary variable use hota hai.

---

# 🎯 Pattern Recognition

Is type ke questions dekhte hi socho:

```text
Need Reverse

↓

No Extra Space

↓

Use Two Pointers

↓

Swap Elements

↓

Done
```

---

# 🔄 Similar Problems

- Reverse Array
- Reverse String
- Reverse Linked List
- Swap First and Last
- Two Pointer Problems
- Palindrome Check

---

# 🧩 Master Formula

```text
Left Pointer

↓

Right Pointer

↓

Swap

↓

Move Both

↓

Repeat Until Meet
```

---

# 🔑 8. Yaad Rakhne Wali Baat (One-Liner)

> **Jab bhi reverse without extra space bola ho, hamesha Two Pointers aur Swapping technique use karo.**

---

# 📚 Cheat Sheet

```text
Left

0


Right

arr.length - 1


Swap

temp = arr[left]

arr[left] = arr[right]

arr[right] = temp


Move

left++

right--


Time

O(N)


Space

O(1)
```

---

# 🏷️ Topic Tag

`#Array`
`#ReverseArray`
`#TwoPointers`
`#Swapping`
`#InPlaceAlgorithm`
`#DSABasics`
`#LogicBuilding`
