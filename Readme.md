# Tag 10 Array Funktionen und Methoden

### **📚 Unterrichtseinheit: Array-Methoden und -Funktionen**  

#### **🛠 Lernziele:**  
✔️ Kennenlernen der wichtigsten Array-Methoden und -Funktionen in JavaScript.  
✔️ Verstehen, wie man durch Arrays iteriert, um Daten zu lesen und zu verändern.  
✔️ Einführung in mehrdimensionale Arrays und deren Anwendungsfälle.  

---

## **🔹 Wichtige Array-Methoden und -Funktionen**  

### **1️⃣ Mutierende Methoden (Verändern das Original-Array)**  

📌 `.push()` → Fügt Elemente **am Ende** eines Arrays hinzu.  
📌 `.pop()` → Entfernt das **letzte Element** aus einem Array.  
📌 `.shift()` → Entfernt das **erste Element** eines Arrays.  
📌 `.unshift()` → Fügt Elemente **am Anfang** eines Arrays hinzu.  

**🔹 Beispiel:**

```js
let fruits = ["Apfel", "Banane"];
fruits.push("Orange"); 
console.log(fruits); // ["Apfel", "Banane", "Orange"]

fruits.pop(); 
console.log(fruits); // ["Apfel", "Banane"]

fruits.unshift("Erdbeere");
console.log(fruits); // ["Erdbeere", "Apfel", "Banane"]

fruits.shift();
console.log(fruits); // ["Apfel", "Banane"]
```

**📝 Übung 1:**  
Erstelle ein Array mit mindestens 3 Städten und füge eine neue Stadt mit `.push()` hinzu.  

**🔍 Lösung:** 
 
```js
let cities = ["Berlin", "Hamburg", "München"];
cities.push("Köln");
console.log(cities);
```

---

### **2️⃣ Methoden zur Manipulation von Arrays (Kopieren, Entfernen, Kombinieren)**  

📌 `.slice(start, end)` → Erstellt eine Kopie eines **Ausschnitts** aus dem Array.  
📌 `.splice(start, deleteCount, item1, item2, …)` → Fügt oder entfernt Elemente an einer bestimmten Position.  
📌 `.concat()` → Verbindet zwei Arrays zu einem neuen Array.  
📌 `.indexOf()` → Gibt den Index eines Elements zurück (oder `-1`, wenn nicht gefunden).  

**🔹 Beispiel:**

```js
let numbers = [10, 20, 30, 40, 50];

let sliced = numbers.slice(1, 4); 
console.log(sliced); // [20, 30, 40]

numbers.splice(2, 1, 99); 
console.log(numbers); // [10, 20, 99, 40, 50]

let moreNumbers = numbers.concat([60, 70]); 
console.log(moreNumbers); // [10, 20, 99, 40, 50, 60, 70]

console.log(numbers.indexOf(40)); // 3
```

**📝 Übung 2:**  

- Entferne das zweite Element aus einem Array und ersetze es durch eine neue Zahl mit `.splice()`.  
- Verbinde zwei Arrays mit `.concat()`.  

**🔍 Lösung:**  

```js
let zahlen = [5, 10, 15, 20];
zahlen.splice(1, 1, 99);
console.log(zahlen); // [5, 99, 15, 20]

let a = [1, 2, 3];
let b = [4, 5, 6];
let c = a.concat(b);
console.log(c); // [1, 2, 3, 4, 5, 6]
```

---

## **🔹 Iteration durch Arrays**  

### **1️⃣ Iteration mit Schleifen**  

📌 **For-Schleife**  

```js
let arr = [10, 20, 30];
for (let i = 0; i < arr.length; i++) {
  console.log(arr[i]);
}
```

📌 **For…of-Schleife**  

```js
for (let num of arr) {
  console.log(num);
}
```

**📝 Übung 3:**  

Gib alle Elemente eines Arrays mit einer `for`-Schleife und einer `for…of`-Schleife aus.  

**🔍 Lösung:**  

```js
let namen = ["Anna", "Ben", "Clara"];
for (let i = 0; i < namen.length; i++) {
  console.log(namen[i]);
}

for (let name of namen) {
  console.log(name);
}
```

---

### **2️⃣ Iteration mit Array-Methoden**  

📌 **`.forEach()`** → Führt eine Funktion für jedes Element aus.  
📌 **`.map()`** → Erstellt ein **neues** Array mit modifizierten Werten.  
📌 **`.filter()`** → Erstellt ein **neues** Array mit gefilterten Elementen.  
📌 **`.reduce()`** → Reduziert das Array auf einen einzigen Wert.  

