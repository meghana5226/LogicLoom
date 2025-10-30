
# 🕒 Time and Space Complexity — Master Guide

Welcome to the **Time Complexity Mastery Repo** 💻  
Your ultimate reference for analyzing algorithm efficiency — from basics to advanced interview-level mastery.

---

## 📘 Overview
Every algorithm has two invisible costs:
- **Time Complexity (TC):** How long it takes to run.
- **Space Complexity (SC):** How much memory it uses.

Understanding them helps you:
✅ Pick optimal solutions  
✅ Predict performance for large inputs  
✅ Crack technical interviews confidently

---

## 🧠 1. What is Time Complexity?

Time complexity measures **how execution time grows** as input size increases.

### 🎯 Why It’s Needed
- Machine-independent comparison  
- Predicts scalability  
- Helps you identify bottlenecks early  

Example (Guess the Number Game):
- **Linear Guess (1–1000):** O(n)
- **Binary Search Guess:** O(log n)

---

## ⚙️ 2. Asymptotic Notations

| Notation | Meaning | Represents | Example |
|-----------|----------|-------------|----------|
| **O(g(n))** | Upper Bound | Worst-case | Binary Search → O(log n) |
| **Ω(g(n))** | Lower Bound | Best-case | Linear Search (first element) → Ω(1) |
| **Θ(g(n))** | Tight Bound | Average case | Merge Sort → Θ(n log n) |

💡 **Trick to Remember:**  
> O = “Overestimate” (upper bound)  
> Ω = “Optimistic” (best)  
> Θ = “Typical” (average)

---

## 🧩 3. Common Complexities (Fastest → Slowest)

| Notation | Name | Example |
|-----------|------|----------|
| O(1) | Constant | Accessing array element |
| O(log n) | Logarithmic | Binary Search |
| O(n) | Linear | Traversing array |
| O(n log n) | Log-linear | Merge Sort |
| O(n²) | Quadratic | Bubble Sort |
| O(2ⁿ) | Exponential | Subset Generation |
| O(n!) | Factorial | Permutation Generation |

---

## 📏 4. Rules to Calculate Time Complexity

1️⃣ **Drop constants:**  
`T(n) = 5n → O(n)`

2️⃣ **Drop lower terms:**  
`T(n) = n² + 10n + 5 → O(n²)`

3️⃣ **Sequential statements:**  
Add → `O(n) + O(n²) = O(n²)`

4️⃣ **Nested loops:**  
Multiply →  
```

for i in n:
for j in n:

````
→ O(n²)

5️⃣ **Divide-and-conquer:**  
`T(n) = aT(n/b) + f(n)` → Use Master Theorem

---

## 💡 5. Real Examples

### Example 1 — Binary Search
```python
while left <= right:
    mid = (left + right)//2
````

⏱ **Time:** O(log n)
💾 **Space:** O(1)

---

### Example 2 — Fibonacci Recursion

```python
def fib(n):
    if n <= 1: return 1
    return fib(n-1) + fib(n-2)
```

⏱ **Time:** O(2ⁿ)
💾 **Space:** O(n) (due to recursion stack)

🧠 Optimized using DP → O(n)

---

### Example 3 — Nested Variable Steps

```python
for i in range(1, n):
    for j in range(i, n, i):
        print("hi")
```

✅ Total operations = n/1 + n/2 + n/3 + ... + n/n ≈ n log n
⏱ **Time:** O(n log n)

---

### Example 4 — Prime Check

```python
for i in range(2, int(math.sqrt(n))):
    if n % i == 0: return False
```

⏱ **Time:** O(√n)
💾 **Space:** O(1)

---

## 💾 6. What is Space Complexity?

**Definition:**

> Total memory required by an algorithm, including input + auxiliary (extra) space.

### Example

```python
arr = [0]*n
```

⏱ Time: O(n)
💾 Space: O(n)

**Auxiliary Space:** Extra memory beyond input.
Example:

```python
sum = 0
for i in arr: sum += i
```

→ Auxiliary space = O(1)

---

## ⚔️ 7. Time vs Space Complexity

| Aspect  | Time                    | Space                   |
| ------- | ----------------------- | ----------------------- |
| Meaning | Execution time          | Memory used             |
| Unit    | CPU steps               | Bytes                   |
| Focus   | Optimize speed          | Optimize memory         |
| Example | Merge Sort – O(n log n) | Merge Sort – O(n) extra |

---

## 🧩 8. Master Theorem (For Recursive Algorithms)

T(n) = aT(n/b) + f(n)

| Case   | Condition                 | Result               |
| ------ | ------------------------- | -------------------- |
| Case 1 | f(n) = O(n^(log_b a - ε)) | O(n^(log_b a))       |
| Case 2 | f(n) = Θ(n^(log_b a))     | O(n^(log_b a) log n) |
| Case 3 | f(n) = Ω(n^(log_b a + ε)) | O(f(n))              |

**Example:**
T(n) = 2T(n/2) + O(n) → **O(n log n)**

---

## ⚡ 9. Quick Estimation Tricks — “Solve in 1 Minute”

### 🧠 Step-by-Step TC Estimation

1. **Count loops →**

   * One loop: O(n)
   * Two nested loops: O(n²)
   * Logarithmic change (i*=2 or n/=2): O(log n)
2. **Check recursion →**

   * Single recursion → O(n)
   * Double recursion → O(2ⁿ)
   * Divide-and-conquer → O(n log n)
3. **Check function calls or recursion stack →** for Space Complexity.
4. **Ignore constants and small terms.**
5. **If confusion →** count number of iterations manually for small `n`.

---

### 💡 Quick Space Complexity Estimation

| Code Pattern          | Space Complexity |
| --------------------- | ---------------- |
| Simple variables      | O(1)             |
| Array of size n       | O(n)             |
| 2D Matrix n×n         | O(n²)            |
| Recursion depth n     | O(n)             |
| Hashmap of n elements | O(n)             |

---

### ⚙️ Superfast Shortcut Table

| Pattern                                              | Complexity |
| ---------------------------------------------------- | ---------- |
| Single loop → `for i in range(n)`                    | O(n)       |
| Nested loop → `for i in range(n): for j in range(n)` | O(n²)      |
| Loop halving → `while n > 0: n/=2`                   | O(log n)   |
| Divide & Conquer → Merge Sort                        | O(n log n) |
| Recursion doubling → Fibonacci                       | O(2ⁿ)      |
| All subsets → Power set                              | O(2ⁿ × n)  |

---

### 🎯 Pro Interview Tip

> In interviews, **don’t say just “O(n)”** — add a short reason:
> “It’s O(n) because the loop runs once per input element.”

---

## 🧾 10. Cheat Sheet Summary

| Complexity | Example           | Ideal For          |
| ---------- | ----------------- | ------------------ |
| O(1)       | Accessing element | Any data           |
| O(log n)   | Binary Search     | Huge data          |
| O(n)       | Linear Traversal  | Moderate data      |
| O(n log n) | Merge Sort        | Sorting large data |
| O(n²)      | Nested Loops      | Small datasets     |
| O(2ⁿ)      | Recursion         | n < 20             |
| O(n!)      | Permutations      | n < 10             |

---

## 🧩 11. Practice Tip

When you see code:

1. Identify **loops/recursions**
2. Multiply their ranges
3. Add separate fragments
4. Drop constants/lower terms

🔹 That’s your **Time Complexity**.
🔹 Count extra memory/recursion stack → **Space Complexity**.

---

## 🧠 Final Words

> Time Complexity isn’t just about formulas — it’s about **thinking like the computer**.
> Once you can estimate TC/SC in seconds, optimizing becomes effortless.