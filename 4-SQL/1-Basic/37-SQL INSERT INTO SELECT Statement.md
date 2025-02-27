# 📌 **`INSERT INTO SELECT` في SQL – إدراج البيانات من جدول إلى آخر**

## 🔹 **ما هو `INSERT INTO SELECT` في SQL؟**

🚀 **`INSERT INTO SELECT`** يُستخدم **لنسخ البيانات من جدول إلى آخر عندما يكون الجدول الهدف موجودًا مسبقًا**.  
✅ **يُستخدم لنقل البيانات بين الجداول، أو دمج بيانات من عدة جداول في جدول واحد**.  
✅ **يجب أن يكون الجدول الوجهة (`destination table`) موجودًا مسبقًا قبل تشغيل الاستعلام**.

---

## 🔹 **الصيغة العامة (`Syntax`)**

### ✅ **إدراج جميع الأعمدة**

```sql
INSERT INTO destination_table  
SELECT * FROM source_table  
WHERE condition;
```

📌 **يجب أن يكون عدد الأعمدة وأنواع البيانات متطابقة بين الجدولين**.

### ✅ **إدراج أعمدة محددة**

```sql
INSERT INTO destination_table (column1, column2, ...)  
SELECT column1, column2, ... FROM source_table  
WHERE condition;
```

📌 **يجب تحديد الأعمدة بنفس الترتيب في الجدولين لضمان التوافق**.

---

## 🔹 **مثال عملي على `INSERT INTO SELECT`**

### 🗄️ **جدول `customers` (العملاء الأصليين)**

|customer_id|name|country|
|---|---|---|
|1|Ali|Egypt|
|2|Sara|USA|
|3|Omar|France|
|4|Huda|Egypt|

### 🗄️ **جدول `customers_backup` (النسخة الاحتياطية) – فارغ في البداية**

|customer_id|name|country|
|---|---|---|

---

### 🎯 **1️⃣ إدراج جميع البيانات من `customers` إلى `customers_backup`**

```sql
INSERT INTO customers_backup  
SELECT * FROM customers;
```

🔹 **النتيجة:** يتم نقل جميع البيانات إلى `customers_backup`.

|customer_id|name|country|
|---|---|---|
|1|Ali|Egypt|
|2|Sara|USA|
|3|Omar|France|
|4|Huda|Egypt|

---

### 🎯 **2️⃣ إدراج بيانات العملاء المصريين فقط**

```sql
INSERT INTO customers_backup (customer_id, name, country)  
SELECT customer_id, name, country FROM customers  
WHERE country = 'Egypt';
```

🔹 **النتيجة:** فقط العملاء المصريين سيتم إدراجهم في `customers_backup`.

|customer_id|name|country|
|---|---|---|
|1|Ali|Egypt|
|4|Huda|Egypt|

---

### 🎯 **3️⃣ إدراج بيانات من جدول يحتوي على أعمدة مختلفة**

🚀 **إذا كان الجدول الوجهة يحتوي على أعمدة مختلفة، حدد فقط الأعمدة المتوافقة.**

```sql
INSERT INTO customers_backup (customer_id, name)  
SELECT customer_id, name FROM customers;
```

📌 **يتم إدخال `customer_id` و `name` فقط، وسيكون العمود `country` فارغًا (`NULL`).**

---

## 🏆 **ملخص سريع عن `INSERT INTO SELECT`**

|الميزة|التفاصيل|
|---|---|
|**يُستخدم لنسخ البيانات من جدول إلى آخر**|✅|
|**يجب أن يكون الجدول الوجهة موجودًا مسبقًا**|✅|
|**يجب أن تتطابق الأعمدة المحددة في الجدولين**|✅|
|**يمكن تصفية البيانات باستخدام `WHERE`**|✅|

---

## 🎯 **الخلاصة**

- **`INSERT INTO SELECT`** يُستخدم لنقل البيانات بين الجداول.
- **يجب أن يكون الجدول الوجهة موجودًا مسبقًا**.
- **إذا كانت بنية الجدولين مختلفة، يجب تحديد الأعمدة المطابقة يدويًا**.
- **يمكن تصفية البيانات باستخدام `WHERE`** لنقل جزء محدد من البيانات فقط.

---


## Connect Me :

- https://github.com/foefvjfev33
- https://t.me/It_auf
- https://www.youtube.com/@IT_red-j9b
- https://www.linkedin.com/in/mohamed-auf-860537353/