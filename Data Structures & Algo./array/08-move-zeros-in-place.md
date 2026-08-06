# Move Zeros without Extra Space

---

# 📌 1. Question

> **Given an array containing only `0`s and `1`s, move all the `0`s to the end of the array without using any extra space.**
>
> - Original array ko **modify (in-place)** karna hai.
> - Koi **new array** use nahi karna.
> - Sabhi `1`s ka relative order same rehna chahiye.
> - JavaScript mein original array ko modify karna hai.

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
- Second line mein `n` space-separated integers (`0` aur `1`) honge.

Example

```text
5
0 1 0 1 1
```

---

## Output Format

Original array ko modify karo.

JavaScript mein:

```javascript
// Do not return anything
// Modify the original array
```

---

## Constraints

```text
1 ≤ n ≤ 10^5

Array contains only 0 and 1
```

---

# 📖 2. Keyword Bank (English → Hindi)

| English Word  | Hindi / Simple Meaning                     |
| ------------- | ------------------------------------------ |
| Move          | Ek jagah se doosri jagah le jana           |
| Zero          | 0                                          |
| One           | 1                                          |
| In-place      | Original array mein hi changes karna       |
| Swap          | Do values ki position badalna              |
| Pointer       | Kisi position ko track karne wala variable |
| Left Pointer  | Agla 1 rakhne ki position                  |
| Right Pointer | Array ko traverse karne wala pointer       |

> 💡 **Tip:** Yahan **new array banana allowed nahi hai**, isliye **Two Pointer + Swap** use karte hain.

---

# 🧠 3. Question Ko Apne Shabdon Mein (Paraphrase)

> Array mein jitne bhi `1` hain unhe starting mein lana hai aur saare `0` automatically end mein chale jane chahiye. Ye sab original array ke andar hi karna hai.

✅ **Check:** Agar tum bol sako ki **"Jab bhi 1 mile usko aage shift karna hai"**, to question samajh aa gaya.

---

# 🛠️ 4. Approach / Method

## Technique ka naam

**Two Pointer + Swap**

---

## Soch Hindi Mein

- `left` pointer batayega ki agla `1` kis index par rakhna hai.
- `right` pointer poore array ko traverse karega.
- Jab `right` ko `1` mile:
  - `left` aur `right` ki values swap karo.
  - `left` ko aage badha do.

- Loop khatam hote hi saare `1` starting mein aur `0` end mein aa jayenge.

---

## Algorithm

```text
left = 0

Loop right from 0 to n-1

    If current element is 1

        Swap arr[left] and arr[right]

        left++

End Loop
```

---

## Visualization

```
Original

[0,1,0,1,1]

left = 0

right = 1

↓

Swap

[1,0,0,1,1]

left = 1

↓

right = 3

Swap

[1,1,0,0,1]

left = 2

↓

right = 4

Swap

[1,1,1,0,0]
```

---

# ✍️ 5. Dry Run (Chhota Example)

### Input

```text
[0,1,0,1]
```

---

### Step 1

```
left = 0

right = 0

Current = 0

No Swap

[0,1,0,1]
```

---

### Step 2

```
right = 1

Current = 1

Swap index 0 and 1

[1,0,0,1]

left = 1
```

---

### Step 3

```
right = 2

Current = 0

No Swap

[1,0,0,1]
```

---

### Step 4

```
right = 3

Current = 1

Swap index 1 and 3

[1,1,0,0]

left = 2
```

---

### Final Output

```text
[1,1,0,0]
```

---

# 💻 6. Actual Code / Answer

```javascript
class Solution {
  moveZeros(arr) {
    let left = 0;

    for (let right = 0; right < arr.length; right++) {
      if (arr[right] !== 0) {
        [arr[left], arr[right]] = [arr[right], arr[left]];
        left++;
      }
    }
  }
}

module.exports = Solution;
```

```javascript
class Solution {
  moveZeros(arr) {
    let count = 0;

    for (let i = 0; i < arr.length; i++) {
      if (arr[i] !== 0) {
        arr[count++] = arr[i];
      }
    }

    while (count < arr.length) {
      arr[count++] = 0;
    }

    return arr;
  }
}

module.exports = Solution;
```

```javascript
class Solution {
  moveZeros(arr) {
    const result = arr.reduce((acc, num) => {
      if (num !== 0) acc.push(num);
      return acc;
    }, []);

    const zeros = Array(arr.length - result.length).fill(0);
    return result.concat(zeros);
  }
}

module.exports = Solution;
```

---

# 🧩 Code Explanation

### Left Pointer

```javascript
let left = 0;
```

Ye batata hai ki agla `1` kis index par rakhna hai.

---

### Traverse Array

```javascript
for (let right = 0; right < arr.length; right++)
```

`right` pointer har element ko check karega.

Example

```
Indexes

0 1 2 3 4

right

0 → 1 → 2 → 3 → 4
```

---

### Check Non-Zero

```javascript
if (arr[right] !== 0)
```

Agar current element `1` hai tabhi swap karenge.

---

### Swap

```javascript
[arr[left], arr[right]] = [arr[right], arr[left]];
```

Current `1` ko uski sahi position par le aate hain.

Example

```
Before

[0,1,0,1]

left = 0

right = 1

↓

After Swap

[1,0,0,1]
```

---

### Move Left Pointer

```javascript
left++;
```

Ab agla `1` next position par jayega.

---

# ⚠️ Common Mistakes

## ❌ Extra Array Banana

Wrong

```javascript
let ans = [];
```

Question extra space allow nahi karta.

Correct

```javascript
Swap inside original array
```

---

## ❌ Left Pointer Ko Increment Na Karna

Wrong

```javascript
if(arr[right] !== 0){
    swap...
}
```

Correct

```javascript
left++;
```

---

## ❌ Har Element Ko Swap Karna

Wrong

```javascript
Swap every element
```

Sirf `1` milne par swap karna hai.

---

## ❌ New Array Return Karna

Wrong

```javascript
return newArray;
```

Correct

```javascript
Modify original array
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
O(1)
```

Koi extra array use nahi hua.

---

# 🎯 Pattern Recognition

Is type ke questions dekhte hi socho:

```text
Given Array

↓

Move Non-Zero Elements Forward

↓

Swap Using Two Pointers

↓

Zeros Automatically End Mein
```

---

# 🔄 Similar Problems

- Move Zeros
- Segregate 0s and 1s
- Partition Array
- Remove Elements
- Stable Rearrangement
- Two Pointer Problems

---

# 🧩 Master Formula

```text
left = 0

↓

Traverse using right

↓

If current is non-zero

↓

Swap(left, right)

↓

left++
```

---

# 🔑 8. Yaad Rakhne Wali Baat (One-Liner)

> **Jab bhi `1` mile usko `left` pointer wali position par swap karo aur `left` ko aage badha do. Isse saare `0` automatically end mein chale jayenge.**

---

# 📚 Cheat Sheet

```text
Left Pointer

left = 0


Loop

right = 0 → n-1


If

arr[right] != 0


Swap

arr[left] ↔ arr[right]


Move

left++


Time

O(N)


Space

O(1)
```

---

# 🏷️ Topic Tag

`#Array`
`#MoveZeros`
`#TwoPointers`
`#Swap`
`#InPlace`
`#DSABasics`
`#LogicBuilding`
