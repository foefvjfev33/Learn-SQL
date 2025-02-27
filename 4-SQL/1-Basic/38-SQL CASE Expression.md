# 📌 **`CASE` في SQL – استخدام العبارات الشرطية داخل الاستعلامات**

## 🔹 **ما هو `CASE` في SQL؟**

🚀 **`CASE`** يُستخدم **لتنفيذ منطق شرطي داخل استعلام SQL**، مما يسمح بإرجاع قيم مختلفة بناءً على شروط محددة، مثل `IF-ELSE` في لغات البرمجة.  
✅ يُستخدم عادةً مع `SELECT`, `UPDATE`, `ORDER BY`, و `GROUP BY`.

---

## 🔹 **الصيغة العامة (`Syntax`)**

### ✅ **`CASE` مع شروط متعددة (`WHEN... THEN...`)**

```sql
SELECT column_name,  
       CASE  
           WHEN condition1 THEN result1  
           WHEN condition2 THEN result2  
           ELSE default_result  
       END AS alias_name  
FROM table_name;
```

📌 **يتم فحص كل `WHEN` بالتسلسل حتى يتم العثور على الشرط الصحيح، ثم يتم إرجاع القيمة المقابلة.**  
📌 **إذا لم يتحقق أي شرط، يتم تنفيذ `ELSE` (اختياري، وإذا لم يوجد `ELSE` سيتم إرجاع `NULL`).**

---

### ✅ **`CASE` بسيط (`CASE column_name WHEN ... THEN ...`)**

```sql
SELECT column_name,  
       CASE column_name  
           WHEN value1 THEN result1  
           WHEN value2 THEN result2  
           ELSE default_result  
       END AS alias_name  
FROM table_name;
```

📌 **يُستخدم عندما تكون المقارنة مع قيمة واحدة فقط.**

---

## 🔹 **أمثلة عملية على `CASE`**

### 🗄️ **جدول `employees` (الموظفون)**

|emp_id|name|department_id|salary|
|---|---|---|---|
|1|Ali|1|5000|
|2|Sara|2|7000|
|3|Omar|3|6000|
|4|Huda|1|8000|

---

### 🎯 **1️⃣ استخدام `CASE` لتصنيف الرواتب إلى فئات**

```sql
SELECT name, salary,  
       CASE  
           WHEN salary < 6000 THEN 'Low'  
           WHEN salary BETWEEN 6000 AND 7500 THEN 'Medium'  
           ELSE 'High'  
       END AS salary_category  
FROM employees;
```

🔹 **النتيجة:**

|name|salary|salary_category|
|---|---|---|
|Ali|5000|Low|
|Sara|7000|Medium|
|Omar|6000|Medium|
|Huda|8000|High|

📌 **يتم تصنيف الرواتب إلى `Low`, `Medium`, و `High` بناءً على قيم `salary`**.

---

### 🎯 **2️⃣ استخدام `CASE` لتحويل `department_id` إلى أسماء الأقسام**

```sql
SELECT name, department_id,  
       CASE department_id  
           WHEN 1 THEN 'IT'  
           WHEN 2 THEN 'HR'  
           WHEN 3 THEN 'Marketing'  
           ELSE 'Unknown'  
       END AS department_name  
FROM employees;
```

🔹 **النتيجة:**

|name|department_id|department_name|
|---|---|---|
|Ali|1|IT|
|Sara|2|HR|
|Omar|3|Marketing|
|Huda|1|IT|

📌 **يتم استبدال `department_id` باسم القسم الفعلي**.

---

### 🎯 **3️⃣ استخدام `CASE` مع `ORDER BY` لتحديد الأولوية**

```sql
SELECT name, salary  
FROM employees  
ORDER BY  
       CASE  
           WHEN salary < 6000 THEN 1  
           WHEN salary BETWEEN 6000 AND 7500 THEN 2  
           ELSE 3  
       END;
```

📌 **يتم ترتيب البيانات بحيث تكون الرواتب `Low` أولاً، ثم `Medium`، ثم `High`**.

---

### 🎯 **4️⃣ استخدام `CASE` مع `UPDATE` لتحديث القيم بناءً على شرط**

```sql
UPDATE employees  
SET salary =  
       CASE  
           WHEN salary < 6000 THEN salary + 500  
           WHEN salary BETWEEN 6000 AND 7500 THEN salary + 1000  
           ELSE salary + 1500  
       END;
```

📌 **يتم تعديل الراتب لكل موظف بناءً على فئته**.

---

## 🏆 **ملخص سريع عن `CASE`**

|الاستخدام|التفاصيل|
|---|---|
|**`CASE` مع `SELECT`**|عرض بيانات مختلفة بناءً على شروط معينة.|
|**`CASE` مع `UPDATE`**|تعديل القيم بناءً على منطق شرطي.|
|**`CASE` مع `ORDER BY`**|ترتيب البيانات حسب أولويات مخصصة.|
|**`CASE` مع `GROUP BY`**|تصنيف البيانات في مجموعات شرطية.|

---

## 🎯 **الخلاصة**

- **`CASE`** يسمح بتنفيذ منطق شرطي داخل SQL، مثل `IF-ELSE` في البرمجة.
- **يمكن استخدامه في `SELECT`, `UPDATE`, `ORDER BY`, `GROUP BY`** وغيرهم.
- **يعمل بأسلوب تسلسلي، ويتوقف عند أول شرط صحيح**.

---


## Connect Me :

- https://github.com/foefvjfev33
- https://t.me/It_auf
- https://www.youtube.com/@IT_red-j9b
- https://www.linkedin.com/in/mohamed-auf-860537353/