**🔹 Beispiel:**

```js
let numbers = [1, 2, 3, 4, 5];

numbers.forEach(num => console.log(num * 2)); // 2, 4, 6, 8, 10

let doubled = numbers.map(num => num * 2);
console.log(doubled); // [2, 4, 6, 8, 10]

let evenNumbers = numbers.filter(num => num % 2 === 0);
console.log(evenNumbers); // [2, 4]

let sum = numbers.reduce((acc, num) => acc + num, 0);
console.log(sum); // 15
```

**📝 Übung 4:**
  
- Nutze `.map()`, um jedes Element eines Arrays um 10 zu erhöhen.  
- Nutze `.filter()`, um nur gerade Zahlen zu behalten.  
- Nutze `.reduce()`, um die Summe aller Werte zu berechnen.  

**🔍 Lösung:** 
 
```js
let zahlen = [5, 10, 15, 20];

let plusZehn = zahlen.map(num => num + 10);
console.log(plusZehn); // [15, 20, 25, 30]

let gerade = zahlen.filter(num => num % 2 === 0);
console.log(gerade); // [10, 20]

let summe = zahlen.reduce((acc, num) => acc + num, 0);
console.log(summe); // 50
```

--- 

### **Was ist `reduce()`?**  

Die Methode `.reduce()` ist eine Möglichkeit, alle Werte eines Arrays auf **einen einzigen Wert** zu reduzieren. Das kann eine Summe, ein Produkt, ein Objekt oder sogar ein neuer Array sein.

### **Wie funktioniert es?**  

`reduce()` geht über jedes Element im Array und führt eine Funktion aus, die zwei Werte kombiniert:  
1. **Den aktuellen "Zwischenwert"** (was bisher berechnet wurde).  
2. **Das aktuelle Element** aus dem Array.  

Am Ende bleibt ein einziger Wert übrig.

### **Grundstruktur**

```js
array.reduce((akkumulator, aktuellesElement) => { 
  // Berechnung 
  return neuerWert;
}, startwert);
```

- `akkumulator`: Das Zwischenergebnis (wird in jeder Iteration aktualisiert).  
- `aktuellesElement`: Das aktuelle Element aus dem Array.  
- `startwert`: Der Anfangswert für den Akkumulator.

---

### **Beispiel 1: Summe berechnen**  

Angenommen, du hast eine Liste von Zahlen und möchtest ihre Summe berechnen:

```js
const zahlen = [2, 3, 5, 7];

const summe = zahlen.reduce((akk, zahl) => akk + zahl, 0);

console.log(summe); // 17
```

🔹 Ablauf:  
1. Startwert ist `0`.  
2. Erste Iteration: `0 + 2 = 2`.  
3. Zweite Iteration: `2 + 3 = 5`.  
4. Dritte Iteration: `5 + 5 = 10`.  
5. Vierte Iteration: `10 + 7 = 17`.  
➡ Ergebnis: `17`.

---

### **Beispiel 2: Wörter zu einem Satz verbinden**

```js
const wörter = ["Ich", "lerne", "JavaScript"];

const satz = wörter.reduce((akk, wort) => akk + " " + wort, "");

console.log(satz); // "Ich lerne JavaScript"
```

Hier startet der Akkumulator als `""` (leerer String) und fügt jedes Wort hinzu.

---

### **Beispiel 3: Array in ein Objekt umwandeln**

Du hast eine Liste von Personen und möchtest daraus ein Objekt erstellen, das Namen den IDs zuordnet:

```js
const personen = [
  { id: 1, name: "Anna" },
  { id: 2, name: "Ben" },
  { id: 3, name: "Clara" }
];

const personenObjekt = personen.reduce((akk, person) => {
  akk[person.id] = person.name;
  return akk;
}, {});

console.log(personenObjekt);
// { 1: "Anna", 2: "Ben", 3: "Clara" }
```

---

### **Wann sollte man `reduce()` verwenden?**

- Wenn du eine Liste von Werten zu einem einzigen Wert verarbeiten willst.  
- Wenn du eine Summe, ein Produkt oder eine andere Berechnung über alle Elemente brauchst.  
- Wenn du Daten umstrukturieren möchtest (z. B. ein Array in ein Objekt umwandeln).

`reduce()` kann komplex wirken, aber wenn du verstehst, dass es einfach eine Funktion ist, die durch ein Array iteriert und einen Wert "zusammenbaut", wird es logisch!

## **🔹  Mehrdimensionale Arrays**  

### **1️⃣ Einführung in mehrdimensionale Arrays**  

