# Right Triangle - Star Pattern

---

# 📌 1. Question (Jaisa Hai Waisa)

> **Write a program that takes an integer `n` as input and prints a right triangle star pattern with `n` rows.**
>
> * Each row should contain stars (`*`) with spaces between them.
> * The number of stars increases as you move from the first row to the `n`th row.

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

A single integer `n` representing the number of rows.

---

## Output Format

Print a right triangle star pattern.

> **JavaScript Note:** Use `process.stdout.write()` to print characters on the same line.

---

## Constraints

```text
1 ≤ n ≤ 100
```

---

# 📖 2. Keyword Bank (English → Hindi)

| English Word   | Hindi / Simple Meaning                    |
| -------------- | ----------------------------------------- |
| Pattern        | Kisi fixed design ya shape ko print karna |
| Right Triangle | Right side wala triangle shape            |
| Nested Loop    | Ek loop ke andar dusra loop               |
| Outer Loop     | Rows ko control karta hai                 |
| Inner Loop     | Har row ke columns ko control karta hai   |
| Row            | Ek horizontal line                        |
| Column         | Ek row ke andar ki position               |
| Character      | Ek symbol jaise `*`                       |
| Iteration      | Loop ka ek complete round                 |
| New Line       | Agli line mein jana (`\n`)                |

> 💡 **Yaad Rakho:** Pattern Programming mein **Outer Loop = Rows** aur **Inner Loop = Columns**.

---

# 🧠 3. Question Ko Apne Shabdon Mein (Paraphrase)

> Ye question mujhse keh raha hai ki `n` rows ka ek right triangle banana hai. Pehli row mein 1 star, doosri mein 2 stars, teesri mein 3 stars... aur isi tarah har row mein ek star badhta jayega.

✔️ Rule:

* Row Number = Star Count

Matlab

```
Row 1 → 1 Star

Row 2 → 2 Stars

Row 3 → 3 Stars

...

Row n → n Stars
```

---

# 🛠️ 4. Approach / Method

## Technique

**Nested Loops**

---

## Soch Hindi Mein

Har row mein jitna row number hoga utne hi stars print karne hain.

* Outer Loop rows ko control karega.
* Inner Loop stars print karega.
* Har star ke baad ek space print karenge.
* Row complete hone ke baad `\n` se next line mein chale jayenge.

---

## Algorithm

```
Repeat for every row

    Repeat row number times

        Print "* "

    Move to next line
```

---

# 🎯 Golden Rule

```
Outer Loop

↓

Rows

↓

Inner Loop

↓

Stars
```

Yahan

```
Stars = Row Number
```

---

# ✍️ 5. Dry Run

### Input

```text
4
```

---

### Row 1

```
i = 1

Inner Loop

j = 1

Print

*


Output

*
```

---

### Row 2

```
i = 2

Inner Loop

j = 1
j = 2

Print

* *
```

Output

```text
*
* *
```

---

### Row 3

```
i = 3

Inner Loop

j = 1
j = 2
j = 3

Print

* * *
```

Output

```text
*
* *
* * *
```

---

### Row 4

```
i = 4

Inner Loop

j = 1
j = 2
j = 3
j = 4

Print

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

## ✅ Using `process.stdout.write()` (Recommended)

```javascript
function printPattern(n) {

    for (let i = 1; i <= n; i++) {

        for (let j = 1; j <= i; j++) {
            process.stdout.write("* ");
        }

        process.stdout.write("\n");
    }

}

module.exports = { printPattern };
```

---

## ✅ Same Logic Using `console.log()`

```javascript
function printPattern(n) {

    for (let i = 1; i <= n; i++) {

        let row = "";

        for (let j = 1; j <= i; j++) {
            row += "* ";
        }

        console.log(row.trimEnd());
    }

}
```

---

# ⚠️ Common Mistakes

## ❌ Inner Loop ko `n` tak chalana

Wrong

```javascript
for (let j = 1; j <= n; j++)
```

Ye Square Pattern banayega.

---

Correct

```javascript
for (let j = 1; j <= i; j++)
```

Ye Right Triangle banayega.

---

## ❌ `\n` na lagana

Agar

```javascript
process.stdout.write("\n");
```

nahi likhoge to saare stars ek hi line mein print ho jayenge.

---

## ❌ Space na dena

Wrong

```javascript
process.stdout.write("*");
```

Output

```text
***
```

Correct

```javascript
process.stdout.write("* ");
```

Output

```text
* * *
```

---

# ⏱️ 7. Complexity

### Time Complexity

```
O(n²)
```

Kyunki

```
1 + 2 + 3 + ... + n
```

stars print hote hain.

---

### Space Complexity

```
O(1)
```

Kyunki extra memory use nahi ho rahi, sirf direct print kar rahe hain.

---

# 🔄 Similar Problems

* Left Triangle
* Inverted Triangle
* Right Triangle
* Pyramid
* Hollow Triangle
* Number Triangle
* Alphabet Triangle

---

# 🧩 Pattern Recognition

Har Triangle Pattern se pehle ye 4 questions pucho:

```
1. Total Rows Kitni Hai?

2. Har Row Mein Kitne Stars Hai?

3. Kya Print Karna Hai?

4. Inner Loop Kahan Tak Chalega?
```

Is question ke answers:

```
Rows = n

Stars = Row Number

Print = "* "

Inner Loop = j <= i
```

---

# 🔑 8. Yaad Rakhne Wali Baat (One-Liner)

> **Right Triangle Pattern mein jitna row number hota hai, utne hi stars print hote hain. Isliye Inner Loop hamesha `j <= i` tak chalta hai, aur `process.stdout.write("\n")` har row ke baad next line mein le jata hai.**

---

# 🏷️ Topic Tag

`#PatternProgramming`
`#NestedLoop`
`#ForLoop`
`#RightTriangle`
`#StarPattern`
`#LogicBuilding`
`#DSABasics`
