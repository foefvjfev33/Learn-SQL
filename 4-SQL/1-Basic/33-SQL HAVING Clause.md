# 📌 **`HAVING` في SQL – تصفية البيانات بعد `GROUP BY`**

## 🔹 **ما هو `HAVING` في SQL؟**

🚀 **`HAVING`** يُستخدم **لتصفية نتائج الاستعلام بعد استخدام `GROUP BY`**.  
✅ **يشبه `WHERE` لكنه يُستخدم مع الدوال التجميعية (`COUNT()`, `SUM()`, `AVG()`, `MAX()`, `MIN()`)**.  
✅ **`WHERE` يُستخدم قبل `GROUP BY` لتصفية الصفوف، بينما `HAVING` يُستخدم بعد `GROUP BY` لتصفية المجموعات.**

---

## 🔹 **الصيغة العامة (`Syntax`)**

```sql
SELECT column_name, AGGREGATE_FUNCTION(column_name)  
FROM table_name  
GROUP BY column_name  
HAVING condition;
```

📌 **يجب أن يكون `HAVING` بعد `GROUP BY` مباشرة.**

---

## 🔹 **الفرق بين `WHERE` و `HAVING`**

|الشرط|`WHERE`|`HAVING`|
|---|---|---|
|**التصفية قبل `GROUP BY`**|✅|❌|
|**التصفية بعد `GROUP BY`**|❌|✅|
|**يمكن استخدامه مع الدوال التجميعية**|❌|✅|
|**يعمل على كل صف بشكل فردي**|✅|❌|
|**يعمل على مجموعات البيانات**|❌|✅|

---

## 🔹 **مثال عملي على `HAVING`**

### 🗄️ **جدول `orders` (الطلبات)**

|order_id|customer|category|amount|
|---|---|---|---|
|1|Ali|Electronics|200|
|2|Sara|Clothing|150|
|3|Ali|Electronics|300|
|4|Omar|Clothing|100|
|5|Sara|Electronics|250|

### 🎯 **1️⃣ عرض الفئات التي حققت مبيعات إجمالية أكبر من 300**

```sql
SELECT category, SUM(amount) AS total_sales  
FROM orders  
GROUP BY category  
HAVING SUM(amount) > 300;
```

🔹 **النتيجة:**

|category|total_sales|
|---|---|
|Electronics|750|

📌 **تمت تصفية الفئات وإظهار الفئات التي تجاوزت مبيعاتها 300 فقط.**

---

### 🎯 **2️⃣ عرض العملاء الذين لديهم أكثر من طلب واحد (`COUNT()`)**

```sql
SELECT customer, COUNT(order_id) AS order_count  
FROM orders  
GROUP BY customer  
HAVING COUNT(order_id) > 1;
```

🔹 **النتيجة:**

|customer|order_count|
|---|---|
|Ali|2|
|Sara|2|

📌 **تمت تصفية العملاء بحيث يظهر فقط من لديه أكثر من طلب واحد.**

---

### 🎯 **3️⃣ الجمع بين `WHERE` و `HAVING`**

🚀 **`WHERE` يُستخدم لتصفية الصفوف قبل `GROUP BY`، بينما `HAVING` لتصفية النتائج بعد `GROUP BY`.**

```sql
SELECT category, SUM(amount) AS total_sales  
FROM orders  
WHERE amount > 100  
GROUP BY category  
HAVING SUM(amount) > 300;
```

📌 **`WHERE amount > 100`** يستبعد الطلبات التي قيمتها **100 أو أقل** قبل `GROUP BY`.  
📌 **`HAVING SUM(amount) > 300`** يُظهر فقط الفئات التي إجمالي مبيعاتها **أكبر من 300** بعد `GROUP BY`.

---

## 🏆 **ملخص سريع عن `HAVING`**

|الميزة|التفاصيل|
|---|---|
|**يُستخدم لتصفية البيانات بعد `GROUP BY`**|✅|
|**يُستخدم مع الدوال التجميعية (`SUM()`, `COUNT()`, `AVG()`, إلخ)**|✅|
|**`WHERE` يُستخدم قبل `GROUP BY`، بينما `HAVING` بعده**|✅|
|**يمكن دمجه مع `WHERE` لتحسين التصفية**|✅|

---

## 🎯 **الخلاصة**

- **`HAVING`** يُستخدم **لتصفية النتائج بعد `GROUP BY`**.
- **يُستخدم مع الدوال التجميعية (`SUM()`, `COUNT()`, إلخ)**.
- **`WHERE` يُستخدم قبل `GROUP BY` لتصفية الصفوف، بينما `HAVING` يُستخدم بعد `GROUP BY` لتصفية النتائج المجمّعة.**

---


## Connect Me :

- https://github.com/foefvjfev33
- https://t.me/It_auf
- https://www.youtube.com/@IT_red-j9b
- https://www.linkedin.com/in/mohamed-auf-860537353/