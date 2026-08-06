# Array Left Rotation by 1

---

# 📌 1. Question

> **Write a program that performs a left rotation by one position in an array.**
>
> - First element ko **last position** par bhejna hai.
> - Baaki saare elements **ek position left shift** honge.
> - Array ko **in-place modify** karna hai.
> - JavaScript mein **modified array return** karna hai.

### Example 1

**Input**

```text
5
1 2 3 4 5
```

**Output**

```text
2 3 4 5 1
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
8 7 6 9
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

Modified array return karo.

JavaScript mein:

```javascript
return arr;
```

---

## Constraints

```text
1 ≤ n ≤ 1000

-2^31 ≤ arr[i] ≤ 2^31
```

---

# 📖 2. Keyword Bank (English → Hindi)

| English Word       | Hindi / Simple Meaning                 |
| ------------------ | -------------------------------------- |
| Array              | Elements ka collection                 |
| Rotation           | Elements ko ghuma dena                 |
| Left Rotation      | Sabhi elements ko left shift karna     |
| Shift              | Ek position aage ya peeche le jana     |
| First Element      | Pehla element                          |
| Last Position      | Aakhri index                           |
| In-place           | Usi array ko modify karna              |
| Temporary Variable | Value ko thodi der ke liye store karna |

> 💡 **Tip:** Left rotation mein **pehla element last mein chala jata hai**, aur baaki sab ek step left aa jate hain.

---

# 🧠 3. Question Ko Apne Shabdon Mein (Paraphrase)

> Ek array diya gaya hai. Mujhe uske first element ko save karna hai, baaki sab elements ko ek position left shift karna hai aur saved element ko last position par rakhna hai.

✅ **Check:** Agar tum bol sako ki **"Pehla element last mein aur baaki sab ek step left"**, to question samajh aa gaya.

---

# 🛠️ 4. Approach / Method

## Technique ka naam

**Left Shift + Temporary Variable**

---

## Soch Hindi Mein

- Pehle first element ko save kar lo.
- Loop chalao aur har element ki jagah next element rakh do.
- Last position par saved first element rakh do.
- Modified array return kar do.

---

## Algorithm

```text
Store first element

Loop from index 0 to n-2

    arr[i] = arr[i + 1]

Place stored first element at last index

Return array
```

---

## Visualization

```
Original Array

[1, 2, 3, 4, 5]

↓

Save first element

1

↓

Shift Left

[2, 3, 4, 5, ?]

↓

Put saved element at last

[2, 3, 4, 5, 1]
```

---

# ✍️ 5. Dry Run (Chhota Example)

### Input

```text
[10, 20, 30, 40]
```

---

### Step 1

```
first = 10
```

---

### Step 2

```
Shift

20 → index 0

30 → index 1

40 → index 2

Array

[20,30,40,40]
```

---

### Step 3

```
Last index = first

[20,30,40,10]
```

---

### Final Output

```text
[20,30,40,10]
```

---

# 💻 6. Actual Code / Answer

```javascript
function leftRotateByOne(arr) {
  let first = arr[0];
  let right = arr.length - 1;

  for (let i = 0; i < arr.length - 1; i++) {
    arr[i] = arr[i + 1];
  }

  arr[right] = first;

  return arr;
}

module.exports = { leftRotateByOne };
```

```javascript
function leftRotateByOne(arr) {
  arr.push(arr.shift());
  return arr;
}

module.exports = { leftRotateByOne };
```

---

# 🧩 Code Explanation

### Store First Element

```javascript
let first = arr[0];
```

Pehla element save kar liya, kyunki shift ke baad ye overwrite ho jayega.

Example

```
[1,2,3,4,5]

first = 1
```

---

### Store Last Index

```javascript
let right = arr.length - 1;
```

Last index ko store kiya jahan first element ko baad mein rakhna hai.

Example

```
Length = 5

Last Index = 4
```

---

### Shift Elements Left

```javascript
for (let i = 0; i < arr.length - 1; i++) {
  arr[i] = arr[i + 1];
}
```

Har element ki jagah uske next element ko rakh diya.

Example

```
Before

[1,2,3,4,5]

↓

After Shift

[2,3,4,5,5]
```

Dhyan do ki last value temporary duplicate ho gayi hai, jise next step mein replace karenge.

---

### Place First Element at Last

```javascript
arr[right] = first;
```

Saved first element ko last position par rakh diya.

Example

```
[2,3,4,5,5]

↓

[2,3,4,5,1]
```

---

### Return Result

```javascript
return arr;
```

Modified array return ho jata hai.

---

# ⚠️ Common Mistakes

## ❌ First element save na karna

Wrong

```javascript
for (let i = 0; i < arr.length - 1; i++) {
  arr[i] = arr[i + 1];
}
```

First element hamesha ke liye lost ho jayega.

Correct

```javascript
let first = arr[0];
```

---

## ❌ Last element ko update na karna

Wrong

```javascript
return arr;
```

Output

```
[2,3,4,5,5]
```

Correct

```javascript
arr[right] = first;
```

---

## ❌ Loop ko last index tak chalana

Wrong

```javascript
for (let i = 0; i < arr.length; i++)
```

`arr[i + 1]` last iteration mein `undefined` ho jayega.

Correct

```javascript
for (let i = 0; i < arr.length - 1; i++)
```

---

## ❌ New array banana

Wrong

```javascript
let newArr = [];
```

Question specifically **in-place modification** maang raha hai.

Correct

```javascript
Modify original array directly.
```

---

# ⏱️ 7. Complexity

### Time Complexity

```text
O(N)
```

Har element sirf ek baar shift hota hai.

---

### Space Complexity

```text
O(1)
```

Sirf ek temporary variable (`first`) use hua hai.

---

# 🎯 Pattern Recognition

Is type ke questions dekhte hi socho:

```text
Save First Element

↓

Shift Left

↓

Put First at Last

↓

Return Array
```

---

# 🔄 Similar Problems

- Right Rotation by 1
- Left Rotation by K
- Rotate Array
- Reverse Array
- Cyclic Rotation
- Array Shifting

---

# 🧩 Master Formula

```text
Store First Element

↓

Shift Every Element Left

↓

Place First at Last

↓

Return Array
```

---

# 🔑 8. Yaad Rakhne Wali Baat (One-Liner)

> **Left Rotation by 1 mein pehla element save karo, baaki sabko ek step left shift karo aur saved element ko last index par rakh do.**

---

# 📚 Cheat Sheet

```text
Store

first = arr[0]


Loop

0 → n-2


Shift

arr[i] = arr[i+1]


Last

arr[n-1] = first


Return

arr


Time

O(N)


Space

O(1)
```

---

# 🏷️ Topic Tag

`#Array`
`#LeftRotation`
`#ArrayRotation`
`#InPlace`
`#ForLoop`
`#LogicBuilding`
`#DSABasics`