📌 Ein Array kann **andere Arrays enthalten**, um eine **Matrix-Struktur** zu bilden.  
📌 Jedes Element ist **ein weiteres Array**, auf das mit `array[row][column]` zugegriffen wird.  

**🔹 Beispiel einer 3×3-Matrix:**  

```js
let matrix = [
  [1, 2, 3],
  [4, 5, 6],
  [7, 8, 9]
];

console.log(matrix[0][1]); // 2 (erste Zeile, zweite Spalte)
console.log(matrix[2][2]); // 9 (dritte Zeile, dritte Spalte)
```

**📝 Übung 5:**  

- Erstelle ein 2×3-Array mit beliebigen Zahlen.  
- Greife auf das erste und letzte Element zu.  

**🔍 Lösung:**  

```js
let zahlenMatrix = [
  [10, 20, 30],
  [40, 50, 60]
];

console.log(zahlenMatrix[0][0]); // 10
console.log(zahlenMatrix[1][2]); // 60
```

---

### **2️⃣ Iteration durch mehrdimensionale Arrays**  

📌 Verschachtelte Schleifen werden benötigt, um **jede Zeile und Spalte zu durchlaufen**.  

```js
for (let i = 0; i < matrix.length; i++) {
  for (let j = 0; j < matrix[i].length; j++) {
    console.log(matrix[i][j]);
  }
}
```

**📝 Übung 6:**  

Schreibe eine Schleife, die eine Matrix Zeile für Zeile ausgibt.  

**🔍 Lösung:**  
```js
let arr = [
  [1, 2],
  [3, 4]
];

for (let row of arr) {
  console.log(row);
}
```

---
Hier sind die ergänzten Übungen für jede Array-Methode, sodass jede Methode nun drei kleine Aufgaben enthält.  

---

## Zusaätzliche Übungen

## **1️⃣ Mutierende Methoden (Verändern das Original-Array)**  

### **📌 `.push()` – Element(e) am Ende hinzufügen**  

```js
let fruits = ["Apfel", "Banane"];
fruits.push("Orange"); 
console.log(fruits); // ["Apfel", "Banane", "Orange"]
```

### **📝 Übungen:**  

1. Füge `"Kiwi"` zu einem Obst-Array hinzu.  
2. Füge `"Mango"` und `"Ananas"` auf einmal zu einem Array hinzu.  
3. Prüfe, wie viele Elemente nach dem `.push()` im Array sind.  

**🔍 Lösungen:**  

```js
let fruits = ["Apfel", "Banane"];
fruits.push("Kiwi");
console.log(fruits); // ["Apfel", "Banane", "Kiwi"]

fruits.push("Mango", "Ananas");
console.log(fruits); // ["Apfel", "Banane", "Kiwi", "Mango", "Ananas"]

console.log(fruits.length); // 5
```

---

## **2️⃣ Methoden zur Manipulation von Arrays (Kopieren, Entfernen, Kombinieren)**  

### **📌 `.slice()` – Einen Teil des Arrays extrahieren**  

```js
let numbers = [10, 20, 30, 40, 50];
let sliced = numbers.slice(1, 4); 
console.log(sliced); // [20, 30, 40]
```

### **📝 Übungen:**  

1. Extrahiere die ersten drei Elemente aus einem Array.  
2. Schneide ein Array ab dem zweiten Element bis zum Ende ab.  
3. Speichere ein neues Array mit den letzten beiden Elementen.  

**🔍 Lösungen:**  

```js
let arr = [5, 10, 15, 20, 25];

let firstThree = arr.slice(0, 3);
console.log(firstThree); // [5, 10, 15]

let fromSecond = arr.slice(1);
console.log(fromSecond); // [10, 15, 20, 25]

let lastTwo = arr.slice(-2);
console.log(lastTwo); // [20, 25]
```

---

## **🔹  Iteration durch Arrays**  

### **📌 `.forEach()` – Jedes Element einzeln verarbeiten**  

```js
let numbers = [1, 2, 3, 4, 5];
numbers.forEach(num => console.log(num * 2)); // 2, 4, 6, 8, 10
```

### **📝 Übungen:**  

1. Gib jedes Element eines Arrays in Großbuchstaben aus.  
2. Berechne die Summe aller Zahlen in einem Array mithilfe von `.forEach()`.  
3. Prüfe, ob jedes Element eines Arrays durch 3 teilbar ist.  

**🔍 Lösungen:**  

