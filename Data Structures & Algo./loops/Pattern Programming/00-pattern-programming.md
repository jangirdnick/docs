# Pattern Programming (Nested Loop)

---

# 📌 1. Question (Jaisa Hai Waisa)

> **Pattern Programming** ek aisi programming technique hai jisme hum loops (especially Nested Loops) ka use karke stars (`*`), numbers, alphabets ya symbols ke different patterns print karte hain.

Is topic ka main goal **Nested Loop** ko samajhna aur uska practical use seekhna hai.

Examples:

```
*
**
***
****
*****
```

```
*****
****
***
**
*
```

```
    *
   ***
  *****
 *******
*********
```

```
1
12
123
1234
12345
```

---

## Input Format

Generally ek integer `n` diya jata hai jo rows represent karta hai.

Example

```
5
```

---

## Output Format

Question ke according required pattern print karna hota hai.

---

## Constraints

```
1 ≤ n ≤ 100
```

---

# 📖 2. Keyword Bank (English → Hindi)

| English Word | Hindi / Simple Meaning |
|--------------|------------------------|
| Pattern | Kisi fixed design ya shape ko print karna |
| Nested Loop | Ek loop ke andar dusra loop |
| Outer Loop | Rows ko control karta hai |
| Inner Loop | Columns ko control karta hai |
| Row | Horizontal line |
| Column | Vertical position |
| Iteration | Loop ka ek complete round |
| Space | Empty character |
| Character | Ek symbol jaise *, #, A |
| Increment | Value ko badhana |
| Decrement | Value ko kam karna |

> 💡 **Yaad Rakho:** Pattern Programming ka 90% game sirf **Rows** aur **Columns** ko samajhne ka hai.

---

# 🧠 3. Question Ko Apne Shabdon Mein (Paraphrase)

> Pattern Programming mein hume kisi shape ko print karna hota hai. Har row mein kitne stars, numbers ya spaces print honge, ye decide karne ke liye hum Nested Loops use karte hain.

Simple words mein:

- Outer Loop → Kitni rows print hongi.
- Inner Loop → Har row mein kya print hoga.

---

# 🛠️ 4. Approach / Method

## Technique

**Nested Loops**

---

## Soch Hindi Mein

Har pattern ko solve karne ke liye sabse pehle ye observe karo:

1. Total rows kitni hain?
2. Har row mein kitne columns print ho rahe hain?
3. Kya print ho raha hai?
   - Star (`*`)
   - Number
   - Alphabet
   - Space
4. Kya values badh rahi hain ya kam ho rahi hain?

---

## General Algorithm

```
Repeat for every row

    Repeat for every column

        Print required value

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

Columns
```

Yaad rakhna:

```
Outer Loop kabhi bhi Row control karta hai.

Inner Loop hamesha Column control karta hai.
```

---

# 🔍 5. Dry Run

## Example

Input

```
4
```

Pattern

```
*
**
***
****
```

---

### Outer Loop

```
i = 1
```

Inner Loop

```
Print *

Output

*
```

---

### Outer Loop

```
i = 2
```

Inner Loop

```
Print * *

Output

**
```

---

### Outer Loop

```
i = 3
```

Inner Loop

```
Print * * *

Output

***
```

---

### Outer Loop

```
i = 4
```

Inner Loop

```
Print * * * *

Output

****
```

---

Final Output

```
*
**
***
****
```

---

# 💻 6. Basic Nested Loop Template
```
💡 Tips:
 
console.log() har baar nayi line pe print karta hai.
Agar aapko same line mein print karna hai (jaise pattern banate waqt), toh process.stdout.write() use karo.
process.stdout.write() se aap stars, numbers ya symbols ko horizontal print kar sakte ho bina nayi line ke.
Pattern complete hone ke baad console.log() ya process.stdout.write("\n") se next line pe jaao.
```

```javascript
for (let i = 1; i <= n; i++) {

    for (let j = 1; j <= n; j++) {

        // Print Something

    }

}
```

