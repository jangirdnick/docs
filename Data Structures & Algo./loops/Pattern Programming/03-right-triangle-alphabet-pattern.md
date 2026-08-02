# Right Triangle - Alphabet Pattern

---

# 📌 1. Question (Jaisa Hai Waisa)

> **Write a program that takes an integer `n` as input and prints a right triangle alphabet pattern with `n` rows.**
>
> * Har row **A** se start hogi.
> * Har next alphabet sequence mein increment hoga.
> * Row number jitni hogi, utne alphabets print honge.
> * JavaScript mein same line mein print karne ke liye `process.stdout.write()` ka use karna hai.

### Example

Input

```text
5
```

Output

```text
A
A B
A B C
A B C D
A B C D E
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

Right Triangle Alphabet Pattern print karna hai.

JavaScript mein same line ke liye

```javascript
process.stdout.write()
```

ka use karna hai.

---

## Constraints

```text
1 ≤ n ≤ 26
```

---

# 📖 2. Keyword Bank (English → Hindi)

| English Word | Hindi / Simple Meaning                          |
| ------------ | ----------------------------------------------- |
| Alphabet     | English ke letters (A-Z)                        |
| ASCII        | Characters ko represent karne wala numeric code |
| Character    | Ek letter ya symbol                             |
| Pattern      | Kisi fixed design ya shape ko print karna       |
| Nested Loop  | Ek loop ke andar dusra loop                     |
| Outer Loop   | Rows ko control karta hai                       |
| Inner Loop   | Columns ko control karta hai                    |
| Increment    | Agla letter ya value lena                       |

> 💡 **Yaad Rakho:** Alphabet Pattern bhi Number Pattern jaisa hi hota hai. Bas numbers ki jagah letters print hote hain.

---

# 🧠 3. Question Ko Apne Shabdon Mein (Paraphrase)

> Ye question mujhse keh raha hai ki `n` rows ka ek right triangle banana hai. Har row **A** se start hogi aur current row tak alphabets print honge.

Simple words mein:

* Row 1 → `A`
* Row 2 → `A B`
* Row 3 → `A B C`
* Row 4 → `A B C D`

Har nayi row mein ek alphabet aur add hota jayega.

---

# 🛠️ 4. Approach / Method

## Technique

**Nested Loops**

---

## Soch Hindi Mein

Har row ke liye:

1. Outer Loop rows ko control karega.
2. Inner Loop `1` se current row (`i`) tak chalega.
3. Har iteration mein alphabet array se letter print karenge.
4. Row complete hone ke baad next line (`\n`) print karenge.

---

## General Algorithm

```text
Repeat for every row

    Repeat from 1 to current row

        Print alphabet

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

Columns (Alphabets)
```

Yaad Rakho:

```text
Outer Loop

↓

Kitni rows print hongi


Inner Loop

↓

Har row mein kitne alphabets print honge
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
A
```

---

### Row 2 (`i = 2`)

Inner Loop

```text
j = 1 → 2
```

Print

```text
A B
```

---

### Row 3 (`i = 3`)

Inner Loop

```text
j = 1 → 3
```

Print

```text
A B C
```

---

### Row 4 (`i = 4`)

Inner Loop

```text
j = 1 → 4
```

Print

```text
A B C D
```

---

Final Output

```text
A
A B
A B C
A B C D
```

---

# 💻 6. Actual Code / Answer

## Solution Using Array

```javascript
function printRightTriangleAlphabets(n) {

    const arr = [
        "A", "B", "C", "D", "E", "F", "G",
        "H", "I", "J", "K", "L", "M",
        "N", "O", "P", "Q", "R", "S",
        "T", "U", "V", "W", "X", "Y", "Z"
    ];

    for (let i = 1; i <= n; i++) {

        for (let j = 1; j <= i; j++) {
            process.stdout.write(`${arr[j - 1]} `);
        }

        process.stdout.write("\n");
    }

}

module.exports = { printRightTriangleAlphabets };
```

---

## ⭐ Better Solution (Using ASCII)

JavaScript mein letters ko array mein store karne ki zarurat nahi hai. ASCII code se direct alphabet nikala ja sakta hai.

```javascript
function printRightTriangleAlphabets(n) {

    for (let i = 1; i <= n; i++) {

        for (let j = 0; j < i; j++) {
            process.stdout.write(String.fromCharCode(65 + j) + " ");
        }

        process.stdout.write("\n");
    }

}

module.exports = { printRightTriangleAlphabets };
```

**ASCII Values**

```text
A → 65
B → 66
C → 67
...
Z → 90
```

---

## 🔄 Same Logic Using `console.log()`

```javascript
function printRightTriangleAlphabets(n) {

    for (let i = 1; i <= n; i++) {

        let row = "";

        for (let j = 0; j < i; j++) {
            row += String.fromCharCode(65 + j) + " ";
        }

        console.log(row.trim());
    }

}
```

> 💡 **Difference**
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
A B C D
A B C D
A B C D
A B C D
```

Correct

```javascript
for (let j = 1; j <= i; j++)
```

---

## ❌ Wrong Index

Wrong

```javascript
arr[j]
```

Output

```text
B
B C
B C D
```

Correct

```javascript
arr[j - 1]
```

---

## ❌ New Line bhool jana

Wrong

```javascript
process.stdout.write(arr[j - 1]);
```

Output

```text
AA BABC ABCD
```

Correct

```javascript
process.stdout.write("\n");
```

---

## ❌ ASCII Value Galat Lena

Wrong

```javascript
String.fromCharCode(97 + j)
```

Output

```text
a
a b
a b c
```

Correct

```javascript
String.fromCharCode(65 + j)
```

Output

```text
A
A B
A B C
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

Using `process.stdout.write()` + ASCII

```text
O(1)
```

Using Alphabet Array

```text
O(1)
```

(26 letters fix hain, isliye constant space hai.)

Using `console.log()` + `row` string

```text
O(n)
```

---

# 🎯 Pattern Recognition

Har Alphabet Pattern solve karne se pehle ye 4 questions pucho:

```text
1. Total Rows Kitni Hai?

2. Har Row Mein Kitne Alphabets Hai?

3. Alphabet Kahan Se Start Ho Raha Hai?

4. Next Alphabet Ka Formula Kya Hai?
```

---

# 🏗️ Master Formula

```text
Right Triangle Alphabet Pattern

↓

Rows

↓

Columns

↓

Print Alphabet
```

Yaad Rakho:

```text
Rows

↓

Outer Loop


Alphabets

↓

Inner Loop


Array[j - 1]

ya

String.fromCharCode(65 + j)
```

---

# 🔑 8. Yaad Rakhne Wali Baat (One-Liner)

> **Jab har row mein A se current row tak alphabets print karne ho, tab Inner Loop `A` se start hoga aur har iteration mein next alphabet print karega. ASCII (`String.fromCharCode`) use karna array se bhi better approach hai.**

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

arr[j - 1]

OR

String.fromCharCode(65 + j)


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
`#AlphabetPattern`
`#ForLoop`
`#BasicProgramming`
`#LogicBuilding`
`#RightTriangle`
`#ASCII`
`#DSABasics`
