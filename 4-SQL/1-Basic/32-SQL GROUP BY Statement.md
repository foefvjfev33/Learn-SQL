# 📌 **`GROUP BY` في SQL – تجميع البيانات وتحليلها**

## 🔹 **ما هو `GROUP BY` في SQL؟**

يُستخدم **`GROUP BY`** **لتجميع الصفوف التي تحتوي على نفس القيم في مجموعة واحدة**، وغالبًا ما يُستخدم مع **الدوال التجميعية (`COUNT()`, `SUM()`, `AVG()`, `MAX()`, `MIN()`)** لتحليل البيانات.

✅ **يقسم البيانات إلى مجموعات بناءً على قيمة عمود معين**.  
✅ **يُستخدم مع الدوال التجميعية لاستخراج معلومات من كل مجموعة**.

---

## 🔹 **الصيغة العامة (`Syntax`)**

```sql
SELECT column_name, AGGREGATE_FUNCTION(column_name)  
FROM table_name  
GROUP BY column_name;
```

📌 **يجب أن تحتوي `SELECT` على الأعمدة المستخدمة في `GROUP BY` أو الدوال التجميعية.**

---

## 🔹 **مثال عملي على `GROUP BY`**

### 🗄️ **جدول `orders` (الطلبات)**

|order_id|customer|category|amount|
|---|---|---|---|
|1|Ali|Electronics|200|
|2|Sara|Clothing|150|
|3|Ali|Electronics|300|
|4|Omar|Clothing|100|
|5|Sara|Electronics|250|

### 🎯 **1️⃣ عدد الطلبات لكل عميل (`COUNT()`)**

```sql
SELECT customer, COUNT(order_id) AS order_count  
FROM orders  
GROUP BY customer;
```

🔹 **النتيجة:**

|customer|order_count|
|---|---|
|Ali|2|
|Sara|2|
|Omar|1|

📌 **تم تجميع الطلبات حسب `customer`، وحساب عدد الطلبات لكل عميل.**

---

### 🎯 **2️⃣ إجمالي المبيعات لكل فئة (`SUM()`)**

```sql
SELECT category, SUM(amount) AS total_sales  
FROM orders  
GROUP BY category;
```

🔹 **النتيجة:**

|category|total_sales|
|---|---|
|Electronics|750|
|Clothing|250|

📌 **تم حساب إجمالي المبيعات لكل فئة.**

---

### 🎯 **3️⃣ متوسط قيمة الطلبات لكل عميل (`AVG()`)**

```sql
SELECT customer, AVG(amount) AS avg_order_value  
FROM orders  
GROUP BY customer;
```

🔹 **النتيجة:**

|customer|avg_order_value|
|---|---|
|Ali|250|
|Sara|200|
|Omar|100|

📌 **تم حساب متوسط قيمة الطلبات لكل عميل.**

---

## 🔹 **استخدام `GROUP BY` مع `HAVING` لتصفية النتائج**

🚀 **`WHERE` لا يعمل مع الدوال التجميعية، لذلك نستخدم `HAVING` بدلاً منه**.

### 🎯 **عرض الفئات التي حققت مبيعات أكبر من 300 فقط**

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

## 🏆 **ملخص سريع عن `GROUP BY`**

|الميزة|التفاصيل|
|---|---|
|**يُستخدم لتجميع البيانات**|يقسم البيانات إلى مجموعات حسب قيمة عمود معين.|
|**يُستخدم مع الدوال التجميعية**|مثل `SUM()`, `COUNT()`, `AVG()`, `MAX()`, `MIN()`.|
|**`HAVING` يُستخدم لتصفية النتائج**|لا يمكن استخدام `WHERE` مع القيم الناتجة من `GROUP BY`.|
|**يساعد في تحليل البيانات**|مثل حساب إجمالي المبيعات أو عدد الطلبات لكل فئة.|

---

## 🎯 **الخلاصة**

- **`GROUP BY`** يُستخدم **لتجميع الصفوف المتشابهة وتحليل البيانات باستخدام الدوال التجميعية**.
- **`HAVING`** يُستخدم لتصفية النتائج بعد التجميع.
- **يجب أن تحتوي `SELECT` فقط على الأعمدة الموجودة في `GROUP BY` أو الدوال التجميعية.**

---


## Connect Me :

- https://github.com/foefvjfev33
- https://t.me/It_auf
- https://www.youtube.com/@IT_red-j9b
- https://www.linkedin.com/in/mohamed-auf-860537353/