---

## Left Triangle

```javascript
for (let i = 1; i <= n; i++) {

    let row = "";

    for (let j = 1; j <= i; j++) {
        row += "*";
    }

    console.log(row);
}
```

Output

```
*
**
***
****
*****
```

---

## Inverted Triangle

```javascript
for (let i = n; i >= 1; i--) {

    let row = "";

    for (let j = 1; j <= i; j++) {
        row += "*";
    }

    console.log(row);
}
```

Output

```
*****
****
***
**
*
```

---

## Square Pattern

```javascript
for (let i = 1; i <= n; i++) {

    let row = "";

    for (let j = 1; j <= n; j++) {
        row += "*";
    }

    console.log(row);
}
```

Output

```
*****
*****
*****
*****
*****
```

---

# ⚠️ Common Mistakes

## ❌ Row aur Column ko confuse karna

Wrong Soch

```
Outer Loop

↓

Columns
```

Correct

```
Outer Loop

↓

Rows
```

---

## ❌ Wrong Loop Condition

Wrong

```javascript
for (let j = 1; j <= n; j++)
```

Jab triangle banana ho.

Correct

```javascript
for (let j = 1; j <= i; j++)
```

---

## ❌ New Line na dena

Har row complete hone ke baad

```
console.log(row)
```

karna zaroori hai.

---

## ❌ Space Pattern ignore karna

Pyramid ya Diamond mein

```
Stars se pehle Spaces
```

print hote hain.

Maximum beginners isi mein mistake karte hain.

---

# ⏱️ 7. Complexity

## Time Complexity

General Pattern

```
O(n²)
```

Kyunki

```
Outer Loop

×

Inner Loop
```

dono run karte hain.

---

## Space Complexity

```
O(1)
```

Agar direct print kar rahe ho.

Ya

```
O(n)
```

Agar ek row string mein store kar rahe ho.

---

# 🎯 Interview Follow-up

Interviewer pooch sakta hai:

- Square Pattern
- Rectangle Pattern
- Left Triangle
- Right Triangle
- Pyramid
- Hollow Square
- Hollow Pyramid
- Diamond Pattern
- Pascal Triangle
- Floyd Triangle

---

# 🔄 Similar Problems

- Square Pattern
- Rectangle Pattern
- Triangle Pattern
- Inverted Triangle
- Pyramid Pattern
- Diamond Pattern
- Hollow Square
- Hollow Diamond
- Butterfly Pattern
- Number Triangle
- Alphabet Triangle

---

# 🧩 Pattern Recognition

Har Pattern Question Solve Karne Se Pehle Ye 5 Questions Pucho:

```
1. Total Rows Kitni Hai?

2. Har Row Mein Kitne Columns Hai?

3. Space Kitni Hai?

4. Kya Print Hona Hai?

5. Formula Kya Hai?
```

Agar ye 5 questions answer kar diye, to lagbhag har pattern solve ho jayega.

---

# 🏗️ Master Formula

```
Pattern Programming

↓

Rows

↓

Columns

↓

Spaces

↓

Characters
```

Yaad Rakho:

```
Pattern =

Rows

+

Columns

+

Spaces

+

Logic
```

---

# 🔑 8. Yaad Rakhne Wali Baat (One-Liner)

> **Pattern Programming ka pura game sirf Nested Loops ka hai—Outer Loop rows ko control karta hai, Inner Loop columns ko, aur pattern ki logic decide karti hai ki har position par kya print hoga.**

---

# 📚 Cheat Sheet

```
Outer Loop

↓

Rows

Inner Loop

↓

Columns


Square

j <= n


Triangle

j <= i


Reverse Triangle

j <= n-i+1


Time

O(n²)


Space

O(1)
```

---

# 🏷️ Topic Tag

`#PatternProgramming`
`#NestedLoop`
`#Loop`
`#ForLoop`
`#BasicProgramming`
`#LogicBuilding`
`#2DThinking`
`#DSABasics`