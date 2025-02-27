# 📌 **SQL CREATE TABLE Statement**

## 🔹 **ما هي جملة `CREATE TABLE` في SQL؟**

🚀 **تُستخدم جملة `CREATE TABLE` لإنشاء جدول جديد في قاعدة البيانات.**  
✅ **الجدول هو هيكل أساسي لتخزين البيانات في قاعدة البيانات، ويتكون من صفوف وأعمدة.**

---

## 🔹 **1️⃣ الصيغة الأساسية لجملة `CREATE TABLE`**

📌 **الصيغة الأساسية لإنشاء جدول جديد هي:**

```sql
CREATE TABLE table_name (
   column1 datatype [constraint],
   column2 datatype [constraint],
   ...
);
```

✅ **في هذه الصيغة:**

- **`table_name`** هو اسم الجدول الذي تريد إنشاءه.
- **`column1`, `column2`, ...** هي أسماء الأعمدة في الجدول.
- **`datatype`** هو نوع البيانات الذي ستخزنه في العمود.
- **`constraint`** (اختياري) هي قيود يمكن وضعها على الأعمدة مثل `NOT NULL`, `PRIMARY KEY`, `FOREIGN KEY`, إلخ.

---

## 🔹 **2️⃣ مثال عملي على إنشاء جدول**

📌 **مثال: إنشاء جدول باسم `employees` لتخزين معلومات الموظفين مثل الاسم، والعمر، والراتب:**

```sql
CREATE TABLE employees (
    employee_id INT PRIMARY KEY,
    first_name VARCHAR(50),
    last_name VARCHAR(50),
    age INT,
    salary DECIMAL(10, 2)
);
```

✅ **في هذا المثال:**

- **`employee_id`** هو معرف الموظف من نوع `INT` ويتم تحديده كـ `PRIMARY KEY` (أي أنه يجب أن يكون فريدًا وغير فارغ).
- **`first_name`** و **`last_name`** هما أسماء الموظفين من نوع `VARCHAR(50)` أي نص يصل إلى 50 حرفًا.
- **`age`** هو عمر الموظف من نوع `INT`.
- **`salary`** هو الراتب من نوع `DECIMAL(10, 2)` ويعني أن الراتب يمكن أن يتكون من 10 أرقام مع دقة تصل إلى خانتين عشريتين.

---

## 🔹 **3️⃣ أنواع البيانات (`Data Types`) في SQL**

📌 **عند تحديد نوع البيانات لكل عمود في الجدول، يمكن استخدام العديد من الأنواع مثل:**

|**النوع**|**الوصف**|
|---|---|
|`INT`|للأعداد الصحيحة.|
|`VARCHAR(n)`|لتخزين النصوص مع تحديد الحد الأقصى للطول (n).|
|`DECIMAL(p, s)`|للأعداد العشرية مع تحديد الدقة (p) وعدد المنازل العشرية (s).|
|`DATE`|لتخزين التاريخ.|
|`DATETIME`|لتخزين التاريخ والوقت.|
|`BOOLEAN`|لتخزين القيم الصحيحة والخاطئة (`TRUE` أو `FALSE`).|

---

## 🔹 **4️⃣ إضافة قيود (`Constraints`) على الأعمدة**

📌 **يمكنك إضافة قيود لضمان صحة البيانات في الأعمدة، مثل:**

- **`PRIMARY KEY`**: لتحديد العمود كمفتاح رئيسي يجب أن يحتوي على قيم فريدة وغير فارغة.
- **`NOT NULL`**: لضمان أن العمود لا يحتوي على قيم فارغة.
- **`UNIQUE`**: لضمان أن القيم في العمود فريدة.
- **`FOREIGN KEY`**: لتحديد علاقة بين الجداول.

✅ **مثال: إنشاء جدول مع قيود**

```sql
CREATE TABLE orders (
    order_id INT PRIMARY KEY,
    order_date DATE NOT NULL,
    customer_id INT,
    amount DECIMAL(10, 2) NOT NULL,
    FOREIGN KEY (customer_id) REFERENCES customers(customer_id)
);
```

🔹 **في هذا المثال:**

- **`order_id`** هو المفتاح الرئيسي.
- **`order_date`** لا يمكن أن يكون فارغًا.
- **`amount`** لا يمكن أن يكون فارغًا.
- **`FOREIGN KEY`** يحدد أن العمود `customer_id` يرتبط بالعمود `customer_id` في جدول `customers`.

---

## 🔹 **5️⃣ إضافة عمود جديد إلى جدول موجود**

📌 **لإضافة عمود جديد إلى جدول موجود، استخدم جملة `ALTER TABLE` مع `ADD`**

```sql
ALTER TABLE table_name  
ADD column_name datatype;
```

✅ **مثال: إضافة عمود `email` إلى جدول `employees`**

```sql
ALTER TABLE employees  
ADD email VARCHAR(100);
```

---

## 🏆 **ملخص سريع عن `CREATE TABLE` في SQL**

|العملية|الأمر المستخدم|الوصف|
|---|---|---|
|**إنشاء جدول جديد**|`CREATE TABLE table_name (column1 datatype, column2 datatype, ...);`|لإنشاء جدول جديد مع الأعمدة.|
|**إضافة قيد `PRIMARY KEY`**|`PRIMARY KEY (column_name)`|تحديد عمود كمفتاح رئيسي.|
|**إضافة قيد `FOREIGN KEY`**|`FOREIGN KEY (column_name) REFERENCES other_table (other_column)`|تحديد علاقة بين الجداول.|
|**إضافة عمود جديد**|`ALTER TABLE table_name ADD column_name datatype;`|إضافة عمود جديد إلى جدول موجود.|

---

## 🎯 **الخلاصة**

- **`CREATE TABLE` تُستخدم لإنشاء جدول جديد في SQL**.
- **تحديد أنواع البيانات والقيود يعد أمرًا مهمًا لضمان سلامة البيانات.**
- **يمكنك إضافة أعمدة جديدة أو تعديل الجداول باستخدام `ALTER TABLE`.**

---


## Connect Me :

- https://github.com/foefvjfev33
- https://t.me/It_auf
- https://www.youtube.com/@IT_red-j9b
- https://www.linkedin.com/in/mohamed-auf-860537353/