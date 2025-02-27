# 📌 **`INNER JOIN` في SQL – الجلب المشترك**

## 🔹 **ما هو `INNER JOIN`؟**

يُستخدم `INNER JOIN` في **SQL** لدمج الصفوف من **جدولين أو أكثر** استنادًا إلى شرط تطابق مشترك بينهما.

✅ **إذا لم يكن هناك تطابق بين الجدولين، فلن يتم عرض الصفوف في النتيجة.**

---

## 🔹 **الصيغة العامة (`Syntax`)**

```sql
SELECT table1.column1, table2.column2, ...  
FROM table1  
INNER JOIN table2  
ON table1.common_column = table2.common_column;
```

🔹 **يتم مطابقة البيانات بين `table1` و `table2` بناءً على `common_column`.**

---

## 🔹 **مثال عملي على `INNER JOIN`**

### 🗄️ **جدول `employees` (الموظفون)**

|id|name|department_id|
|---|---|---|
|1|John|101|
|2|Alice|102|
|3|Bob|103|

### 🗄️ **جدول `departments` (الأقسام)**

|id|department_name|
|---|---|
|101|IT|
|102|HR|

🔹 **نريد جلب أسماء الموظفين مع أسماء الأقسام الخاصة بهم باستخدام `INNER JOIN`.**

```sql
SELECT employees.name, departments.department_name  
FROM employees  
INNER JOIN departments ON employees.department_id = departments.id;
```

🔹 **النتيجة:**

|name|department_name|
|---|---|
|John|IT|
|Alice|HR|

📌 **الموظف "Bob" غير موجود في `departments`، لذا لم يظهر في النتيجة.**

---

## 🔹 **مثال باستخدام `INNER JOIN` مع عدة جداول**

إذا كان لدينا **جدول ثالث** `salaries` يحتوي على رواتب الموظفين، فيمكننا الربط بين الثلاثة جداول باستخدام `INNER JOIN`:

```sql
SELECT employees.name, departments.department_name, salaries.salary  
FROM employees  
INNER JOIN departments ON employees.department_id = departments.id  
INNER JOIN salaries ON employees.id = salaries.employee_id;
```

🔹 **هذه الطريقة تربط الجداول الثلاثة معًا بناءً على الأعمدة المشتركة.**

---

## 🔹 **`INNER JOIN` مع `WHERE` لتصفية النتائج**

```sql
SELECT employees.name, departments.department_name  
FROM employees  
INNER JOIN departments ON employees.department_id = departments.id  
WHERE departments.department_name = 'IT';
```

🔹 **النتيجة:** يتم إرجاع الموظفين الذين يعملون فقط في قسم `IT`.

---

## 🏆 **ملخص سريع عن `INNER JOIN`**

|الميزة|التفاصيل|
|---|---|
|**يُستخدم للربط بين الجداول**|يعتمد على مطابقة القيم المشتركة بين جدولين أو أكثر.|
|**يعرض فقط الصفوف المتطابقة**|إذا لم يكن هناك تطابق، فلن يظهر الصف في النتيجة.|
|**يمكن ربط أكثر من جدول**|باستخدام عدة `INNER JOIN` في استعلام واحد.|
|**يمكن استخدامه مع `WHERE`**|لتصفية النتائج حسب شروط إضافية.|

---

## 🎯 **الخلاصة**

- **`INNER JOIN`** هو **الأكثر استخدامًا** لربط البيانات بين الجداول.
- **يعرض فقط الصفوف التي تحتوي على تطابق بين الجدولين**.
- **يمكن ربط أكثر من جدول باستخدام `INNER JOIN`**.
- **يمكن دمجه مع `WHERE` للحصول على نتائج أكثر دقة**.

---


## Connect Me :

- https://github.com/foefvjfev33
- https://t.me/It_auf
- https://www.youtube.com/@IT_red-j9b
- https://www.linkedin.com/in/mohamed-auf-860537353/