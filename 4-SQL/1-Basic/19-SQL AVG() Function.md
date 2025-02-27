# 📌 **دالة `AVG()` في SQL**

تُستخدم دالة **`AVG()`** في **SQL** لحساب **متوسط القيم** في عمود معين، مثل متوسط الأسعار أو الكميات.

---

## 🔹 **1. حساب المتوسط لجميع القيم في العمود**

تُرجع `AVG(column_name)` **المتوسط الحسابي** لجميع القيم في العمود المحدد.

### ✅ **مثال: حساب متوسط سعر الفواكه**

```sql
SELECT AVG(price) AS average_price FROM fruits;
```

🔹 **النتيجة**: متوسط جميع القيم في عمود `price`.

---

## 🔹 **2. استخدام `AVG()` مع `WHERE` (شرط)**

يمكنك استخدام `AVG()` مع `WHERE` لحساب المتوسط فقط للصفوف التي تحقق شرطًا معينًا.

### ✅ **مثال: حساب متوسط سعر الموز فقط**

```sql
SELECT AVG(price) AS average_banana_price
FROM fruits
WHERE name = 'Banana';
```

🔹 **النتيجة**: متوسط أسعار الفاكهة التي اسمها `Banana`.

---

## 🔹 **3. استخدام `AVG()` مع `GROUP BY`**

تُستخدم `AVG()` مع `GROUP BY` لحساب المتوسط لكل مجموعة من البيانات.

### ✅ **مثال: حساب متوسط السعر لكل نوع فاكهة**

```sql
SELECT name, AVG(price) AS average_price
FROM fruits
GROUP BY name;
```

🔹 **النتيجة**: تعرض كل نوع فاكهة مع متوسط سعره.

---

## 🔹 **4. استخدام `AVG()` مع `HAVING` لتصفية النتائج**

`HAVING` تُستخدم لتحديد شرط بعد `GROUP BY`.

### ✅ **مثال: عرض الفواكه التي متوسط سعرها أكبر من 10**

```sql
SELECT name, AVG(price) AS average_price
FROM fruits
GROUP BY name
HAVING AVG(price) > 10;
```

🔹 **النتيجة**: يعرض أنواع الفواكه التي متوسط سعرها **أكبر من 10**.

---

## 🔹 **5. التعامل مع القيم `NULL` في `AVG()`**

- دالة `AVG()` **تتجاهل القيم `NULL`** أثناء الحساب.
- إذا كانت جميع القيم `NULL`، فإنها تُرجع `NULL`، وليس `0`.

### ✅ **مثال: حساب متوسط الكميات (مع وجود `NULL`)**

```sql
SELECT AVG(quantity) AS average_quantity FROM fruits;
```

🔹 **إذا كان هناك قيم `NULL` في `quantity`، سيتم تجاهلها.**

---

## 🏆 **ملخص سريع لدالة `AVG()`**

|الدالة|الوظيفة|
|---|---|
|`AVG(column_name)`|حساب متوسط القيم في العمود|
|`AVG(column_name) WHERE condition`|حساب المتوسط فقط للصفوف التي تحقق شرطًا معينًا|
|`AVG(column_name) GROUP BY column_name`|حساب المتوسط لكل مجموعة من البيانات|
|`AVG(column_name) HAVING condition`|تصفية النتائج بعد `GROUP BY`|
|`AVG(column_name)` مع `NULL`|يتم تجاهل القيم `NULL` أثناء الحساب|

---

## 🎯 **الخلاصة**

- **`AVG()`** تُستخدم لحساب **المتوسط الحسابي** لقيم العمود.
- يمكن استخدامها مع **`WHERE`** لحساب المتوسط بشرط معين.
- يمكن دمجها مع **`GROUP BY`** لحساب المتوسط لكل فئة.
- يمكن تصفية النتائج باستخدام **`HAVING`** بعد `GROUP BY`.
- **`NULL`** لا يؤثر على نتيجة `AVG()`.

---


## Connect Me :

- https://github.com/foefvjfev33
- https://t.me/It_auf
- https://www.youtube.com/@IT_red-j9b
- https://www.linkedin.com/in/mohamed-auf-860537353/