```js
let names = ["anna", "ben", "clara"];
names.forEach(name => console.log(name.toUpperCase()));

let sum = 0;
let nums = [2, 4, 6, 8];
nums.forEach(num => sum += num);
console.log(sum); // 20

let checkDivisible = [3, 6, 9, 12];
checkDivisible.forEach(num => console.log(num % 3 === 0));
```

---

### **📌 `.map()` – Neues Array mit modifizierten Werten erstellen**  

```js
let numbers = [1, 2, 3, 4, 5];
let doubled = numbers.map(function(num) {
  return num * 2
});
console.log(doubled); // [2, 4, 6, 8, 10]
```

### **📝 Übungen:**  

1. Erhöhe jedes Element eines Arrays um 5.  
2. Erstelle ein Array, das angibt, ob eine Zahl gerade ist (`true` oder `false`).  
3. Wandelt eine Liste von Namen in ein Array aus deren Länge um.  

**🔍 Lösungen:**  

```js
let numbers = [10, 20, 30];
let plusFive = numbers.map(function {num} {
  num + 5
});
console.log(plusFive); // [15, 25, 35]

let evenCheck = [1, 2, 3, 4, 5].map(function(num) {
  return num % 2 === 0
});
console.log(evenCheck); // [false, true, false, true, false]

let names = ["Tom", "Max", "Lisa"];
let nameLengths = names.map(function(name) {
  name.length
});
console.log(nameLengths); // [3, 3, 4]
```

---

### **📌 `.filter()` – Bestimmte Elemente herausfiltern**  

```js
let numbers = [1, 2, 3, 4, 5];
let evenNumbers = numbers.filter(function(num) {
  return num % 2 === 0
});
console.log(evenNumbers); // [2, 4]
```

### **📝 Übungen:**  

1. Behalte nur Zahlen größer als 10.  
2. Filtere aus einer Namensliste alle Namen, die mit "A" beginnen.  
3. Entferne alle Werte aus einem Array, die `null` oder `undefined` sind.  

**🔍 Lösungen:** 
 
```js
let nums = [5, 12, 18, 2];
let overTen = nums.filter(function(num) {
  return num > 10
});
console.log(overTen); // [12, 18]

let names = ["Anna", "Ben", "Alex", "Clara"];
let filteredNames = names.filter(function(name) {
  name.startsWith("A")
});
console.log(filteredNames); // ["Anna", "Alex"]

let values = [1, null, "Hello", undefined, 5];
let cleanValues = values.filter(function(value) {
  return value != null
});
console.log(cleanValues); // [1, "Hello", 5]
```

---

### **📌 `.reduce()` – Alle Werte auf einen Wert reduzieren** 
 
```js
let numbers = [1, 2, 3, 4, 5];
let sum = numbers.reduce(function(acc, num) {
  return acc + num
}, 0);
console.log(sum); // 15
```

### **📝 Übungen:**  

1. Berechne das Produkt aller Zahlen in einem Array.  
2. Finde den höchsten Wert in einem Array mit `.reduce()`.  
3. Kette alle Wörter eines Arrays zu einem Satz zusammen.  

**🔍 Lösungen:**  

```js
let numbers = [2, 3, 4];
let product = numbers.reduce(function(acc, num) {
  return acc * num
}, 1);
console.log(product); // 24

let maxNum = [10, 5, 20, 8].reduce(function(max, num) {
  num > max ? num : max
}, 0);
console.log(maxNum); // 20

let words = ["JavaScript", "ist", "super"];
let sentence = words.reduce(function(acc, word) {
  return acc + " " + word
});
console.log(sentence); // "JavaScript ist super"
```

---

# **🔹 Mehrdimensionale Arrays**  

### **📌 Iteration mit `.forEach()`**  

```js
let matrix = [
  [1, 2, 3],
  [4, 5, 6],
  [7, 8, 9]
];

matrix.forEach(functio(row) {
  row.forEach(function(num) {
    console.log(num)
  });
});
```

### **📝 Übungen:** 
 
1. Berechne die Summe aller Zahlen einer 2×2-Matrix.  
2. Erstelle eine 3×3-Matrix und gib sie zeilenweise aus.  
3. Erhöhe jedes Element einer Matrix um 10.  

**🔍 Lösungen:**  

```js
let matrix = [
  [1, 2],
  [3, 4]
];

let sum = matrix.reduce(function(acc, row) {
  return acc + row.reduce(function(a, b) {
    return a + b
  });
}, 0);
console.log(sum); // 10

let newMatrix = matrix.map(function(row) {
  return row.map(function(num) {
    num + 10
  });
});
console.log(newMatrix); // [[11, 12], [13, 14]]
```

---
