# 📌 **الأسماء المستعارة (`Aliases`) في SQL**

**الأسماء المستعارة (Aliases)** تُستخدم في **SQL** لتغيير اسم الأعمدة أو الجداول في الاستعلامات، مما يجعل **النتائج أكثر وضوحًا وسهولة في القراءة** دون التأثير على البيانات الفعلية.

---

## 🔹 **1. الصيغة العامة لاستخدام `AS`**

```sql
SELECT column_name AS alias_name  
FROM table_name;
```

🔹 **أو مع الجداول:**

```sql
SELECT column_name  
FROM table_name AS alias_name;
```

- **`AS`** هو اختياري، ويمكنك استخدام الاسم المستعار بدون `AS`.
- الأسماء المستعارة تُستخدم **فقط أثناء تنفيذ الاستعلام** ولا تغير الهيكل الفعلي للجدول.

---

## 🔹 **2. استخدام `AS` مع أسماء الأعمدة**

🔸 **يمكن استخدام الأسماء المستعارة لجعل أسماء الأعمدة أكثر وضوحًا في النتائج.**

### ✅ **مثال: تغيير اسم العمود "emp_name" إلى "Employee Name"**

```sql
SELECT emp_name AS "Employee Name", salary AS "Monthly Salary"  
FROM employees;
```

🔹 **النتيجة:**

|Employee Name|Monthly Salary|
|---|---|
|John Doe|5000|
|Alice Smith|7000|

📌 **ملاحظة:** إذا كان الاسم المستعار يحتوي على **فراغات ( )**، يجب وضعه بين **علامات اقتباس `" "`** أو **أقواس `[]`** حسب نظام قواعد البيانات.

---

## 🔹 **3. استخدام `AS` مع أسماء الجداول**

🔸 **يمكن استخدام الأسماء المستعارة لتقصير أسماء الجداول عند التعامل مع استعلامات معقدة.**

### ✅ **مثال: استخدام Alias لتقصير اسم الجدول**

```sql
SELECT e.name, e.salary  
FROM employees AS e;
```

🔹 **مكافئ لـ:**

```sql
SELECT employees.name, employees.salary  
FROM employees;
```

📌 **الفائدة:** عند العمل مع **أسماء جداول طويلة أو متعددة**، يمكن تقصيرها لتسهيل القراءة.

---

## 🔹 **4. استخدام الأسماء المستعارة في `JOIN`**

🔸 **تُستخدم الأسماء المستعارة بشكل شائع في الاستعلامات التي تتضمن `JOIN` لتحسين الوضوح.**

### ✅ **مثال: استخدام `AS` مع `JOIN` لتسهيل الاستعلام**

```sql
SELECT e.name AS "Employee", d.department_name AS "Department"  
FROM employees AS e  
JOIN departments AS d ON e.department_id = d.id;
```

🔹 **بدون الأسماء المستعارة، يصبح الاستعلام أطول وأقل وضوحًا:**

```sql
SELECT employees.name AS "Employee", departments.department_name AS "Department"  
FROM employees  
JOIN departments ON employees.department_id = departments.id;
```

---

## 🔹 **5. استخدام الأسماء المستعارة مع العمليات الحسابية**

🔸 **يمكن استخدام `AS` لتسمية القيم المشتقة من العمليات الحسابية.**

### ✅ **مثال: حساب الراتب السنوي وعرضه باسم جديد**

```sql
SELECT name, salary, (salary * 12) AS "Annual Salary"  
FROM employees;
```

🔹 **النتيجة:**

|name|salary|Annual Salary|
|---|---|---|
|John|5000|60000|
|Alice|7000|84000|

📌 **بدون `AS`، سيتم عرض العمود الثالث باسم العملية (`(salary * 12)`) مما قد يكون غير مفهوم.**

---

## 🔹 **6. استخدام الأسماء المستعارة مع `GROUP BY` و `HAVING`**

🔸 **الأسماء المستعارة لا يمكن استخدامها مباشرة في `GROUP BY` و `HAVING`**، لكن يمكن استخدامها مع `ORDER BY`.

### ✅ **مثال: استخدام Alias مع `ORDER BY`**

```sql
SELECT department AS "Dept", COUNT(*) AS "Total Employees"  
FROM employees  
GROUP BY department  
ORDER BY "Total Employees" DESC;
```

🔹 **يتم ترتيب النتائج بناءً على عدد الموظفين (`Total Employees`) بدلاً من استخدام `COUNT(*)`.**

---

## 🏆 **ملخص سريع عن `Aliases` في SQL**

|الاستخدام|الوظيفة|
|---|---|
|`AS "اسم جديد"`|تعيين اسم مستعار للعمود لتسهيل القراءة.|
|`table_name AS alias`|تعيين اسم مستعار للجدول لجعل الاستعلام أقصر.|
|`AS مع العمليات الحسابية`|إعطاء اسم واضح للنتائج المحسوبة.|
|`AS في` JOIN``|تسهيل قراءة الاستعلام عند استخدام `JOIN`.|
|`ORDER BY "alias"`|يمكن استخدام الأسماء المستعارة مع `ORDER BY`.|
|`GROUP BY/HAVING`|لا تدعم الأسماء المستعارة مباشرةً.|

---

## 🎯 **الخلاصة**

- **`AS`** تُستخدم لإعطاء أسماء جديدة للأعمدة أو الجداول **دون تغيير البيانات الأصلية**.
- **يمكن استخدام `AS` مع `JOIN`** لتسهيل قراءة الاستعلامات الطويلة.
- **الأسماء المستعارة يمكن استخدامها مع العمليات الحسابية** مثل `(salary * 12) AS "Annual Salary"`.
- **يمكن استخدامها مع `ORDER BY` ولكن ليس مباشرة مع `GROUP BY` أو `HAVING`.**

---


## Connect Me :

- https://github.com/foefvjfev33
- https://t.me/It_auf
- https://www.youtube.com/@IT_red-j9b
- https://www.linkedin.com/in/mohamed-auf-860537353/