# Move Zeros

---

# 📌 1. Question

> **Given an array containing only `0`s and `1`s, move all the zeros to the end of the array.**
>
> - Sabhi `0` ko array ke **end** mein le jana hai.
> - Sabhi `1` apne **relative order** mein rehne chahiye.
> - Is question mein **extra space use kar sakte ho**.
> - JavaScript mein **modified array return** karna hai.

### Example 1

**Input**

```text
5
0 1 0 1 1
```

**Output**

```text
1 1 1 0 0
```

---

### Example 2

**Input**

```text
6
1 0 1 0 1 0
```

**Output**

```text
1 1 1 0 0 0
```

---

## Input Format

- First line mein integer `n` diya hoga.
- Second line mein `n` space-separated integers honge.

Example

```text
5
0 1 0 1 1
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
0 ≤ n ≤ 10^5

Array mein sirf 0 aur 1 honge.
```

---

# 📖 2. Keyword Bank (English → Hindi)

| English Word | Hindi / Simple Meaning              |
| ------------ | ----------------------------------- |
| Zero         | 0 value                             |
| One          | 1 value                             |
| Move         | Jagah badalna                       |
| End          | Last position                       |
| Array        | Elements ka collection              |
| Splice       | Array se element remove karna       |
| Push         | Array ke end mein element add karna |
| Traverse     | Array ko loop se dekhna             |

> 💡 **Tip:** Har `0` ko remove karke last mein add karna hai.

---

# 🧠 3. Question Ko Apne Shabdon Mein (Paraphrase)

> Array mein jitne bhi `0` hain unhe last mein bhejna hai aur `1` ko aage rakhna hai.

✅ **Check:** Agar tum bol sako ki **"Zero end mein aur One pehle"**, to question samajh aa gaya.

---

# 🛠️ 4. Approach / Method

## Technique ka naam

**Reverse Traversal + Splice + Push**

---

## Soch Hindi Mein

- Array ko last index se first index tak traverse karo.
- Agar current element `0` ho:
  - `splice()` se usse remove karo.
  - `push(0)` se usko last mein add kar do.

- Loop complete hone ke baad array return kar do.

---

## Algorithm

```text
Loop from last index to first index

    If current element is 0

        Remove it using splice()

        Push 0 at the end

Return array
```

---

## Visualization

```
Original

[0,1,0,1,1]

↓

Remove first zero

[1,0,1,1]

↓

Push zero

[1,0,1,1,0]

↓

Remove second zero

[1,1,1,0]

↓

Push zero

[1,1,1,0,0]
```

---

# ✍️ 5. Dry Run (Chhota Example)

### Input

```text
[1,0,1,0]
```

---

### Step 1

```
i = 3

Found 0

Remove

[1,0,1]

Push

[1,0,1,0]
```

---

### Step 2

```
i = 1

Found 0

Remove

[1,1,0]

Push

[1,1,0,0]
```

---

### Final Output

```text
[1,1,0,0]
```

---

# 💻 6. Actual Code / Answer

```javascript
function moveZerosToEnd(arr) {
  for (let i = arr.length - 1; i >= 0; i--) {
    if (arr[i] === 0) {
      arr.splice(i, 1);
      arr.push(0);
    }
  }

  return arr;
}

module.exports = { moveZerosToEnd };
```

```javascript
function moveZerosToEnd(arr) {
  let index = 0;

  for (let i = 0; i < arr.length; i++) {
    if (arr[i] !== 0) {
      arr[index] = arr[i];
      index++;
    }
  }

  while (index < arr.length) {
    arr[index] = 0;
    index++;
  }

  return arr;
}

module.exports = { moveZerosToEnd };
```

```javascript
function moveZerosToEnd(arr) {
  const nonZeros = arr.filter((x) => x !== 0);
  return nonZeros.concat(Array(arr.length - nonZeros.length).fill(0));
}

module.exports = { moveZerosToEnd };
```

