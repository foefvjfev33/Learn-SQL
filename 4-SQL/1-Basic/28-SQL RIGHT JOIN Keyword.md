# 📌 **`RIGHT JOIN` في SQL – الجلب من الجدول الأيمن**

## 🔹 **ما هو `RIGHT JOIN`؟**

يُستخدم **`RIGHT JOIN`** في **SQL** لجلب **جميع الصفوف من الجدول الأيمن (`RIGHT TABLE`)**، مع البيانات المطابقة من الجدول الأيسر (`LEFT TABLE`).  
✅ **إذا لم يكن هناك تطابق، فسيتم إرجاع `NULL` للبيانات غير الموجودة من الجدول الأيسر.**

---

## 🔹 **الصيغة العامة (`Syntax`)**

```sql
SELECT table1.column1, table2.column2, ...  
FROM table1  
RIGHT JOIN table2  
ON table1.common_column = table2.common_column;
```

🔹 **يعيد جميع الصفوف من `table2` (الجدول الأيمن)، ويضيف البيانات المطابقة من `table1` (الجدول الأيسر).**  
🔹 **إذا لم يكن هناك تطابق، فسيتم إرجاع `NULL` من `table1`.**

---

## 🔹 **مثال عملي على `RIGHT JOIN`**

### 🗄️ **جدول `employees` (الموظفون)**

|id|name|department_id|
|---|---|---|
|1|John|101|
|2|Alice|102|

### 🗄️ **جدول `departments` (الأقسام)**

|id|department_name|
|---|---|
|101|IT|
|102|HR|
|103|Finance|

🔹 **نريد جلب جميع الأقسام مع أسماء الموظفين (حتى الأقسام التي ليس بها موظفون).**

```sql
SELECT employees.name, departments.department_name  
FROM employees  
RIGHT JOIN departments ON employees.department_id = departments.id;
```

🔹 **النتيجة:**

|name|department_name|
|---|---|
|John|IT|
|Alice|HR|
|NULL|Finance|

📌 **قسم "Finance" لا يحتوي على موظفين، لذا يظهر `NULL` في عمود `name`.**

---

## 🔹 **استخدام `RIGHT JOIN` مع `WHERE` لتصفية النتائج**

```sql
SELECT employees.name, departments.department_name  
FROM employees  
RIGHT JOIN departments ON employees.department_id = departments.id  
WHERE employees.name IS NULL;
```

🔹 **النتيجة:** يتم إرجاع الأقسام التي **ليس بها موظفون**.

---

## 🔹 **`RIGHT JOIN` مع `COUNT()` لمعرفة عدد الموظفين في كل قسم**

```sql
SELECT departments.department_name, COUNT(employees.id) AS employee_count  
FROM employees  
RIGHT JOIN departments ON employees.department_id = departments.id  
GROUP BY departments.department_name;
```

🔹 **النتيجة:**

|department_name|employee_count|
|---|---|
|IT|1|
|HR|1|
|Finance|0|

📌 **قسم `Finance` ظهر في النتيجة على الرغم من عدم وجود موظفين به.**

---

## 🏆 **ملخص سريع عن `RIGHT JOIN`**

|الميزة|التفاصيل|
|---|---|
|**يجلب جميع الصفوف من الجدول الأيمن**|حتى لو لم يكن هناك تطابق في الجدول الأيسر.|
|**يعرض `NULL` للقيم غير المطابقة**|إذا لم يكن هناك تطابق في `table1`.|
|**يُستخدم مع `WHERE`**|لتصفية النتائج (مثل البحث عن الأقسام بدون موظفين).|
|**يُستخدم مع `COUNT()`**|لمعرفة عدد العناصر المرتبطة في الجدول الأيسر.|

---

## 🎯 **الخلاصة**

- **`RIGHT JOIN`** يُستخدم **للحفاظ على جميع بيانات الجدول الأيمن**.
- **إذا لم يكن هناك تطابق، يتم إرجاع `NULL` من الجدول الأيسر**.
- **يُستخدم لاكتشاف البيانات المفقودة**، مثل الأقسام بدون موظفين.
- **مفيد عند تحليل البيانات، خاصةً مع `COUNT()` و `GROUP BY`**.

---


## Connect Me :

- https://github.com/foefvjfev33
- https://t.me/It_auf
- https://www.youtube.com/@IT_red-j9b
- https://www.linkedin.com/in/mohamed-auf-860537353/