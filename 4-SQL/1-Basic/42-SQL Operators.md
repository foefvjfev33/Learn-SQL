# 📌 **المعاملات في SQL (`SQL Operators`)**

## 🔹 **ما هي المعاملات في SQL؟**

🚀 **المعاملات (`Operators`)** هي **رموز خاصة تُستخدم لإجراء عمليات على القيم في استعلامات SQL**.  
✅ **تُستخدم في العمليات الحسابية، المنطقية، والمقارنات بين القيم**.  
✅ **تُستخدم في `SELECT`, `WHERE`, `JOIN`, `HAVING`, وغيرها من الجمل في SQL**.

---

## 🔹 **أنواع المعاملات في SQL**

📌 تنقسم المعاملات في SQL إلى عدة أنواع رئيسية:

|النوع|الوصف|
|---|---|
|**معاملات الحسابية (`Arithmetic Operators`)**|تُستخدم في العمليات الرياضية مثل الجمع والطرح.|
|**معاملات المقارنة (`Comparison Operators`)**|تُستخدم لمقارنة القيم في شروط `WHERE`.|
|**المعاملات المنطقية (`Logical Operators`)**|تُستخدم لدمج شروط متعددة في `WHERE`.|
|**معاملات البت (`Bitwise Operators`)**|تُستخدم لإجراء عمليات على مستوى البت.|
|**معاملات السلاسل النصية (`String Operators`)**|تُستخدم لمعالجة النصوص.|

---

## 🔹 **1️⃣ المعاملات الحسابية (`Arithmetic Operators`)**

📌 **تُستخدم لإجراء العمليات الرياضية على الأرقام.**

|المعامل|الوصف|مثال|
|---|---|---|
|`+`|الجمع|`SELECT 10 + 5;` → **15**|
|`-`|الطرح|`SELECT 10 - 5;` → **5**|
|`*`|الضرب|`SELECT 10 * 5;` → **50**|
|`/`|القسمة|`SELECT 10 / 5;` → **2**|
|`%`|باقي القسمة|`SELECT 10 % 3;` → **1**|

✅ **مثال عملي: إظهار الراتب بعد زيادة 10%**

```sql
SELECT name, salary, salary * 1.10 AS new_salary  
FROM employees;
```

---

## 🔹 **2️⃣ معاملات المقارنة (`Comparison Operators`)**

📌 **تُستخدم في جملة `WHERE` لمقارنة القيم.**

|المعامل|الوصف|مثال|
|---|---|---|
|`=`|يساوي|`WHERE salary = 5000`|
|`<>` أو `!=`|لا يساوي|`WHERE salary <> 5000`|
|`>`|أكبر من|`WHERE salary > 5000`|
|`<`|أصغر من|`WHERE salary < 5000`|
|`>=`|أكبر من أو يساوي|`WHERE salary >= 5000`|
|`<=`|أصغر من أو يساوي|`WHERE salary <= 5000`|
|`BETWEEN`|بين قيمتين|`WHERE salary BETWEEN 4000 AND 6000`|
|`IN`|موجود في قائمة|`WHERE department_id IN (1, 2, 3)`|
|`LIKE`|البحث عن نمط معين|`WHERE name LIKE 'A%'`|
|`IS NULL`|التحقق من `NULL`|`WHERE salary IS NULL`|

✅ **مثال عملي: البحث عن الموظفين الذين رواتبهم أكبر من 5000**

```sql
SELECT name, salary FROM employees WHERE salary > 5000;
```

---

## 🔹 **3️⃣ المعاملات المنطقية (`Logical Operators`)**

📌 **تُستخدم لدمج الشروط في `WHERE` أو `HAVING`.**

|المعامل|الوصف|مثال|
|---|---|---|
|`AND`|يتحقق من أن جميع الشروط صحيحة|`WHERE salary > 5000 AND department_id = 1`|
|`OR`|يتحقق من أن على الأقل شرطًا واحدًا صحيح|`WHERE salary > 5000 OR department_id = 1`|
|`NOT`|يعكس النتيجة|`WHERE NOT salary > 5000`|

✅ **مثال عملي: البحث عن الموظفين في القسم 1 أو الذين رواتبهم أعلى من 7000**

```sql
SELECT name, salary, department_id  
FROM employees  
WHERE department_id = 1 OR salary > 7000;
```

---

## 🔹 **4️⃣ معاملات البت (`Bitwise Operators`)**

📌 **تُستخدم لإجراء عمليات على مستوى البت، نادرًا ما تُستخدم في SQL.**

|المعامل|الوصف|مثال|
|---|---|---|
|`&`|AND بت|`SELECT 5 & 3;` → **1**|
|`|`|OR بت|
|`^`|XOR بت|`SELECT 5 ^ 3;` → **6**|

---

## 🔹 **5️⃣ معاملات النصوص (`String Operators`)**

📌 **تُستخدم للعمل على النصوص (`VARCHAR`, `TEXT`).**

|المعامل|الوصف|مثال|
|---|---|---|
|`+`|دمج النصوص (`SQL Server`)|`SELECT 'Hello' + ' World';` → **Hello World**|
|`||`|

✅ **مثال عملي: دمج الاسم الأول واسم العائلة في عمود واحد**

```sql
SELECT first_name + ' ' + last_name AS full_name  
FROM employees;
```

---

## 🏆 **ملخص سريع عن المعاملات في SQL**

|النوع|المعاملات|الاستخدام|
|---|---|---|
|**حسابية**|`+`, `-`, `*`, `/`, `%`|العمليات الرياضية|
|**مقارنة**|`=`, `<>`, `>`, `<`, `>=`, `<=`, `BETWEEN`, `IN`, `LIKE`|المقارنات في `WHERE`|
|**منطقية**|`AND`, `OR`, `NOT`|دمج الشروط|
|**بتية**|`&`, `|`,` ^`|
|**نصوص**|`+`, `||

---

## 🎯 **الخلاصة**

- **المعاملات (`Operators`) تُستخدم في العمليات الحسابية، المقارنات، الشروط المنطقية، والتعامل مع النصوص**.
- **`Arithmetic Operators` تُستخدم لإجراء العمليات الحسابية**.
- **`Comparison Operators` تُستخدم لمقارنة القيم في `WHERE`**.
- **`Logical Operators` تُستخدم لدمج الشروط**.
- **`String Operators` تُستخدم لمعالجة النصوص**.

---


## Connect Me :

- https://github.com/foefvjfev33
- https://t.me/It_auf
- https://www.youtube.com/@IT_red-j9b
- https://www.linkedin.com/in/mohamed-auf-860537353/