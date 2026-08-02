# Print an X-Shape Pattern

---

# 📌 1. Question

> **Write a program that takes a positive odd integer `N` as input and prints an X-shaped star pattern with `N` rows.**
>
> * `N` hamesha **odd number** hoga.
> * Har row mein stars sirf **do diagonals** par print honge.
> * Jahan dono diagonals milti hain (center), wahan sirf **ek star** print hoga.
> * JavaScript mein same line print karne ke liye `process.stdout.write()` ka use karna hai.

### Example

**Input**

```text
5
```

**Output**

```text
*   *
 * *
  *
 * *
*   *
```

---

## Input Format

Ek positive **odd integer** `N` diya jata hai.

Example

```text
5
```

---

## Output Format

`N` rows ka **X-shaped pattern** print karo.

JavaScript mein same line ke liye:

```javascript
process.stdout.write()
```

use karna hai.

---

## Constraints

```text
1 ≤ N ≤ 51

N must be odd.
```

---

# 📖 2. Keyword Bank (English → Hindi)

| English Word       | Hindi / Simple Meaning       |
| ------------------ | ---------------------------- |
| X Shape            | X jaisi shape                |
| Diagonal           | Tirchi line                  |
| Main Diagonal      | Left se Right wali diagonal  |
| Secondary Diagonal | Right se Left wali diagonal  |
| Nested Loop        | Ek loop ke andar dusra loop  |
| Outer Loop         | Rows ko control karta hai    |
| Inner Loop         | Columns ko control karta hai |
| Pattern            | Shape print karna            |
| Position           | Kis jagah print karna        |
| Condition          | Star kab print hoga          |

> 💡 **Tip:** X Pattern mein sirf **2 diagonals** hoti hain. Baaki poori row spaces hoti hain.

---

# 🧠 3. Question Ko Apne Shabdon Mein (Paraphrase)

> Ye question mujhse ek **X shape** print karne ko keh raha hai. Har row aur column ko check karna hai. Agar current position **main diagonal** ya **secondary diagonal** par hai to `*` print karna hai, warna space print karni hai.

☑️ **Check:** Agar tum bol sako ki **"Dono diagonals ko print karna hai"**, to question samajh aa gaya.

---

# 🛠️ 4. Approach / Method

## Technique ka naam

**Nested Loops + Diagonal Position Checking**

---

## Soch Hindi Mein

Is pattern mein:

* Outer Loop rows ko control karega.
* Inner Loop columns ko control karega.
* Har row mein sirf **2 positions** par star print hoga.

### Main Diagonal

```text
row == col
```

### Secondary Diagonal

```text
row + col == N + 1
```

Agar dono conditions false hain to space print hogi.

---

## Algorithm

```text
Loop row from 1 to N

    Loop column from 1 to N

        If row equals column
            Print *

        Else if row + column equals N + 1
            Print *

        Else
            Print space

    Move to next line
```

---

## Visualization

```
N = 5

Row 1

*   *

Row 2

 * *

Row 3

  *

Row 4

 * *

Row 5

*   *
```

---

# ✍️ 5. Dry Run (Chhota Example)

### Input

```text
5
```

---

### Step 1

```
row = 1

Main Diagonal      -> col = 1
Secondary Diagonal -> col = 5

*   *
```

---

### Step 2

```
row = 2

Main Diagonal      -> col = 2
Secondary Diagonal -> col = 4

 * *
```

---

### Step 3

```
row = 3

Main Diagonal      -> col = 3
Secondary Diagonal -> col = 3

Dono same position par hain.

  *
```

---

### Step 4

```
row = 4

Main Diagonal      -> col = 4
Secondary Diagonal -> col = 2

 * *
```

---

### Step 5

```
row = 5

Main Diagonal      -> col = 5
Secondary Diagonal -> col = 1

*   *
```

---

### Final Output

```text
*   *
 * *
  *
 * *
*   *
```

---

# 💻 6. Actual Code / Answer

