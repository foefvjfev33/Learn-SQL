# 📌 **`JOIN` في SQL – شرح شامل**

تُستخدم **`JOIN`** في **SQL** لدمج البيانات من **جدولين أو أكثر** استنادًا إلى علاقة مشتركة بينهما.

---

## 🔹 **1. أنواع `JOIN` في SQL**

|النوع|الوظيفة|
|---|---|
|**`INNER JOIN`**|يُرجع فقط الصفوف التي تتطابق بين الجدولين.|
|**`LEFT JOIN` (أو `LEFT OUTER JOIN`)**|يُرجع جميع الصفوف من الجدول الأيسر، مع البيانات المطابقة من الجدول الأيمن (إن وجدت).|
|**`RIGHT JOIN` (أو `RIGHT OUTER JOIN`)**|يُرجع جميع الصفوف من الجدول الأيمن، مع البيانات المطابقة من الجدول الأيسر (إن وجدت).|
|**`FULL JOIN` (أو `FULL OUTER JOIN`)**|يُرجع جميع الصفوف من كلا الجدولين، مع البيانات المطابقة إن وجدت.|
|**`CROSS JOIN`**|يُنتج جميع التباديل الممكنة بين الجدولين (المُنتج الديكارتي).|
|**`SELF JOIN`**|يُستخدم لربط الجدول بنفسه.|

---

## 🔹 **2. `INNER JOIN` – الجلب المشترك**

🔸 **يجلب فقط الصفوف التي تحتوي على تطابق في كلا الجدولين.**

### ✅ **مثال: البحث عن الموظفين مع الأقسام الخاصة بهم**

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

📌 **إذا لم يكن هناك تطابق في `department_id` بين الجدولين، فلن يتم عرض الصف.**

---

## 🔹 **3. `LEFT JOIN` – جلب جميع الصفوف من الجدول الأيسر**

🔸 **يجلب جميع الصفوف من الجدول الأيسر (`LEFT`)، حتى لو لم يكن هناك تطابق في الجدول الأيمن.**

### ✅ **مثال: إظهار جميع الموظفين حتى لو لم يكن لديهم قسم**

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

📌 **"Bob" ليس لديه `department_id` مطابق، لذلك يتم إرجاع `NULL` بدلاً من اسم القسم.**

---

## 🔹 **4. `RIGHT JOIN` – جلب جميع الصفوف من الجدول الأيمن**

🔸 **يجلب جميع الصفوف من الجدول الأيمن (`RIGHT`)، حتى لو لم يكن هناك تطابق في الجدول الأيسر.**

### ✅ **مثال: البحث عن جميع الأقسام حتى لو لم يكن بها موظفون**

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

## 🔹 **5. `FULL JOIN` – جلب جميع الصفوف من كلا الجدولين**

🔸 **يجلب جميع الصفوف من الجدولين، مع عرض `NULL` إذا لم يكن هناك تطابق.**

### ✅ **مثال: البحث عن جميع الموظفين والأقسام**

```sql
SELECT employees.name, departments.department_name  
FROM employees  
FULL JOIN departments ON employees.department_id = departments.id;
```

🔹 **النتيجة:**

|name|department_name|
|---|---|
|John|IT|
|Alice|HR|
|Bob|NULL|
|NULL|Finance|

📌 **يتم عرض جميع الموظفين والأقسام، حتى لو لم يكن هناك تطابق.**

---

## 🔹 **6. `CROSS JOIN` – ضرب ديكارتي لجميع الصفوف**

🔸 **ينتج جميع التباديل الممكنة بين الجدولين (جدول ضرب ديكارتي).**

### ✅ **مثال: إنشاء جميع التوليفات الممكنة بين الموظفين والمشاريع**

```sql
SELECT employees.name, projects.project_name  
FROM employees  
CROSS JOIN projects;
```

🔹 **إذا كان هناك 3 موظفين و 2 مشاريع، فستكون النتيجة 3 × 2 = 6 صفوف.**

---

## 🔹 **7. `SELF JOIN` – ربط الجدول بنفسه**

🔸 **يُستخدم عند مقارنة الصفوف داخل الجدول نفسه، مثل البحث عن المدير لكل موظف.**

### ✅ **مثال: البحث عن المدير لكل موظف**

```sql
SELECT e1.name AS "Employee", e2.name AS "Manager"  
FROM employees AS e1  
LEFT JOIN employees AS e2 ON e1.manager_id = e2.id;
```

🔹 **النتيجة:**

|Employee|Manager|
|---|---|
|John|Alice|
|Bob|John|

📌 **يتم ربط الجدول بنفسه لمقارنة الموظفين بمدرائهم.**

---

## 🏆 **ملخص سريع عن `JOIN` في SQL**

|النوع|الوظيفة|
|---|---|
|`INNER JOIN`|يُرجع فقط الصفوف المتطابقة بين الجدولين.|
|`LEFT JOIN`|يُرجع جميع الصفوف من الجدول الأيسر مع البيانات المطابقة من الجدول الأيمن.|
|`RIGHT JOIN`|يُرجع جميع الصفوف من الجدول الأيمن مع البيانات المطابقة من الجدول الأيسر.|
|`FULL JOIN`|يُرجع جميع الصفوف من كلا الجدولين، حتى لو لم يكن هناك تطابق.|
|`CROSS JOIN`|يُنتج جميع التباديل الممكنة بين الجدولين.|
|`SELF JOIN`|يُستخدم لربط الجدول بنفسه.|

---

## 🎯 **الخلاصة**

- **`INNER JOIN`** يُستخدم لجلب **التطابقات فقط** بين الجدولين.
- **`LEFT JOIN`** يُظهر جميع الصفوف من الجدول الأيسر، حتى لو لم يكن هناك تطابق.
- **`RIGHT JOIN`** يُظهر جميع الصفوف من الجدول الأيمن، حتى لو لم يكن هناك تطابق.
- **`FULL JOIN`** يُظهر جميع الصفوف من كلا الجدولين، حتى لو لم يكن هناك تطابق.
- **`CROSS JOIN`** يُستخدم لإنشاء جميع **التباديل الممكنة** بين الصفوف.
- **`SELF JOIN`** يُستخدم عند الحاجة لمقارنة بيانات داخل الجدول نفسه.

---


## Connect Me :

- https://github.com/foefvjfev33
- https://t.me/It_auf
- https://www.youtube.com/@IT_red-j9b
- https://www.linkedin.com/in/mohamed-auf-860537353/