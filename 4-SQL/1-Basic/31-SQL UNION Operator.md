# 📌 **`UNION` في SQL – دمج نتائج الاستعلامات**

## 🔹 **ما هو `UNION` في SQL؟**

يُستخدم **`UNION`** لدمج نتائج **استعلامين أو أكثر** وإرجاع **مجموعة نتائج موحدة** بدون تكرار.  
✅ **يجب أن يكون لكل الاستعلامات نفس عدد الأعمدة، بنفس الترتيب، وبنفس أنواع البيانات.**

---

## 🔹 **الصيغة العامة (`Syntax`)**

```sql
SELECT column1, column2 FROM table1  
UNION  
SELECT column1, column2 FROM table2;
```

📌 **يقوم `UNION` بإزالة التكرارات تلقائيًا، مما يجعل النتائج فريدة.**

---

## 🔹 **مثال عملي على `UNION`**

### 🗄️ **جدول `employees_2023` (الموظفون لعام 2023)**

|id|name|department|
|---|---|---|
|1|John|IT|
|2|Alice|HR|

### 🗄️ **جدول `employees_2024` (الموظفون لعام 2024)**

|id|name|department|
|---|---|---|
|2|Alice|HR|
|3|Bob|Finance|

🔹 **نريد دمج بيانات الموظفين من الجدولين دون تكرار.**

```sql
SELECT id, name, department FROM employees_2023  
UNION  
SELECT id, name, department FROM employees_2024;
```

🔹 **النتيجة:**

|id|name|department|
|---|---|---|
|1|John|IT|
|2|Alice|HR|
|3|Bob|Finance|

📌 **Alice تكررت في الجدولين، لكن `UNION` أزال التكرار تلقائيًا.**

---

## 🔹 **`UNION ALL` – دمج بدون إزالة التكرارات**

إذا كنت تريد **الحفاظ على التكرارات**، استخدم `UNION ALL`:

```sql
SELECT id, name, department FROM employees_2023  
UNION ALL  
SELECT id, name, department FROM employees_2024;
```

🔹 **النتيجة:**

|id|name|department|
|---|---|---|
|1|John|IT|
|2|Alice|HR|
|2|Alice|HR|
|3|Bob|Finance|

📌 **هنا لم يتم إزالة التكرار، وظهرت Alice مرتين.**

---

## 🔹 **`UNION` مع ترتيب النتائج (`ORDER BY`)**

```sql
SELECT id, name, department FROM employees_2023  
UNION  
SELECT id, name, department FROM employees_2024  
ORDER BY name;
```

📌 **`ORDER BY` يجب أن يكون بعد آخر استعلام، وليس بعد كل `SELECT`.**

---

## 🔹 **`UNION` مع تصفية النتائج (`WHERE`)**

```sql
SELECT id, name, department FROM employees_2023 WHERE department = 'IT'  
UNION  
SELECT id, name, department FROM employees_2024 WHERE department = 'IT';
```

📌 **يتم تطبيق `WHERE` داخل كل استعلام على حدة.**

---

## 🏆 **ملخص سريع عن `UNION`**

|الميزة|التفاصيل|
|---|---|
|**يُستخدم لدمج استعلامات متعددة**|يجب أن تحتوي على نفس الأعمدة بنفس الترتيب ونوع البيانات.|
|**`UNION` يزيل التكرارات تلقائيًا**|النتائج تكون فريدة.|
|**`UNION ALL` يحتفظ بالتكرارات**|أسرع في الأداء لأنه لا يحتاج إلى إزالة التكرارات.|
|**`ORDER BY` يُستخدم بعد `UNION`**|يجب أن يكون بعد آخر استعلام وليس كل استعلام.|

---

## 🎯 **الخلاصة**

- **`UNION`** يُستخدم لدمج نتائج استعلامات متعددة **مع إزالة التكرارات**.
- **`UNION ALL`** يُبقي على التكرارات **وهو أسرع أداءً**.
- **جميع الاستعلامات يجب أن تحتوي على نفس عدد الأعمدة ونوع البيانات**.
- **يمكن استخدام `ORDER BY` و `WHERE` مع `UNION` لتنظيم وتصفية النتائج**.

---


## Connect Me :

- https://github.com/foefvjfev33
- https://t.me/It_auf
- https://www.youtube.com/@IT_red-j9b
- https://www.linkedin.com/in/mohamed-auf-860537353/