في **SQL**، تُستخدم **`TOP` و `LIMIT` و `FETCH FIRST` و `ROWNUM`** لتحديد عدد الصفوف التي يتم إرجاعها من استعلام `SELECT`. تختلف الصياغة حسب نظام قواعد البيانات (DBMS) المستخدم.

---

## 🔹 **1. استخدام `TOP` (في SQL Server)**

في **SQL Server**، تُستخدم `TOP` لتحديد عدد معين من الصفوف في نتيجة الاستعلام.

### ✅ **مثال: جلب أول 3 فواكه من الجدول**

```sql
SELECT TOP 3 * FROM fruits;
```

🔹 سيتم إرجاع **أول 3 صفوف** من الجدول `fruits`، حسب الترتيب الافتراضي.

### ✅ **استخدام `TOP` مع النسبة المئوية**

يمكنك إرجاع نسبة مئوية من الصفوف بدلاً من عدد ثابت:

```sql
SELECT TOP 50 PERCENT * FROM fruits;
```

🔹 هذا يُرجع **50% من الصفوف** في الجدول.

---

## 🔹 **2. استخدام `LIMIT` (في MySQL, PostgreSQL, SQLite)**

في **MySQL و PostgreSQL و SQLite**، يتم استخدام `LIMIT` لتحديد عدد الصفوف المُرجعة.

### ✅ **مثال: جلب أول 3 صفوف**

```sql
SELECT * FROM fruits LIMIT 3;
```

🔹 يتم جلب **أول 3 صفوف** فقط.

### ✅ **استخدام `LIMIT` مع `OFFSET`**

يمكنك تخطي عدد معين من الصفوف باستخدام `OFFSET`:

```sql
SELECT * FROM fruits LIMIT 3 OFFSET 2;
```

🔹 **يتم تخطي أول صفين، ثم جلب 3 صفوف بعدهما**.

---

## 🔹 **3. استخدام `FETCH FIRST` (في Oracle, SQL Server 2012+)**

في **Oracle 12c+ و SQL Server 2012+**، يمكنك استخدام `FETCH FIRST` لتحديد عدد الصفوف.

### ✅ **مثال: جلب أول 3 صفوف**

```sql
SELECT * FROM fruits FETCH FIRST 3 ROWS ONLY;
```

🔹 هذا مشابه لـ `LIMIT` ولكنه يستخدم في أنظمة مثل **Oracle**.

### ✅ **استخدام `FETCH FIRST` مع `OFFSET`**

```sql
SELECT * FROM fruits OFFSET 2 ROWS FETCH FIRST 3 ROWS ONLY;
```

🔹 **يتم تخطي أول صفين، ثم جلب 3 صفوف بعدهما**.

---

## 🔹 **4. استخدام `ROWNUM` (في Oracle قبل الإصدار 12c)**

في **Oracle** قبل الإصدار **12c**، كان يتم استخدام `ROWNUM` لتحديد عدد الصفوف.

### ✅ **مثال: جلب أول 3 صفوف**

```sql
SELECT * FROM fruits WHERE ROWNUM <= 3;
```

🔹 يتم جلب **أول 3 صفوف** فقط.

⚠️ **مشكلة `ROWNUM`**:  
لا يمكنك استخدام `ROWNUM` مباشرة مع `ORDER BY`، لأن `ROWNUM` يتم حسابه **قبل الفرز**.

✅ **الحل:** استخدم استعلامًا فرعيًا:

```sql
SELECT * FROM (SELECT * FROM fruits ORDER BY quantity DESC) WHERE ROWNUM <= 3;
```

🔹 يتم فرز البيانات أولًا، ثم يتم تحديد أول 3 صفوف.

---

## 🛠 **الفرق بين `TOP` و `LIMIT` و `FETCH FIRST` و `ROWNUM`**

|الميزة|**TOP** (SQL Server)|**LIMIT** (MySQL, PostgreSQL, SQLite)|**FETCH FIRST** (Oracle, SQL Server 2012+)|**ROWNUM** (Oracle قديم)|
|---|---|---|---|---|
|**تحديد عدد الصفوف**|✅ `TOP n`|✅ `LIMIT n`|✅ `FETCH FIRST n ROWS ONLY`|✅ `WHERE ROWNUM <= n`|
|**تخطي الصفوف (OFFSET)**|❌ غير مدعوم|✅ `LIMIT n OFFSET x`|✅ `OFFSET x ROWS FETCH FIRST n ROWS ONLY`|❌ غير مدعوم مباشرة|
|**مدعوم في**|SQL Server|MySQL, PostgreSQL, SQLite|Oracle 12c+, SQL Server 2012+|Oracle قبل 12c|

---

## 🎯 **الخلاصة**

- إذا كنت تستخدم **SQL Server** ➝ استخدم `TOP`.
- إذا كنت تستخدم **MySQL, PostgreSQL, SQLite** ➝ استخدم `LIMIT`.
- إذا كنت تستخدم **Oracle 12c+ أو SQL Server 2012+** ➝ استخدم `FETCH FIRST`.
- إذا كنت تستخدم **Oracle قديمًا** ➝ استخدم `ROWNUM` (مع استعلام فرعي إذا كنت بحاجة إلى `ORDER BY`).


## Connect Me :

- https://github.com/foefvjfev33
- https://t.me/It_auf
- https://www.youtube.com/@IT_red-j9b
- https://www.linkedin.com/in/mohamed-auf-860537353/