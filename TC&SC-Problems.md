
## 🔹 Step 1: Identify Loops / Recursion

Check **how many loops or recursive calls** are there and how they depend on `n`.

### 🧩 Example 1:

```java
for (int i = 0; i < n; i++) {
    System.out.println(i);
}
```

✅ One loop → runs `n` times
⏱ TC = **O(n)**
💾 SC = **O(1)** (no extra space)

---

## 🔹 Step 2: Multiply Their Ranges (Nested Loops)

If loops are **nested**, multiply how many times each one runs.

### 🧩 Example 2:

```java
for (int i = 0; i < n; i++) {
    for (int j = 0; j < n; j++) {
        System.out.println(i + j);
    }
}
```

✅ Outer loop → runs `n` times
✅ Inner loop → runs `n` times for each `i`
👉 Total = `n * n`
⏱ TC = **O(n²)**
💾 SC = **O(1)**

---

### 🧩 Example 3 (Different Ranges)

```java
for (int i = 0; i < n; i++) {
    for (int j = 0; j < m; j++) {
        System.out.println(i + j);
    }
}
```

✅ Outer → `n`
✅ Inner → `m`
👉 Total = `n * m`
⏱ TC = **O(n·m)**
💾 SC = **O(1)**

---

## 🔹 Step 3: Add Separate Fragments (Independent Parts)

If loops are **not nested**, you **add** their complexities.

### 🧩 Example 4:

```java
for (int i = 0; i < n; i++) {}      // O(n)
for (int j = 0; j < n; j++) {}      // O(n)
```

✅ Two independent loops
⏱ TC = **O(n + n)** → **O(2n)**
Drop constants (next step 👇) → **O(n)**
💾 SC = **O(1)**

---

## 🔹 Step 4: Drop Constants / Lower Terms

Keep **only the dominant term** — ignore constants and small powers.

### 🧩 Example 5:

```java
O(n² + n + 100) → O(n²)
O(5n) → O(n)
O(n³ + n² + n) → O(n³)
```

---

## ⚡ 1-Minute Trick Summary (Quick Estimation)

| Code Pattern                    | Shortcut Trick                | Time Complexity |
| ------------------------------- | ----------------------------- | --------------- |
| Single loop (0→n)               | runs n times                  | O(n)            |
| Nested loops (n×n)              | multiply ranges               | O(n²)           |
| 2 separate loops                | add ranges → drop constants   | O(n)            |
| Divide problem (half recursion) | recurrence T(n) = T(n/2)+O(1) | O(log n)        |
| Merge sort / Quick sort type    | T(n)=2T(n/2)+O(n)             | O(n log n)      |
| Double recursion (Fibonacci)    | exponential growth            | O(2ⁿ)           |

---

## 🧮 Space Complexity (SC) Quick Estimation

| Code Type                     | What Adds Space      | Space Complexity |
| ----------------------------- | -------------------- | ---------------- |
| Simple loop / no extra array  | no new space         | O(1)             |
| Using an array/list of size n | stores n elements    | O(n)             |
| 2D array (matrix)             | n×m elements         | O(n·m)           |
| Recursive call stack          | depth = no. of calls | O(depth)         |

---

## 💡 Practice Examples (Try Estimating)

1.

```java
for(int i=0;i<n;i++)
  for(int j=i;j<n;j++)
    System.out.println(i+j);
```

✅ Inner loop runs fewer times each iteration
⏱ TC ≈ n + (n−1) + … + 1 = O(n²)

---

2.

```java
for(int i=1;i<n;i*=2)
    System.out.println(i);
```

✅ i doubles → log₂n times
⏱ TC = **O(log n)**

---

3.

```java
void solve(int n){
   if(n==0) return;
   solve(n/2);
}
```

✅ Recursive halving → log₂n depth
⏱ TC = O(log n)
💾 SC = O(log n) (call stack)

---

### 🎯 How to Solve in Under 1 Minute

1. Count how many **loops** and **recursions** → note their **range**.
2. Multiply nested, add separate.
3. Drop constants and small terms.
4. Note extra data structures (for SC).
