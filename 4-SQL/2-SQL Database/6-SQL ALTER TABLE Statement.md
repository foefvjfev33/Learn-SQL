# 📌 **SQL ALTER TABLE Statement**

## 🔹 **ما هي جملة `ALTER TABLE` في SQL؟**

🚀 **تُستخدم جملة `ALTER TABLE` لتعديل هيكل جدول موجود في قاعدة البيانات.**  
✅ **يمكنك إضافة أو تعديل أو حذف الأعمدة داخل الجدول باستخدام هذه الجملة.**  
✅ **أي تغييرات تتم على هيكل الجدول باستخدام `ALTER TABLE` تؤثر مباشرةً على تصميم الجدول في قاعدة البيانات.**

---

## 🔹 **1️⃣ الصيغة الأساسية لجملة `ALTER TABLE`**

📌 **الصيغة الأساسية لتعديل الجدول باستخدام `ALTER TABLE`:**

```sql
ALTER TABLE table_name action;
```

✅ **في هذه الصيغة:**

- **`table_name`** هو اسم الجدول الذي ترغب في تعديله.
- **`action`** هو الإجراء الذي تريد تنفيذه على الجدول (مثل إضافة عمود، تعديل عمود، حذف عمود، إلخ).

---

## 🔹 **2️⃣ إضافة عمود جديد إلى جدول (`ADD`)**

📌 **إذا أردت إضافة عمود جديد إلى جدول موجود، يمكنك استخدام جملة `ADD`**

✅ **مثال: إضافة عمود `email` من نوع `VARCHAR(100)` إلى جدول `employees`**

```sql
ALTER TABLE employees
ADD email VARCHAR(100);
```

🔹 **يتم إضافة عمود جديد باسم `email` إلى جدول `employees` ويستطيع تخزين نصوص تصل إلى 100 حرف.**

---

## 🔹 **3️⃣ تعديل عمود موجود (`MODIFY` أو `CHANGE`)**

📌 **إذا أردت تعديل خصائص عمود موجود، مثل تغيير نوع البيانات أو تغيير الحجم، يمكنك استخدام جملة `MODIFY` أو `CHANGE` حسب النظام المستخدم.**

- **في MySQL، نستخدم `MODIFY`.**
- **في SQL Server، نستخدم `ALTER COLUMN`.**

✅ **مثال: تعديل عمود `age` ليصبح نوعه `DECIMAL` بدلاً من `INT`**

```sql
ALTER TABLE employees
MODIFY age DECIMAL(5,2);
```

🔹 **سيتم تعديل عمود `age` ليقبل أرقام عشرية بدلًا من الأعداد الصحيحة.**

---

## 🔹 **4️⃣ تغيير اسم العمود (`RENAME COLUMN`)**

📌 **إذا أردت تغيير اسم عمود في جدول، يمكنك استخدام جملة `RENAME COLUMN` (في بعض أنظمة SQL مثل PostgreSQL).**

✅ **مثال: تغيير اسم العمود `email` إلى `contact_email` في جدول `employees`**

```sql
ALTER TABLE employees
RENAME COLUMN email TO contact_email;
```

🔹 **يتم تغيير اسم العمود من `email` إلى `contact_email`.**

---

## 🔹 **5️⃣ حذف عمود من جدول (`DROP COLUMN`)**

📌 **إذا أردت حذف عمود من جدول موجود، يمكنك استخدام جملة `DROP COLUMN`**

✅ **مثال: حذف العمود `email` من جدول `employees`**

```sql
ALTER TABLE employees
DROP COLUMN email;
```

🔹 **سيتم حذف العمود `email` من جدول `employees`.**

---

## 🔹 **6️⃣ إعادة ترتيب الأعمدة في الجدول (محدود لبعض الأنظمة)**

📌 **في بعض أنظمة SQL مثل MySQL، يمكن استخدام `ALTER TABLE` لإعادة ترتيب الأعمدة.**  
✅ **ملاحظة: معظم أنظمة SQL لا تدعم إعادة ترتيب الأعمدة مباشرة باستخدام `ALTER TABLE`، ويمكن فقط تعديل الأعمدة أو إضافتها وحذفها.**

---

## 🏆 **ملخص سريع عن `ALTER TABLE` في SQL**

|العملية|الأمر المستخدم|الوصف|
|---|---|---|
|**إضافة عمود جديد**|`ALTER TABLE table_name ADD column_name datatype;`|إضافة عمود جديد إلى الجدول.|
|**تعديل عمود موجود**|`ALTER TABLE table_name MODIFY column_name new_datatype;` (في MySQL)|تعديل نوع البيانات لعمود موجود.|
|**تغيير اسم عمود**|`ALTER TABLE table_name RENAME COLUMN old_name TO new_name;` (في PostgreSQL)|تغيير اسم العمود في الجدول.|
|**حذف عمود**|`ALTER TABLE table_name DROP COLUMN column_name;`|حذف عمود من الجدول.|

---

## 🎯 **الخلاصة**

- **`ALTER TABLE` تُستخدم لتعديل هيكل الجدول مثل إضافة عمود أو تعديله أو حذفه.**
- **تدعم بعض أنظمة SQL مثل PostgreSQL إعادة تسمية الأعمدة، بينما لا تدعم معظم الأنظمة ذلك بشكل مباشر.**
- **يجب الحذر عند تعديل الجداول في بيئات الإنتاج لأن التغييرات قد تؤثر على البيانات الموجودة أو على التطبيقات التي تعتمد على هيكل الجدول.**

---


## Connect Me :

- https://github.com/foefvjfev33
- https://t.me/It_auf
- https://www.youtube.com/@IT_red-j9b
- https://www.linkedin.com/in/mohamed-auf-860537353/