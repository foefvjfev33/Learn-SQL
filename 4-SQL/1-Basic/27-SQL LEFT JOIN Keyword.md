# 📌 **`LEFT JOIN` في SQL – الجلب من الجدول الأيسر**

## 🔹 **ما هو `LEFT JOIN`؟**

يُستخدم **`LEFT JOIN`** في **SQL** لجلب **جميع الصفوف من الجدول الأيسر (`LEFT TABLE`)**، مع البيانات المطابقة من الجدول الأيمن (`RIGHT TABLE`).  
✅ **إذا لم يكن هناك تطابق، فسيتم إرجاع `NULL` للبيانات غير الموجودة من الجدول الأيمن.**

---

## 🔹 **الصيغة العامة (`Syntax`)**

```sql
SELECT table1.column1, table2.column2, ...  
FROM table1  
LEFT JOIN table2  
ON table1.common_column = table2.common_column;
```

🔹 **يعيد جميع الصفوف من `table1` (الجدول الأيسر)، ويضيف البيانات المطابقة من `table2` (الجدول الأيمن).**  
🔹 **إذا لم يكن هناك تطابق، فسيتم إرجاع `NULL` من `table2`.**

---

## 🔹 **مثال عملي على `LEFT JOIN`**

### 🗄️ **جدول `employees` (الموظفون)**

|id|name|department_id|
|---|---|---|
|1|John|101|
|2|Alice|102|
|3|Bob|NULL|

### 🗄️ **جدول `departments` (الأقسام)**

|id|department_name|
|---|---|
|101|IT|
|102|HR|

🔹 **نريد جلب جميع الموظفين مع أقسامهم (حتى الذين ليس لديهم قسم).**

```sql
SELECT employees.name, departments.department_name  
FROM employees  
LEFT JOIN departments ON employees.department_id = departments.id;
```

🔹 **النتيجة:**

|name|department_name|
|---|---|
|John|IT|
|Alice|HR|
|Bob|NULL|

📌 **الموظف "Bob" ليس لديه `department_id` مطابق، لذا يظهر `NULL`.**

---

## 🔹 **استخدام `LEFT JOIN` مع `WHERE` لتصفية النتائج**

```sql
SELECT employees.name, departments.department_name  
FROM employees  
LEFT JOIN departments ON employees.department_id = departments.id  
WHERE departments.department_name IS NULL;
```

🔹 **النتيجة:** سيتم إرجاع الموظفين الذين **ليس لديهم قسم** (`department_id` غير موجود).

---

## 🔹 **`LEFT JOIN` مع `COUNT()` لمعرفة عدد الموظفين في كل قسم**

```sql
SELECT departments.department_name, COUNT(employees.id) AS employee_count  
FROM departments  
LEFT JOIN employees ON departments.id = employees.department_id  
GROUP BY departments.department_name;
```

🔹 **النتيجة:**

|department_name|employee_count|
|---|---|
|IT|1|
|HR|1|
|Finance|0|

📌 **قسم `Finance` لم يكن في `employees`، لكنه ظهر بسبب `LEFT JOIN`.**

---

## 🏆 **ملخص سريع عن `LEFT JOIN`**

|الميزة|التفاصيل|
|---|---|
|**يجلب جميع الصفوف من الجدول الأيسر**|حتى لو لم يكن هناك تطابق في الجدول الأيمن.|
|**يعرض `NULL` للقيم غير المطابقة**|إذا لم يكن هناك تطابق في `table2`.|
|**يُستخدم مع `WHERE`**|لتصفية النتائج (مثل البحث عن القيم غير الموجودة).|
|**يُستخدم مع `COUNT()`**|لمعرفة عدد العناصر المرتبطة في الجدول الأيمن.|

---

## 🎯 **الخلاصة**

- **`LEFT JOIN`** يُستخدم **للحفاظ على جميع بيانات الجدول الأيسر**.
- **إذا لم يكن هناك تطابق، يتم إرجاع `NULL` من الجدول الأيمن**.
- **يُستخدم لاكتشاف البيانات المفقودة**، مثل الموظفين بدون أقسام.
- **مفيد عند تحليل البيانات، خاصةً مع `COUNT()` و `GROUP BY`**.

---


## Connect Me :

- https://github.com/foefvjfev33
- https://t.me/It_auf
- https://www.youtube.com/@IT_red-j9b
- https://www.linkedin.com/in/mohamed-auf-860537353/