---

# 🧩 Code Explanation

### Traverse from Last

```javascript
for (let i = arr.length - 1; i >= 0; i--)
```

Last se start karte hain taaki `splice()` ke baad indexing issue na aaye.

Example

```
Indexes

0 1 2 3 4

Loop

4 ← 3 ← 2 ← 1 ← 0
```

---

### Check Zero

```javascript
if (arr[i] === 0)
```

Agar current element `0` hai tabhi operation karenge.

---

### Remove Zero

```javascript
arr.splice(i, 1);
```

Current zero ko array se remove kar dete hain.

Example

```
Before

[1,0,1]

↓

After splice

[1,1]
```

---

### Push Zero

```javascript
arr.push(0);
```

Removed zero ko last mein add kar dete hain.

Example

```
Before

[1,1]

↓

After push

[1,1,0]
```

---

### Return Result

```javascript
return arr;
```

Modified array return ho jata hai.

---

# ⚠️ Common Mistakes

## ❌ Forward loop chalana

Wrong

```javascript
for (let i = 0; i < arr.length; i++)
```

`splice()` ke baad elements shift ho jate hain aur kuch zero skip ho sakte hain.

Correct

```javascript
for (let i = arr.length - 1; i >= 0; i--)
```

---

## ❌ Zero remove karna lekin push na karna

Wrong

```javascript
arr.splice(i, 1);
```

Array ki length kam ho jayegi.

Correct

```javascript
arr.splice(i, 1);
arr.push(0);
```

---

## ❌ One ko bhi remove kar dena

Wrong

```javascript
if (arr[i] === 1)
```

Question sirf zero move karne ko bol raha hai.

Correct

```javascript
if (arr[i] === 0)
```

---

## ❌ Push pehle aur splice baad mein

Wrong

```javascript
arr.push(0);
arr.splice(i, 1);
```

Ye incorrect ordering create kar sakta hai.

Correct

```javascript
arr.splice(i, 1);
arr.push(0);
```

---

# ⏱️ 7. Complexity

### Time Complexity

```text
O(N²)
```

> ⚠️ `splice()` ek **O(N)** operation hai, aur ye loop ke andar chal raha hai. Isliye worst case mein complexity **O(N²)** ho jati hai.

---

### Space Complexity

```text
O(1)
```

Extra array use nahi hua.

---

# 🎯 Pattern Recognition

Is type ke questions dekhte hi socho:

```text
Traverse Backward

↓

Find Zero

↓

Remove Zero

↓

Push at End

↓

Return Array
```

---

# 🔄 Similar Problems

- Move Zeros to End (Two Pointers)
- Segregate 0s and 1s
- Stable Partition
- Remove Elements
- Left Rotation
- Right Rotation

---

# 🧩 Master Formula

```text
Loop Backward

↓

If Element is Zero

↓

Splice

↓

Push Zero

↓

Return Array
```

---

# 🔑 8. Yaad Rakhne Wali Baat (One-Liner)

> **Backward traverse karo, har `0` ko `splice()` se remove karo aur `push(0)` se last mein add kar do.**

---

# 📚 Cheat Sheet

```text
Loop

Last → First


Condition

arr[i] === 0


Remove

arr.splice(i,1)


Add

arr.push(0)


Return

arr


Time

O(N²)


Space

O(1)
```

---

# 🚀 Better Approach (Interview Recommended)

Tumhara solution **sahi hai**, lekin interview mein **`splice()` avoid** kiya jata hai kyunki uski complexity `O(N)` hoti hai.

Better approach hota hai **extra array** banana (kyunki question allow karta hai) ya **two pointers** use karna, jisse overall **O(N)** time complexity milti hai.

---

# 🏷️ Topic Tag

`#Array`
`#MoveZeros`
`#Splice`
`#ArrayTraversal`
`#LogicBuilding`
`#DSABasics`
`#JavaScript`