```javascript
function printXShapePattern(n) {
    for (let row = 1; row <= n; row++) {

        for (let col = 1; col <= n; col++) {

            if (col === row || (row + col === n + 1)) {
                process.stdout.write("*");
            } else {
                process.stdout.write(" ");
            }

        }

        process.stdout.write("\n");
    }
}

module.exports = { printXShapePattern };
```

---

# 🧩 Code Explanation

### Outer Loop

```javascript
for (let row = 1; row <= n; row++)
```

Ye har row ko print karta hai.

---

### Inner Loop

```javascript
for (let col = 1; col <= n; col++)
```

Ye har row ke andar har column ko check karta hai.

---

### Main Diagonal

```javascript
col === row
```

Ye left-top se right-bottom wali diagonal hai.

Example

```
Row 1 → Col 1

Row 2 → Col 2

Row 3 → Col 3
```

---

### Secondary Diagonal

```javascript
row + col === n + 1
```

Ye right-top se left-bottom wali diagonal hai.

Example (N = 5)

```
Row 1 → Col 5

Row 2 → Col 4

Row 3 → Col 3

Row 4 → Col 2

Row 5 → Col 1
```

---

### Print Star

```javascript
process.stdout.write("*");
```

Diagonal positions par star print hota hai.

---

### Print Space

```javascript
process.stdout.write(" ");
```

Baaki sab positions par space print hoti hai.

---

### Move to Next Line

```javascript
process.stdout.write("\n");
```

Har row complete hone ke baad next line mein chala jata hai.

---

# ⚠️ Common Mistakes

## ❌ Sirf ek diagonal print karna

Wrong

```javascript
if (col === row)
```

Correct

```javascript
if (col === row || row + col === n + 1)
```

---

## ❌ `&&` use kar dena

Wrong

```javascript
if (col === row && row + col === n + 1)
```

Ye sirf center star print karega.

Correct

```javascript
if (col === row || row + col === n + 1)
```

---

## ❌ `n` ki jagah `2 * n - 1` columns lena

Wrong

```javascript
for (let col = 1; col <= (2 * n - 1); col++)
```

Correct

```javascript
for (let col = 1; col <= n; col++)
```

X Pattern square grid mein banta hai.

---

## ❌ New line bhool jana

```javascript
process.stdout.write("\n");
```

Iske bina poora pattern ek hi line mein print hoga.

---

# ⏱️ 7. Complexity

### Time Complexity

```text
O(N²)
```

Har row ke liye saare columns check ho rahe hain.

---

### Space Complexity

```text
O(1)
```

Koi extra data structure use nahi ho raha.

---

# 🎯 Pattern Recognition

Is pattern ko dekhte hi ye socho:

```text
Rows

↓

Columns = N

↓

Main Diagonal

+

Secondary Diagonal

↓

X Shape
```

---

# 🔄 Similar Problems

* V Pattern
* Hollow X Pattern
* Hollow Diamond
* Butterfly Pattern
* Cross Pattern
* Plus Pattern

---

# 🧩 Master Formula

```text
Rows

↓

Columns = N

↓

Main Diagonal

col == row

↓

Secondary Diagonal

row + col == N + 1

↓

Else Space
```

---

# 🔑 8. Yaad Rakhne Wali Baat (One-Liner)

> **X Pattern mein hamesha do diagonals hoti hain — `col == row` aur `row + col == N + 1`. Dono ko print karoge to perfect X ban jayega.**

---

# 📚 Cheat Sheet

```text
Outer Loop

row = 1 → N


Inner Loop

col = 1 → N


Main Diagonal

col == row


Secondary Diagonal

row + col == N + 1


Print Star

process.stdout.write("*")


Print Space

process.stdout.write(" ")


Next Line

process.stdout.write("\n")


Time

O(N²)


Space

O(1)
```

---

# 🏷️ Topic Tag

`#PatternProgramming`
`#NestedLoop`
`#XPattern`
`#StarPattern`
`#ForLoop`
`#BasicProgramming`
`#LogicBuilding`
`#DSABasics`
