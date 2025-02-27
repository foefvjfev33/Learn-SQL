# 📌 **`SELECT INTO` في SQL – إنشاء نسخة من البيانات**

## 🔹 **ما هو `SELECT INTO` في SQL؟**

🚀 **`SELECT INTO`** يُستخدم **لنسخ البيانات من جدول إلى جدول آخر**.  
✅ يُنشئ **جدولًا جديدًا تلقائيًا وينسخ البيانات إليه** بدون الحاجة إلى `CREATE TABLE`.  
✅ يُستخدم عادةً **لأخذ نسخة احتياطية من البيانات أو إنشاء جداول مؤقتة**.

---

## 🔹 **الصيغة العامة (`Syntax`)**

```sql
SELECT column1, column2, ...  
INTO new_table  
FROM existing_table  
WHERE condition;
```

📌 **يتم إنشاء `new_table` تلقائيًا بناءً على البيانات المحددة من `existing_table`**.  
📌 **يمكنك تحديد أعمدة معينة أو كل الأعمدة باستخدام `*`**.

---

## 🔹 **مثال عملي على `SELECT INTO`**

### 🗄️ **جدول `customers` (العملاء)**

|customer_id|name|country|
|---|---|---|
|1|Ali|Egypt|
|2|Sara|USA|
|3|Omar|France|
|4|Huda|Egypt|

---

### 🎯 **1️⃣ إنشاء جدول جديد ونسخ جميع البيانات**

```sql
SELECT * INTO customers_backup  
FROM customers;
```

🔹 **النتيجة:** يتم إنشاء **جدول جديد باسم `customers_backup` يحتوي على نفس بيانات `customers`**.

---

### 🎯 **2️⃣ إنشاء جدول جديد ونسخ بيانات محددة فقط**

```sql
SELECT customer_id, name INTO egyptian_customers  
FROM customers  
WHERE country = 'Egypt';
```

🔹 **النتيجة:** يتم إنشاء جدول جديد باسم `egyptian_customers` يحتوي فقط على العملاء من **مصر (`Egypt`)**.

|customer_id|name|
|---|---|
|1|Ali|
|4|Huda|

---

### 🎯 **3️⃣ نسخ بيانات من جدول إلى جدول موجود (`INSERT INTO ... SELECT`)**

🚀 إذا كان **الجدول موجودًا مسبقًا، يجب استخدام `INSERT INTO ... SELECT` بدلاً من `SELECT INTO`**.

```sql
INSERT INTO customers_backup (customer_id, name, country)  
SELECT customer_id, name, country FROM customers  
WHERE country = 'USA';
```

📌 **هذا يضيف بيانات العملاء من `USA` إلى `customers_backup` دون إنشاء جدول جديد.**

---

## 🏆 **ملخص سريع عن `SELECT INTO`**

|الميزة|التفاصيل|
|---|---|
|**يُستخدم لإنشاء جدول جديد ونسخ البيانات إليه**|✅|
|**لا يحتاج إلى `CREATE TABLE` مسبقًا**|✅|
|**لا يمكن نسخه إلى جدول موجود، بل يتم إنشاؤه تلقائيًا**|✅|
|**إذا كان الجدول موجودًا، استخدم `INSERT INTO ... SELECT` بدلاً منه**|✅|

---

## 🎯 **الخلاصة**

- **`SELECT INTO`** يُستخدم **لإنشاء نسخة جديدة من البيانات في جدول جديد**.
- **يُنشئ الجدول تلقائيًا بناءً على البيانات المحددة من الجدول الأصلي**.
- **إذا كنت تريد نسخ البيانات إلى جدول موجود، استخدم `INSERT INTO ... SELECT` بدلاً من ذلك**.

---


## Connect Me :

- https://github.com/foefvjfev33
- https://t.me/It_auf
- https://www.youtube.com/@IT_red-j9b
- https://www.linkedin.com/in/mohamed-auf-860537353/