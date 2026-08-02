# Mirrored Right Triangle - Star Pattern

---

# 📌 1. Question

> **Write a program that takes an integer `n` as input and prints a mirrored right triangle star pattern with `n` rows.**
>
> * Pattern **right-aligned** hona chahiye.
> * Left side mein spaces aur right side mein stars print honge.
> * Har next row mein **1 star increase** hoga.
> * JavaScript mein same line print karne ke liye `process.stdout.write()` ka use karna hai.

### Example

**Input**

```text
5
```

**Output**

```text
        *
      * *
    * * *
  * * * *
* * * * *
```

---

## Input Format

Ek integer `n` diya jata hai jo total rows batata hai.

Example

```text
5
```

---

## Output Format

`n` rows ka mirrored right triangle print karo.

JavaScript mein same line ke liye:

```javascript
process.stdout.write()
```

use karna hai.

---

## Constraints

```text
1 ≤ n ≤ 100
```

---

# 📖 2. Keyword Bank (English → Hindi)

| English Word   | Hindi / Simple Meaning          |
| -------------- | ------------------------------- |
| Mirrored       | Aaine jaisa / Right Align       |
| Right Triangle | Seedha Tribhuj                  |
| Nested Loop    | Ek loop ke andar dusra loop     |
| Outer Loop     | Rows ko control karta hai       |
| Inner Loop     | Spaces ya Stars print karta hai |
| Right Aligned  | Right side se start hona        |
| Space          | Khali jagah                     |
| Row            | Horizontal line                 |
| Column         | Har row ke andar position       |
| Pattern        | Shape print karna               |

> 💡 **Tip:** Is pattern mein sirf stars print karna kaafi nahi hai. **Pehle spaces aur phir stars** print karne padte hain.

---

# 🧠 3. Question Ko Apne Shabdon Mein (Paraphrase)

> Ye question mujhse ek aisa triangle print karwana chahta hai jo right side se start ho. Isliye har row mein pehle kuch spaces print hongi aur uske baad stars print honge. Jaise-jaise rows badhti hain, spaces kam aur stars zyada hote jaate hain.

☑️ **Check:** Agar tum bol sako **"Pehle spaces print karni hain, phir stars"**, to question samajh aa gaya.

---

# 🛠️ 4. Approach / Method

## Technique ka naam

**Nested Loops**

---

## Soch Hindi Mein

Is pattern mein **2 Inner Loops** lagenge.

* Outer Loop → Rows control karega.
* Pehla Inner Loop → Spaces print karega.
* Dusra Inner Loop → Stars print karega.
* Har row ke baad next line print karenge.

---

## Algorithm

```text
Repeat row from 1 to n

    Print (n-row) spaces

    Print row stars

    Move to next line
```

---

## Visualization

```
n = 5

Row 1

Spaces = 4
Stars  = 1

        *

----------------

Row 2

Spaces = 3
Stars  = 2

      * *

----------------

Row 3

Spaces = 2
Stars  = 3

    * * *

----------------

Row 4

Spaces = 1
Stars  = 4

  * * * *

----------------

Row 5

Spaces = 0
Stars  = 5

* * * * *
```

---

# ✍️ 5. Dry Run (Chhota Example)

### Input

```text
4
```

---

### Step 1

```
row = 1

Spaces = 3

Stars = 1

      *
```

---

### Step 2

```
row = 2

Spaces = 2

Stars = 2

    * *
```

---

### Step 3

```
row = 3

Spaces = 1

Stars = 3

  * * *
```

---

### Step 4

```
row = 4

Spaces = 0

Stars = 4

* * * *
```

---

### Final Output

```text
      *
    * *
  * * *
* * * *
```

---

# 💻 6. Actual Code / Answer

```javascript
function printMirroredRightTriangle(n) {
    for (let row = 1; row <= n; row++) {

        for (let colSp = 1; colSp <= n - row; colSp++) {
            process.stdout.write("  ");
        }

        for (let col = 1; col <= row; col++) {
            process.stdout.write("* ");
        }

        process.stdout.write("\n");
    }
}

module.exports = { printMirroredRightTriangle };
```

---

# 🧩 Code Explanation

### Outer Loop

```javascript
for (let row = 1; row <= n; row++)
```

Rows ko control karta hai.

Har iteration ek nayi row print karta hai.

---

### Space Loop

```javascript
for (let colSp = 1; colSp <= n - row; colSp++)
```

Har row mein left side ki spaces print karta hai.

Example

```
n = 5

row = 1

Spaces = 4

row = 3

Spaces = 2

row = 5

Spaces = 0
```

---

### Star Loop

```javascript
for (let col = 1; col <= row; col++)
```

Current row jitne stars print karta hai.

Example

```
row = 1

*

row = 3

* * *

row = 5

* * * * *
```

---

### Same Line Print

```javascript
process.stdout.write("* ");
```

Star ko same line mein print karta hai.

---

### Next Line

```javascript
process.stdout.write("\n");
```

Row complete hone ke baad next line mein chala jata hai.

---

# ⚠️ Common Mistakes

## ❌ Spaces print na karna

Wrong

```javascript
for (let col = 1; col <= row; col++)
```

Sirf normal triangle ban jayega.

Correct

```javascript
Spaces

↓

Stars
```

---

## ❌ Space Formula galat likhna

Wrong

```javascript
row - n
```

Correct

```javascript
n - row
```

---

## ❌ Space aur Star Loop ka order badal dena

Wrong

```text
Stars

↓

Spaces
```

Correct

```text
Spaces

↓

Stars
```

---

## ❌ New Line bhool jana

```javascript
process.stdout.write("\n");
```

Nahi likhoge to pura pattern ek hi line mein print ho jayega.

---

# ⏱️ 7. Complexity

### Time Complexity

```text
O(n²)
```

Kyuki har row mein spaces aur stars print ho rahe hain.

---

### Space Complexity

```text
O(1)
```

Koi extra data structure use nahi hua.

---

# 🎯 Pattern Recognition

Is pattern ko dekhte hi ye socho:

```
Rows

↓

Spaces decrease

↓

Stars increase

↓

Spaces First

↓

Stars Second
```

---

# 🔄 Similar Problems

* Right Triangle Star Pattern
* Inverted Right Triangle
* Number Triangle
* Alphabet Triangle
* Full Pyramid
* Hollow Pyramid
* Diamond Pattern

---

# 🧩 Master Formula

```text
Rows

↓

Spaces = n-row

↓

Stars = row

↓

Pattern Complete
```

---

# 🔑 8. Yaad Rakhne Wali Baat (One-Liner)

> **Jab bhi pattern right side se start ho, pehle spaces print karo aur phir current row ke according stars print karo.**

---

# 📚 Cheat Sheet

```text
Outer Loop

row = 1 → n


Space Loop

1 → n-row


Star Loop

1 → row


Print Space

process.stdout.write("  ")


Print Star

process.stdout.write("* ")


Next Line

process.stdout.write("\n")


Time

O(n²)


Space

O(1)
```

---

# 🏷️ Topic Tag

`#PatternProgramming`
`#NestedLoop`
`#StarPattern`
`#MirroredTriangle`
`#RightAlignedPattern`
`#ForLoop`
`#BasicProgramming`
`#LogicBuilding`
`#DSABasics`
