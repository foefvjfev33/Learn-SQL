# 📌 **`FULL OUTER JOIN` في SQL – الجلب الكامل من الجدولين**

## 🔹 **ما هو `FULL OUTER JOIN`؟**

يُستخدم **`FULL OUTER JOIN`** في **SQL** لدمج البيانات من **جدولين**، حيث يعيد:  
✅ **جميع الصفوف من الجدول الأيسر (`LEFT TABLE`)** حتى إن لم يكن هناك تطابق.  
✅ **جميع الصفوف من الجدول الأيمن (`RIGHT TABLE`)** حتى إن لم يكن هناك تطابق.  
✅ **إذا لم يكن هناك تطابق بين الجدولين، يتم إرجاع `NULL` في الأعمدة غير المطابقة.**

---

## 🔹 **الصيغة العامة (`Syntax`)**

```sql
SELECT table1.column1, table2.column2, ...  
FROM table1  
FULL OUTER JOIN table2  
ON table1.common_column = table2.common_column;
```

🔹 **يعيد جميع البيانات من `table1` و `table2`، مع إظهار `NULL` عند عدم التطابق.**

---

## 🔹 **مثال عملي على `FULL OUTER JOIN`**

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
|103|Finance|

🔹 **نريد جلب جميع الموظفين وجميع الأقسام حتى لو لم يكن هناك تطابق.**

```sql
SELECT employees.name, employees.department_id, departments.department_name  
FROM employees  
FULL OUTER JOIN departments ON employees.department_id = departments.id;
```

🔹 **النتيجة:**

|name|department_id|department_name|
|---|---|---|
|John|101|IT|
|Alice|102|HR|
|Bob|NULL|NULL|
|NULL|103|Finance|

📌 **تحليل النتيجة:**

- **John و Alice** لهما قسم مطابق، لذا ظهرا بشكل عادي.
- **Bob** ليس له قسم (`NULL` في `department_name`).
- **Finance** لا يحتوي على موظفين (`NULL` في `name`).

---

## 🔹 **`FULL OUTER JOIN` مع `WHERE` لتصفية البيانات غير المتطابقة**

### 🔍 **لإظهار البيانات غير المتطابقة فقط (`NULL` في أحد الجدولين)**

```sql
SELECT employees.name, employees.department_id, departments.department_name  
FROM employees  
FULL OUTER JOIN departments ON employees.department_id = departments.id  
WHERE employees.name IS NULL OR departments.department_name IS NULL;
```

🔹 **النتيجة:**

|name|department_id|department_name|
|---|---|---|
|Bob|NULL|NULL|
|NULL|103|Finance|

📌 **هذه الطريقة تعرض فقط الموظفين بدون أقسام، أو الأقسام التي ليس لديها موظفون.**

---

## 🔹 **`FULL OUTER JOIN` مع `COUNT()` لمعرفة عدد الموظفين في كل قسم**

```sql
SELECT departments.department_name, COUNT(employees.id) AS employee_count  
FROM employees  
FULL OUTER JOIN departments ON employees.department_id = departments.id  
GROUP BY departments.department_name;
```

🔹 **النتيجة:**

|department_name|employee_count|
|---|---|
|IT|1|
|HR|1|
|Finance|0|
|NULL|1|

📌 **لاحظ أن `NULL` في `department_name` يشير إلى موظفين ليس لديهم قسم.**

---

## 🏆 **ملخص سريع عن `FULL OUTER JOIN`**

|الميزة|التفاصيل|
|---|---|
|**يجلب جميع الصفوف من الجدولين**|يعيد كل البيانات سواء كانت متطابقة أم لا.|
|**يعرض `NULL` عند عدم التطابق**|إذا لم يكن هناك تطابق، يتم وضع `NULL` في الأعمدة الفارغة.|
|**يُستخدم مع `WHERE`**|لاستخراج البيانات غير المتطابقة فقط.|
|**يُستخدم مع `COUNT()`**|لمعرفة عدد البيانات المرتبطة بين الجدولين.|

---

## 🎯 **الخلاصة**

- **`FULL OUTER JOIN`** يُستخدم **لجلب جميع البيانات من الجدولين مع عرض `NULL` عند عدم التطابق**.
- **يُظهر جميع الصفوف من `LEFT JOIN` و `RIGHT JOIN` معًا**.
- **يُستخدم لتحليل البيانات المفقودة بين الجدولين**.
- **مفيد جدًا في عمليات `DATA AUDITING` والتحليل الإحصائي**.

---


## Connect Me :

- https://github.com/foefvjfev33
- https://t.me/It_auf
- https://www.youtube.com/@IT_red-j9b
- https://www.linkedin.com/in/mohamed-auf-860537353/