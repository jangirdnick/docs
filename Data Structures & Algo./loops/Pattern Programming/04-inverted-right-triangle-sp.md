# Inverted Right Triangle - Star Pattern

---

# 📌 1. Question

> **Write a program that takes an integer `n` as input and prints an inverted right triangle star pattern with `n` rows.**
>
> * First row mein `n` stars print honge.
> * Har next row mein previous row se **1 star kam** print hoga.
> * JavaScript mein same line print karne ke liye `process.stdout.write()` ka use karna hai.

### Example

**Input**

```text
5
```

**Output**

```text
* * * * *
* * * *
* * *
* *
*
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

`n` rows ka inverted right triangle print karo.

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

| English Word | Hindi / Simple Meaning               |
| ------------ | ------------------------------------ |
| Inverted     | Ulta                                 |
| Triangle     | Tribhuj (Triangle Shape)             |
| Nested Loop  | Ek loop ke andar dusra loop          |
| Outer Loop   | Rows ko control karta hai            |
| Inner Loop   | Columns (Stars) ko control karta hai |
| Decrement    | Value ko kam karna                   |
| Row          | Horizontal line                      |
| Column       | Har row ke andar position            |
| Pattern      | Kisi shape ko print karna            |

> 💡 **Tip:** Is pattern mein sirf ek difference hai — stars **badhne ki jagah kam hote jaate hain.**

---

# 🧠 3. Question Ko Apne Shabdon Mein (Paraphrase)

> Ye question mujhse keh raha hai ki ek ulta triangle banana hai. Pehli row mein sabse zyada stars honge aur har agli row mein ek star kam hota jayega jab tak last row mein sirf ek star na bach jaye.

☑️ **Check:** Agar tum kisi ko bol sako ki "Har row mein ek star kam print karna hai", to question samajh aa gaya.

---

# 🛠️ 4. Approach / Method

## Technique ka naam

**Nested Loops**

---

## Soch Hindi Mein

Is pattern mein:

* Outer Loop rows ko control karega.
* Lekin is baar Outer Loop **n se start hoga aur 1 tak aayega.**
* Inner Loop har row mein jitni current row ki value hai utne stars print karega.
* Har row complete hone ke baad next line (`\n`) print karenge.

---

## Algorithm

```text
Start row from n

Repeat until row becomes 1

    Print row number of stars

    Move to next line
```

---

## Visualization

```
n = 5

Row = 5 → ***** 
Row = 4 → ****
Row = 3 → ***
Row = 2 → **
Row = 1 → *
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
row = 4

col = 1 → *
col = 2 → *
col = 3 → *
col = 4 → *

Output

* * * *
```

---

### Step 2

```
row = 3

Print 3 Stars

Output

* * *
```

---

### Step 3

```
row = 2

Print 2 Stars

Output

* *
```

---

### Step 4

```
row = 1

Print 1 Star

Output

*
```

---

### Final Output

```text
* * * *
* * *
* *
*
```

---

# 💻 6. Actual Code / Answer

```javascript
function printPattern(n) {
    for (let row = n; row >= 1; row--) {

        for (let col = 1; col <= row; col++) {
            process.stdout.write("* ");
        }

        process.stdout.write("\n");
    }
}

module.exports = { printPattern };
```

---

## 🧩 Code Explanation

### Outer Loop

```javascript
for (let row = n; row >= 1; row--)
```

* `row = n` → First row mein maximum stars.
* `row--` → Har row ke baad ek star kam.

---

### Inner Loop

```javascript
for (let col = 1; col <= row; col++)
```

Current row jitni value hogi utne stars print honge.

Example:

```
row = 5

*****

row = 3

***
```

---

### Print Same Line

```javascript
process.stdout.write("* ");
```

Ye newline nahi deta, isliye stars ek hi line mein print hote rehte hain.

---

### Move to Next Line

```javascript
process.stdout.write("\n");
```

Har row complete hone ke baad next line mein chale jaate hain.

---

# ⚠️ Common Mistakes

## ❌ Outer Loop ko 1 se start karna

Wrong

```javascript
for (let row = 1; row <= n; row++)
```

Ye normal triangle bana dega.

Correct

```javascript
for (let row = n; row >= 1; row--)
```

---

## ❌ Inner Loop ki condition galat likhna

Wrong

```javascript
col <= n
```

Correct

```javascript
col <= row
```

Har row mein stars kam hone chahiye.

---

## ❌ New Line bhool jana

```javascript
process.stdout.write("\n");
```

Agar ye nahi likhoge to saare stars ek hi line mein print ho jayenge.

---

# ⏱️ 7. Complexity

### Time Complexity

```text
O(n²)
```

Kyuki Nested Loop chal raha hai.

---

### Space Complexity

```text
O(1)
```

Koi extra data structure use nahi ho raha.

---

# 🎯 Pattern Recognition

Is pattern ko dekhte hi ye socho:

```
Rows

↓

Stars decrease

↓

Outer Loop reverse

↓

Inner Loop prints stars
```

---

# 🔄 Similar Problems

* Inverted Number Triangle
* Inverted Alphabet Triangle
* Right Triangle
* Pyramid
* Hollow Triangle
* Diamond Pattern

---

# 🧩 Master Formula

```text
Rows

↓

Stars = Current Row

↓

Current Row--

↓

Pattern Complete
```

---

# 🔑 8. Yaad Rakhne Wali Baat (One-Liner)

> **Agar har next row mein stars kam ho rahe hain, to Outer Loop reverse (`n → 1`) chalega aur Inner Loop current row ke according stars print karega.**

---

# 📚 Cheat Sheet

```text
Outer Loop

row = n → 1


Inner Loop

col = 1 → row


Print

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
`#InvertedTriangle`
`#ForLoop`
`#BasicProgramming`
`#LogicBuilding`
`#DSABasics`
