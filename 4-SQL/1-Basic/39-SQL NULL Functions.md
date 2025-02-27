# 📌 **دوال `NULL` في SQL – التعامل مع القيم الفارغة**

## 🔹 **ما هو `NULL` في SQL؟**

🚀 في SQL، **`NULL`** تعني **عدم وجود قيمة** وليس "صفر" أو "سلسلة فارغة".  
✅ **تحتاج إلى دوال خاصة لمعالجة `NULL`** لأن العمليات العادية لا تعمل معها كما هو متوقع.  
✅ **`NULL` تُستخدم لتمثيل البيانات المفقودة أو غير المعروفة**.

---

## 🔹 **أهم دوال التعامل مع `NULL` في SQL**

|الدالة|الوصف|
|---|---|
|**`IS NULL`**|يستخدم لفحص ما إذا كانت القيمة `NULL`.|
|**`IS NOT NULL`**|يستخدم لفحص ما إذا كانت القيمة ليست `NULL`.|
|**`COALESCE()`**|يعيد أول قيمة غير `NULL` من قائمة القيم.|
|**`NULLIF()`**|يعيد `NULL` إذا كانت القيمتين متساويتين، وإلا يعيد القيمة الأولى.|
|**`IFNULL()`** (في MySQL)|يعيد القيمة البديلة إذا كانت القيمة `NULL`.|
|**`NVL()`** (في Oracle)|يشبه `IFNULL()`, يعيد قيمة بديلة عند وجود `NULL`.|

---

## 🔹 **1️⃣ `IS NULL` و `IS NOT NULL`**

📌 **تُستخدم لفحص القيم الفارغة (`NULL`)**.

```sql
SELECT * FROM employees WHERE salary IS NULL;
```

🔹 **يعرض جميع الموظفين الذين لا يملكون راتبًا مسجلًا (`NULL`).**

```sql
SELECT * FROM employees WHERE salary IS NOT NULL;
```

🔹 **يعرض جميع الموظفين الذين لديهم راتب مسجل (ليس `NULL`).**

---

## 🔹 **2️⃣ `COALESCE()` – استبدال `NULL` بأول قيمة غير فارغة**

📌 **تعيد أول قيمة غير `NULL` من قائمة القيم.**

```sql
SELECT name, COALESCE(salary, 0) AS salary FROM employees;
```

🔹 **إذا كان `salary` فارغًا (`NULL`)، سيتم إرجاع `0` بدلاً منه.**

|name|salary|
|---|---|
|Ali|5000|
|Sara|NULL → 0|
|Omar|6000|

---

## 🔹 **3️⃣ `NULLIF()` – إرجاع `NULL` إذا كانت القيم متساوية**

📌 **إذا كانت القيمتان متساويتين، تعيد `NULL`، وإلا تعيد القيمة الأولى.**

```sql
SELECT name, NULLIF(salary, 5000) AS new_salary FROM employees;
```

🔹 **إذا كان `salary = 5000`، سيتم تحويله إلى `NULL`، وإلا فسيبقى كما هو.**

|name|salary|new_salary|
|---|---|---|
|Ali|5000|NULL|
|Sara|7000|7000|

---

## 🔹 **4️⃣ `IFNULL()` (MySQL) و `NVL()` (Oracle) – تعيين قيمة بديلة عند `NULL`**

📌 **إذا كانت القيمة `NULL`، يتم استبدالها بالقيمة التي نحددها.**

### ✅ **في MySQL (`IFNULL()`)**

```sql
SELECT name, IFNULL(salary, 0) AS salary FROM employees;
```

### ✅ **في Oracle (`NVL()`)**

```sql
SELECT name, NVL(salary, 0) AS salary FROM employees;
```

🔹 **يتم استبدال أي `NULL` بـ `0` في العمود `salary`.**

---

## 🏆 **ملخص سريع عن دوال `NULL`**

|الدالة|الوظيفة|
|---|---|
|**`IS NULL`**|العثور على القيم الفارغة (`NULL`).|
|**`IS NOT NULL`**|العثور على القيم غير الفارغة.|
|**`COALESCE(val1, val2, ...)`**|إرجاع أول قيمة غير `NULL`.|
|**`NULLIF(val1, val2)`**|إرجاع `NULL` إذا كانت القيمتان متساويتين.|
|**`IFNULL(val, default)` (MySQL)**|استبدال `NULL` بقيمة محددة.|
|**`NVL(val, default)` (Oracle)**|نفس وظيفة `IFNULL()`.|

---

## 🎯 **الخلاصة**

- **`NULL` يعني عدم وجود قيمة وليس "0" أو سلسلة فارغة**.
- **`IS NULL` و `IS NOT NULL` تُستخدم لاختبار `NULL`**.
- **`COALESCE()` تُستخدم لاختيار أول قيمة غير `NULL`**.
- **`NULLIF()` تُستخدم لإرجاع `NULL` إذا كانت القيم متساوية**.
- **`IFNULL()` و `NVL()` تُستخدم لاستبدال `NULL` بقيمة بديلة**.

---


## Connect Me :

- https://github.com/foefvjfev33
- https://t.me/It_auf
- https://www.youtube.com/@IT_red-j9b
- https://www.linkedin.com/in/mohamed-auf-860537353/