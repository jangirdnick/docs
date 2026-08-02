# Print a V-Shape Pattern

---

# 📌 1. Question

> **Write a program that takes a positive integer `N` (minimum value `3`) as input and prints a V-shaped star pattern with `N` rows.**
>
> * Har row ka **first aur last visible character** `*` hoga.
> * Stars dheere-dheere center ki taraf aayenge aur last row mein sirf ek star bachega.
> * JavaScript mein same line print karne ke liye `process.stdout.write()` ka use karna hai.

### Example

**Input**

```text
5
```

**Output**

```text
*       *
 *     *
  *   *
   * *
    *
```

---

## Input Format

Ek integer `N` diya jata hai jo total rows batata hai.

Example

```text
5
```

---

## Output Format

`N` rows ka V-shape pattern print karo.

JavaScript mein same line ke liye:

```javascript
process.stdout.write()
```

use karna hai.

---

## Constraints

```text
3 ≤ N ≤ 50
```

---

# 📖 2. Keyword Bank (English → Hindi)

| English Word   | Hindi / Simple Meaning       |
| -------------- | ---------------------------- |
| V Shape        | V jaisi shape                |
| Nested Loop    | Ek loop ke andar dusra loop  |
| Outer Loop     | Rows ko control karta hai    |
| Inner Loop     | Columns ko control karta hai |
| Left Diagonal  | Left wali tirchi line        |
| Right Diagonal | Right wali tirchi line       |
| Column         | Har row ke andar position    |
| Pattern        | Shape print karna            |
| Condition      | Kis jagah star print hoga    |

> 💡 **Tip:** Is pattern mein stars continuously print nahi hote. Sirf **2 fixed positions** par star print hota hai.

---

# 🧠 3. Question Ko Apne Shabdon Mein (Paraphrase)

> Ye question mujhse ek **V shape** print karne ko keh raha hai. Har row mein left aur right side par star hoga. Har next row mein dono stars ek dusre ke paas aate jayenge aur last row mein dono same position par mil jayenge.

☑️ **Check:** Agar tum bol sako ki "Stars dono side se center ki taraf aa rahe hain", to question samajh aa gaya.

---

# 🛠️ 4. Approach / Method

## Technique ka naam

**Nested Loops + Position Checking**

---

## Soch Hindi Mein

Is pattern mein:

* Outer Loop rows ko control karega.
* Inner Loop total columns ko control karega.
* Total columns hamesha:

```text
2 × N - 1
```

hongi.

Har row mein sirf do jagah star print hoga:

* Left Diagonal → `col === row`
* Right Diagonal → `col === (2 * N - row)`

Baaki sab jagah spaces print hongi.

---

## Algorithm

```text
Loop row from 1 to N

    Loop column from 1 to (2 × N - 1)

        If column equals left diagonal
            Print *

        Else if column equals right diagonal
            Print *

        Else
            Print space

    Move to next line
```

---

## Visualization

```
N = 5

Columns = 9

Row 1

*       *

Row 2

 *     *

Row 3

  *   *

Row 4

   * *

Row 5

    *
```

---

# ✍️ 5. Dry Run (Chhota Example)

### Input

```text
4
```

---

### Total Columns

```text
2 × 4 - 1 = 7
```

---

### Step 1

```
row = 1

Left Star  = col 1
Right Star = col 7

*     *
```

---

### Step 2

```
row = 2

Left Star = col 2
Right Star = col 6

 *   *
```

---

### Step 3

```
row = 3

Left Star = col 3
Right Star = col 5

  * *
```

---

### Step 4

```
row = 4

Left Star = col 4
Right Star = col 4

   *
```

---

### Final Output

```text
*     *
 *   *
  * *
   *
```

---

# 💻 6. Actual Code / Answer

```javascript
function printVShapePattern(n) {
    for (let row = 1; row <= n; row++) {

        for (let col = 1; col <= (2 * n - 1); col++) {

            if (col === row || col === (2 * n - row)) {
                process.stdout.write("*");
            } else {
                process.stdout.write(" ");
            }

        }

        process.stdout.write("\n");
    }
}

module.exports = { printVShapePattern };
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
for (let col = 1; col <= (2 * n - 1); col++)
```

Ye ek row ki saari positions ko check karta hai.

Total columns:

```text
2 × N - 1
```

---

### Left Diagonal

```javascript
col === row
```

Ye left side wala star print karta hai.

Example

```
Row 1 → Col 1

Row 2 → Col 2

Row 3 → Col 3
```

---

### Right Diagonal

```javascript
col === (2 * n - row)
```

Ye right side wala star print karta hai.

Example (N = 5)

```
Row 1 → Col 9

Row 2 → Col 8

Row 3 → Col 7

Row 4 → Col 6

Row 5 → Col 5
```

---

### Print Star

```javascript
process.stdout.write("*");
```

Sirf diagonal positions par star print hota hai.

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

Ek row complete hone ke baad next line mein chale jaate hain.

---

# ⚠️ Common Mistakes

## ❌ Total columns ko `n` rakh dena

Wrong

```javascript
for (let col = 1; col <= n; col++)
```

Correct

```javascript
for (let col = 1; col <= (2 * n - 1); col++)
```

---

## ❌ Sirf ek diagonal print karna

Wrong

```javascript
if (col === row)
```

Correct

```javascript
if (col === row || col === (2 * n - row))
```

---

## ❌ AND (`&&`) use karna

Wrong

```javascript
if (col === row && col === (2 * n - row))
```

Ye sirf last row mein star print karega.

Correct

```javascript
if (col === row || col === (2 * n - row))
```

---

## ❌ New line bhool jana

```javascript
process.stdout.write("\n");
```

Iske bina poora pattern ek hi line mein print ho jayega.

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

Koi extra array ya data structure use nahi ho raha.

---

# 🎯 Pattern Recognition

Is pattern ko dekhte hi ye socho:

```text
Rows

↓

Total Columns = 2 × N - 1

↓

Left Diagonal

+

Right Diagonal

↓

V Shape
```

---

# 🔄 Similar Problems

* X Pattern
* Hollow Diamond
* Butterfly Pattern
* Hollow Pyramid
* Mirrored Triangle
* Hollow V Pattern

---

# 🧩 Master Formula

```text
Rows

↓

Columns = (2 × N - 1)

↓

Left Star = Row

↓

Right Star = (2 × N - Row)

↓

Else Space
```

---

# 🔑 8. Yaad Rakhne Wali Baat (One-Liner)

> **V pattern mein hamesha do diagonals hoti hain — ek `col == row` aur doosri `col == (2 × N - row)`. Dono ko print karoge to perfect V ban jayega.**

---

# 📚 Cheat Sheet

```text
Outer Loop

row = 1 → N


Inner Loop

col = 1 → (2 × N - 1)


Left Star

col == row


Right Star

col == (2 × N - row)


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
`#VPattern`
`#StarPattern`
`#ForLoop`
`#BasicProgramming`
`#LogicBuilding`
`#DSABasics`
