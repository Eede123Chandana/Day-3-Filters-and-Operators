# 🔍 SQL Filtering & Operators

## 📌 Overview

SQL filtering is used to retrieve specific records from databases based on conditions.

Filtering techniques and operators help analysts work with large datasets, identify patterns, segment customers, and generate business insights.

**Objective:** Understand WHERE, HAVING, comparison operators, special operators, and logical operators with practical SQL examples.

---

## 1️⃣ What is Filtering in SQL?

Filtering means retrieving records that satisfy specified conditions.

**Example: Retail Sales Dataset**

| order_id | customer | city | amount |
|---|---|---|---|
| 101 | Rahul | Hyderabad | 15000 |
| 102 | Meera | Mumbai | 8000 |
| 103 | Mohan | Hyderabad | 25000 |
| 104 | Priya | Chennai | 12000 |

### Example: High-Value Transactions

```sql
SELECT *
FROM sales
WHERE amount > 10000;
```

**Result:** Returns transactions with an amount greater than 10,000.

---

## 2️⃣ WHERE vs HAVING

| WHERE | HAVING |
|---|---|
| Filters individual rows | Filters grouped/aggregate results |
| Applied before grouping | Applied after grouping |
| Cannot directly filter aggregate results | Supports aggregate conditions |
| Commonly used with SELECT | Commonly used with GROUP BY |

### WHERE Example

```sql
SELECT *
FROM sales
WHERE amount > 10000;
```

### HAVING Example

```sql
SELECT
    city,
    SUM(amount) AS total_sales
FROM sales
GROUP BY city
HAVING SUM(amount) > 20000;
```

**Business Use Case:** Identify cities generating more than ₹20,000 in revenue.

---

## 3️⃣ Comparison Operators

| Operator | Meaning | Example |
|---|---|---|
| = | Equal | amount = 10000 |
| != or <> | Not Equal | city != 'Mumbai' |
| > | Greater Than | amount > 10000 |
| < | Less Than | amount < 5000 |
| >= | Greater Than or Equal | amount >= 10000 |
| <= | Less Than or Equal | amount <= 20000 |

### Example

```sql
SELECT *
FROM sales
WHERE amount >= 10000;
```

**Use Case:** Identify sales transactions meeting a minimum threshold.

---

## 4️⃣ Special SQL Operators

### 🔹 BETWEEN – Range Filtering

```sql
SELECT *
FROM sales
WHERE amount BETWEEN 5000 AND 20000;
```

Returns values from 5,000 through 20,000, including both boundaries.

### 🔹 IN – Multiple Value Matching

```sql
SELECT *
FROM sales
WHERE city IN ('Mumbai', 'Hyderabad');
```

Returns customers from either city.

### 🔹 NOT IN – Excluding Values

```sql
SELECT *
FROM sales
WHERE city NOT IN ('Mumbai', 'Chennai');
```

Excludes records matching the specified cities.

**Important:** NULL values require special handling with NOT IN.

### 🔹 LIKE – Pattern Matching

| Pattern | Meaning |
|---|---|
| 'M%' | Starts with M |
| '%M' | Ends with M |
| '%M%' | Contains M |
| 'M_' | M followed by exactly one character |

```sql
SELECT *
FROM sales
WHERE customer LIKE 'M%';
```

**Result:** Returns customers whose names start with M.

**Wildcards:**
- `%` → Zero or more characters
- `_` → Exactly one character

### 🔹 IS NULL / IS NOT NULL

Used to identify missing or present values.

```sql
SELECT *
FROM sales
WHERE city IS NULL;
```

```sql
SELECT *
FROM sales
WHERE city IS NOT NULL;
```

**Note:** Use IS NULL instead of `= NULL`.

---

## 5️⃣ Logical Operators

Logical operators combine or negate filtering conditions.

### AND – All Conditions Must Match

```sql
SELECT *
FROM sales
WHERE city = 'Hyderabad'
  AND amount > 10000;
```

### OR – Any Condition Can Match

```sql
SELECT *
FROM sales
WHERE city = 'Mumbai'
   OR city = 'Chennai';
```

### NOT – Negates a Condition

```sql
SELECT *
FROM sales
WHERE NOT city = 'Mumbai';
```

### Combining Operators

```sql
SELECT *
FROM sales
WHERE amount > 10000
  AND city IN ('Hyderabad', 'Chennai');
```

**Tip:** Use parentheses when combining AND and OR to make conditions clear and avoid incorrect results.

---

## 6️⃣ Real-World Business Applications

### 🛒 Retail Analytics

**Objective:** Identify high-value purchases.

```sql
SELECT *
FROM sales
WHERE amount >= 15000;
```

### 📈 Sales Performance

**Objective:** Identify cities exceeding revenue targets.

```sql
SELECT
    city,
    SUM(amount) AS revenue
FROM sales
GROUP BY city
HAVING SUM(amount) > 20000;
```

### 👥 Customer Segmentation

**Objective:** Find customers from Hyderabad or Mumbai who spent over ₹10,000.

```sql
SELECT *
FROM sales
WHERE city IN ('Hyderabad', 'Mumbai')
  AND amount > 10000;
```

### 🔍 Customer Search

**Objective:** Identify customer names beginning with M.

```sql
SELECT *
FROM sales
WHERE customer LIKE 'M%';
```

---

## 7️⃣ Important Interview Concepts

**Q1. WHERE vs HAVING?**

WHERE filters rows before grouping; HAVING filters grouped or aggregated results.

**Q2. BETWEEN vs IN?**

BETWEEN checks an inclusive range; IN checks membership in a specified list.

**Q3. LIKE vs =?**

LIKE supports wildcard-based pattern matching; = compares values for equality.

**Q4. Why use IS NULL?**

NULL represents an unknown or missing value, so ordinary equality comparisons cannot identify it.

**Q5. AND vs OR?**

AND requires every condition to be TRUE; OR requires at least one condition to be TRUE.

---

## 🎯 Key Takeaways

✅ WHERE filters individual rows.

✅ HAVING filters aggregate results.

✅ Comparison operators evaluate values.

✅ BETWEEN and IN simplify filtering.

✅ LIKE enables pattern matching.

✅ IS NULL identifies missing values.

✅ AND, OR, and NOT build complex conditions.

✅ Filtering supports efficient and meaningful business analysis.

---

## 💡 Final Thoughts

**Filtering is the backbone of SQL analysis.**

Mastering filtering techniques helps transform large datasets into focused, meaningful insights that support data-driven business decisions.

### 🏷️ Topics

`SQL` `WHERE` `HAVING` `SQL Operators` `Filtering` `LIKE` `BETWEEN` `IN` `Logical Operators` `MySQL` `Data Analytics` `Business Analytics`
