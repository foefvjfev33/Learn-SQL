# 📌 **دالة `SUM()` في SQL**

تُستخدم دالة **`SUM()`** في **SQL** لحساب **مجموع القيم** في عمود معين، مثل مجموع الأسعار أو الكميات.

---

## 🔹 **1. حساب مجموع القيم في عمود**

تُرجع `SUM(column_name)` **المجموع الكلي** لجميع القيم في العمود المحدد.

### ✅ **مثال: حساب إجمالي الكميات في الجدول**

```sql
SELECT SUM(quantity) AS total_quantity FROM fruits;
```

🔹 **النتيجة**: مجموع جميع القيم في عمود `quantity`.

---

## 🔹 **2. استخدام `SUM()` مع `WHERE` (شرط)**

يمكنك استخدام `SUM()` مع `WHERE` لحساب المجموع فقط للصفوف التي تحقق شرطًا معينًا.

### ✅ **مثال: حساب مجموع كميات الموز فقط**

```sql
SELECT SUM(quantity) AS total_banana_quantity
FROM fruits
WHERE name = 'Banana';
```

🔹 **النتيجة**: مجموع كميات الفاكهة التي اسمها `Banana`.

---

## 🔹 **3. استخدام `SUM()` مع `GROUP BY`**

تُستخدم `SUM()` مع `GROUP BY` لحساب المجاميع لكل مجموعة من البيانات.

### ✅ **مثال: حساب مجموع الكميات لكل نوع فاكهة**

```sql
SELECT name, SUM(quantity) AS total_quantity
FROM fruits
GROUP BY name;
```

🔹 **النتيجة**: تعرض كل نوع من الفواكه مع مجموع كميته.

---

## 🔹 **4. استخدام `SUM()` مع `HAVING` لتصفية النتائج**

`HAVING` تُستخدم لتحديد شرط بعد `GROUP BY`.

### ✅ **مثال: عرض الفواكه التي مجموع كمياتها أكبر من 50**

```sql
SELECT name, SUM(quantity) AS total_quantity
FROM fruits
GROUP BY name
HAVING SUM(quantity) > 50;
```

🔹 **النتيجة**: يعرض أنواع الفواكه التي مجموع كمياتها **أكبر من 50**.

---

## 🔹 **5. التعامل مع القيم `NULL` في `SUM()`**

- دالة `SUM()` **تتجاهل القيم `NULL`** أثناء الحساب.
- إذا كانت جميع القيم `NULL`، فإنها تُرجع `NULL`، وليس `0`.

### ✅ **مثال: حساب مجموع الأسعار (مع وجود `NULL`)**

```sql
SELECT SUM(price) AS total_price FROM fruits;
```

🔹 **إذا كان هناك قيم `NULL` في `price`، سيتم تجاهلها.**

---

## 🏆 **ملخص سريع لدالة `SUM()`**

|الدالة|الوظيفة|
|---|---|
|`SUM(column_name)`|حساب مجموع القيم في العمود|
|`SUM(column_name) WHERE condition`|حساب المجموع فقط للصفوف التي تحقق شرطًا معينًا|
|`SUM(column_name) GROUP BY column_name`|حساب المجموع لكل مجموعة من البيانات|
|`SUM(column_name) HAVING condition`|تصفية النتائج بعد `GROUP BY`|
|`SUM(column_name)` مع `NULL`|يتم تجاهل القيم `NULL` أثناء الحساب|

---

## 🎯 **الخلاصة**

- **`SUM()`** تُستخدم لحساب المجموع الكلي لقيم العمود.
- يمكن استخدامها مع **`WHERE`** لحساب المجموع بشرط معين.
- يمكن دمجها مع **`GROUP BY`** لحساب المجموع لكل فئة.
- يمكن تصفية النتائج باستخدام **`HAVING`** بعد `GROUP BY`.
- **`NULL`** لا يؤثر على نتيجة `SUM()`.

---


## Connect Me :

- https://github.com/foefvjfev33
- https://t.me/It_auf
- https://www.youtube.com/@IT_red-j9b
- https://www.linkedin.com/in/mohamed-auf-860537353/