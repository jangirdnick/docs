# Right Triangle - Number Pattern

---

# 📌 1. Question (Jaisa Hai Waisa)

> **Write a program that takes an integer `n` as input and prints a right triangle number pattern with `n` rows.**
>
> * Har row **1** se start hogi.
> * Row number jitni hogi, utne numbers print honge.
> * Numbers har row mein **1 se increment hote hue** print honge.
> * JavaScript mein same line mein print karne ke liye `process.stdout.write()` ka use karna hai.

### Example

Input

```text
5
```

Output

```text
1
1 2
1 2 3
1 2 3 4
1 2 3 4 5
```

---

## Input Format

Ek integer `n` diya jayega jo rows ko represent karta hai.

Example

```text
5
```

---

## Output Format

Right Triangle Number Pattern print karna hai.

JavaScript mein same line ke liye

```javascript
process.stdout.write()
```

ka use karna hai.

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
| Nested Loop    | Ek loop ke andar dusra loop               |
| Outer Loop     | Rows ko control karta hai                 |
| Inner Loop     | Columns ko control karta hai              |
| Row            | Horizontal line                           |
| Column         | Vertical position                         |
| Increment      | Value ko badhana                          |
| Number Pattern | Numbers se bana hua pattern               |

> 💡 **Yaad Rakho:** Pattern Programming mein pehle **Rows** samjho, phir **Columns**, phir decide karo ki har position par kya print hoga.

---

# 🧠 3. Question Ko Apne Shabdon Mein (Paraphrase)

> Ye question mujhse keh raha hai ki `n` rows ka ek right triangle banana hai. Har row mein numbers **1 se start** honge aur row number tak print honge.

Simple words mein:

* Row 1 → `1`
* Row 2 → `1 2`
* Row 3 → `1 2 3`
* Row 4 → `1 2 3 4`

Har nayi row mein ek number aur add hota jayega.

---

# 🛠️ 4. Approach / Method

## Technique

**Nested Loops**

---

## Soch Hindi Mein

Har row ke liye:

1. Outer Loop rows ko control karega.
2. Inner Loop `1` se current row (`i`) tak chalega.
3. Har iteration mein current number (`j`) print karenge.
4. Row complete hone ke baad next line (`\n`) print karenge.

---

## General Algorithm

```text
Repeat for every row

    Repeat from 1 to current row

        Print current number

    Move to next line
```

---

# 🎯 Golden Rule

```text
Outer Loop

↓

Rows

↓

Inner Loop

↓

Columns (Numbers)
```

Yaad Rakho:

```text
Outer Loop

↓

Kitni rows print hongi


Inner Loop

↓

Har row mein kitne numbers print honge
```

---

# 🔍 5. Dry Run

## Example

Input

```text
4
```

---

### Row 1 (`i = 1`)

Inner Loop

```text
j = 1
```

Print

```text
1
```

---

### Row 2 (`i = 2`)

Inner Loop

```text
j = 1 → 2
```

Print

```text
1 2
```

---

### Row 3 (`i = 3`)

Inner Loop

```text
j = 1 → 3
```

Print

```text
1 2 3
```

---

### Row 4 (`i = 4`)

Inner Loop

```text
j = 1 → 4
```

Print

```text
1 2 3 4
```

---

Final Output

```text
1
1 2
1 2 3
1 2 3 4
```

---

# 💻 6. Actual Code / Answer

```javascript
function printRightTriangleNumbers(n) {

    for (let i = 1; i <= n; i++) {

        for (let j = 1; j <= i; j++) {
            process.stdout.write(`${j} `);
        }

        process.stdout.write("\n");
    }

}

module.exports = { printRightTriangleNumbers };
```

---

## 🔄 Same Logic Using `console.log()`

```javascript
function printRightTriangleNumbers(n) {

    for (let i = 1; i <= n; i++) {

        let row = "";

        for (let j = 1; j <= i; j++) {
            row += j + " ";
        }

        console.log(row.trim());
    }

}
```

> 💡 **Difference:**
>
> * `process.stdout.write()` → Same line mein print karta hai, newline manually (`\n`) deni padti hai.
> * `console.log()` → Har call ke baad automatically next line mein chala jata hai.

---

# ⚠️ Common Mistakes

## ❌ `j <= n` likh dena

Wrong

```javascript
for (let j = 1; j <= n; j++)
```

Output

```text
1 2 3 4
1 2 3 4
1 2 3 4
1 2 3 4
```

Correct

```javascript
for (let j = 1; j <= i; j++)
```

---

## ❌ `i` print kar dena

Wrong

```javascript
process.stdout.write(`${i} `);
```

Output

```text
1
2 2
3 3 3
4 4 4 4
```

Correct

```javascript
process.stdout.write(`${j} `);
```

---

## ❌ New Line bhool jana

Wrong

```javascript
process.stdout.write(`${j} `);
```

Output

```text
1 1 2 1 2 3 1 2 3 4
```

Correct

```javascript
process.stdout.write("\n");
```

---

# ⏱️ 7. Complexity

### Time Complexity

```text
O(n²)
```

Kyunki

```text
Outer Loop

×

Inner Loop
```

dono execute hote hain.

---

### Space Complexity

Using `process.stdout.write()`

```text
O(1)
```

Using `console.log()` + `row` string

```text
O(n)
```

---

# 🎯 Pattern Recognition

Har Number Pattern solve karne se pehle ye 4 questions pucho:

```text
1. Total Rows Kitni Hai?

2. Har Row Mein Kitne Numbers Hai?

3. Number Kahan Se Start Ho Raha Hai?

4. Number Ka Formula Kya Hai?
```

---

# 🏗️ Master Formula

```text
Right Triangle Number Pattern

↓

Rows

↓

Columns

↓

Print j
```

Yaad Rakho:

```text
Rows

↓

Outer Loop


Numbers

↓

Inner Loop

↓

Print j
```

---

# 🔑 8. Yaad Rakhne Wali Baat (One-Liner)

> **Jab har row mein numbers 1 se current row tak print karne ho, tab Inner Loop hamesha `1` se `i` tak chalega aur `j` print hoga.**

---

# 📚 Cheat Sheet

```text
Outer Loop

↓

Rows


Inner Loop

↓

1 → i


Print

↓

j


New Line

↓

process.stdout.write("\n")


Time

↓

O(n²)


Space

↓

O(1)
```

---

# 🏷️ Topic Tag

`#PatternProgramming`
`#NestedLoop`
`#NumberPattern`
`#ForLoop`
`#BasicProgramming`
`#LogicBuilding`
`#RightTriangle`
`#DSABasics`
