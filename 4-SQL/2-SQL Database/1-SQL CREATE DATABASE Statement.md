# 📌 **SQL CREATE DATABASE Statement**

## 🔹 **ما هي جملة `CREATE DATABASE` في SQL؟**

🚀 **تُستخدم جملة `CREATE DATABASE` لإنشاء قاعدة بيانات جديدة في نظام إدارة قواعد البيانات (`DBMS`).**  
✅ **تُعتبر أول خطوة عند إنشاء نظام يعتمد على قاعدة بيانات**.  
✅ **يجب أن يكون لديك الصلاحيات المناسبة (`admin` أو `DBA`) لإنشاء قاعدة بيانات**.

---

## 🔹 **1️⃣ إنشاء قاعدة بيانات جديدة (`CREATE DATABASE`)**

📌 **الصيغة الأساسية لإنشاء قاعدة بيانات**:

```sql
CREATE DATABASE database_name;
```

✅ **مثال عملي: إنشاء قاعدة بيانات باسم `companyDB`**

```sql
CREATE DATABASE companyDB;
```

🔹 **عند تنفيذ هذا الأمر، سيتم إنشاء قاعدة بيانات جديدة باسم `companyDB`**.

---

## 🔹 **2️⃣ تحديد خيارات متقدمة عند إنشاء قاعدة البيانات**

📌 **بعض الأنظمة مثل `SQL Server` و`MySQL` تسمح بتحديد إعدادات مثل الترميز (`Collation`) والمسار (`File Location`).**

✅ **مثال: إنشاء قاعدة بيانات في `SQL Server` مع تحديد الترميز**

```sql
CREATE DATABASE companyDB  
COLLATE Latin1_General_CI_AI;
```

✅ **مثال: إنشاء قاعدة بيانات مع تحديد الموقع في `MySQL`**

```sql
CREATE DATABASE companyDB  
DEFAULT CHARACTER SET utf8mb4  
DEFAULT COLLATE utf8mb4_unicode_ci;
```

🔹 **هذا يضمن دعم الأحرف الخاصة واللغات المختلفة بشكل صحيح.**

---

## 🔹 **3️⃣ التحقق من وجود قاعدة البيانات قبل إنشائها (`IF NOT EXISTS`)**

📌 **لتجنب الخطأ إذا كانت قاعدة البيانات موجودة بالفعل، يمكن استخدام `IF NOT EXISTS`.**

✅ **مثال: إنشاء قاعدة بيانات فقط إذا لم تكن موجودة (`MySQL, PostgreSQL`):**

```sql
CREATE DATABASE IF NOT EXISTS companyDB;
```

🔹 **إذا كانت قاعدة البيانات `companyDB` موجودة مسبقًا، فلن يتم إنشاؤها مرة أخرى.**

---

## 🔹 **4️⃣ حذف قاعدة بيانات (`DROP DATABASE`)**

📌 **لحذف قاعدة بيانات نهائيًا، استخدم `DROP DATABASE`**  
⚠ **❌ تحذير: سيتم حذف جميع الجداول والبيانات بداخلها نهائيًا!**

✅ **مثال: حذف قاعدة البيانات `companyDB`**

```sql
DROP DATABASE companyDB;
```

---

## 🔹 **5️⃣ استخدام قاعدة بيانات (`USE DATABASE`)**

📌 **لتحديد قاعدة بيانات معينة للعمل عليها، استخدم `USE`**

✅ **مثال: تحديد قاعدة البيانات `companyDB` كقاعدة البيانات الحالية**

```sql
USE companyDB;
```

🔹 **بعد تنفيذ هذا الأمر، سيتم تنفيذ جميع استعلامات `SQL` التالية على قاعدة بيانات `companyDB`.**

---

## 🏆 **ملخص سريع عن `CREATE DATABASE` في SQL**

|العملية|الأمر المستخدم|
|---|---|
|**إنشاء قاعدة بيانات**|`CREATE DATABASE database_name;`|
|**إنشاء قاعدة بيانات مع الترميز**|`CREATE DATABASE database_name COLLATE utf8_general_ci;`|
|**إنشاء قاعدة بيانات إذا لم تكن موجودة**|`CREATE DATABASE IF NOT EXISTS database_name;`|
|**حذف قاعدة بيانات**|`DROP DATABASE database_name;`|
|**استخدام قاعدة بيانات**|`USE database_name;`|

---

## 🎯 **الخلاصة**

- **`CREATE DATABASE` تُستخدم لإنشاء قاعدة بيانات جديدة**.
- **`IF NOT EXISTS` تمنع الخطأ إذا كانت قاعدة البيانات موجودة مسبقًا**.
- **`DROP DATABASE` يحذف قاعدة البيانات نهائيًا**.
- **`USE database_name` تُستخدم لتحديد قاعدة البيانات النشطة**.

---


## Connect Me :

- https://github.com/foefvjfev33
- https://t.me/It_auf
- https://www.youtube.com/@IT_red-j9b
- https://www.linkedin.com/in/mohamed-auf-860537353/