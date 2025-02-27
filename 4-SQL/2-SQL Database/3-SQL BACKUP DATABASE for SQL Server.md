# 📌 **SQL BACKUP DATABASE for SQL Server**

## 🔹 **ما هي جملة `BACKUP DATABASE` في SQL Server؟**

🚀 **تُستخدم جملة `BACKUP DATABASE` لإنشاء نسخة احتياطية (Backup) من قاعدة بيانات في SQL Server.**  
✅ **النسخة الاحتياطية تعتبر من أهم العمليات لحماية البيانات من الفقدان أو التلف.**  
✅ **يمكنك تخزين النسخة الاحتياطية في ملف محلي أو على خادم خارجي.**

---

## 🔹 **1️⃣ الصيغة الأساسية لجملة `BACKUP DATABASE`**

📌 **الصيغة الأساسية لإنشاء نسخة احتياطية من قاعدة بيانات في SQL Server**:

```sql
BACKUP DATABASE database_name  
TO DISK = 'path_to_backup_file.bak';
```

✅ **مثال عملي: أخذ نسخة احتياطية من قاعدة بيانات باسم `companyDB`**

```sql
BACKUP DATABASE companyDB  
TO DISK = 'C:\Backups\companyDB.bak';
```

🔹 **ستقوم هذه العملية بإنشاء نسخة احتياطية من قاعدة البيانات `companyDB` في الملف `companyDB.bak` على المسار المحدد.**

---

## 🔹 **2️⃣ أخذ نسخة احتياطية مع خيارات إضافية**

📌 **يمكنك تحديد خيارات إضافية أثناء أخذ النسخة الاحتياطية مثل إضافة وصف أو إجراء النسخ بشكل جزئي.**

|الخيار|الوصف|المثال|
|---|---|---|
|`WITH FORMAT`|تنسيق النسخة الاحتياطية (إعادة الكتابة إذا كانت النسخة الاحتياطية موجودة مسبقًا).|`BACKUP DATABASE companyDB TO DISK = 'C:\Backups\companyDB.bak' WITH FORMAT;`|
|`WITH NOFORMAT`|الحفاظ على تنسيق النسخة السابقة وعدم إعادة الكتابة.|`BACKUP DATABASE companyDB TO DISK = 'C:\Backups\companyDB.bak' WITH NOFORMAT;`|
|`WITH INIT`|كتابة النسخة الاحتياطية من جديد في الملف الحالي.|`BACKUP DATABASE companyDB TO DISK = 'C:\Backups\companyDB.bak' WITH INIT;`|
|`WITH COPY_ONLY`|إنشاء نسخة احتياطية دون التأثير على سجل النسخ الاحتياطي المعتاد.|`BACKUP DATABASE companyDB TO DISK = 'C:\Backups\companyDB.bak' WITH COPY_ONLY;`|

---

## 🔹 **3️⃣ أخذ نسخة احتياطية جزئية أو من ملفات معينة**

📌 **في حال كان لديك ملفات أو مجموعات بيانات معينة ترغب في أخذ نسخة احتياطية منها فقط، يمكنك تحديدها.**

✅ **مثال: أخذ نسخة احتياطية من ملفات معينة في قاعدة البيانات**

```sql
BACKUP DATABASE companyDB  
FILE = 'companyDB_data'  
TO DISK = 'C:\Backups\companyDB_data.bak';
```

🔹 **يتم هنا تحديد ملف `companyDB_data` فقط من قاعدة البيانات `companyDB`.**

---

## 🔹 **4️⃣ استعادة النسخة الاحتياطية (`RESTORE DATABASE`)**

📌 **إذا كنت بحاجة إلى استعادة قاعدة البيانات من نسخة احتياطية، يمكنك استخدام جملة `RESTORE DATABASE`.**

✅ **مثال: استعادة قاعدة بيانات من نسخة احتياطية**

```sql
RESTORE DATABASE companyDB  
FROM DISK = 'C:\Backups\companyDB.bak';
```

🔹 **يتم استعادة قاعدة البيانات `companyDB` من النسخة الاحتياطية المخزنة في `companyDB.bak`.**

---

## 🔹 **5️⃣ النسخة الاحتياطية مع سجل المعاملات (`Transaction Log`)**

📌 **من الممكن أخذ نسخة احتياطية من سجل المعاملات لضمان استعادة البيانات بأدق مستوى من التغييرات.**

✅ **مثال: أخذ نسخة احتياطية من سجل المعاملات**

```sql
BACKUP LOG companyDB  
TO DISK = 'C:\Backups\companyDB_log.trn';
```

🔹 **يتم حفظ سجل المعاملات في `companyDB_log.trn`، وهذا يمكن أن يساعد في استعادة المعاملات بعد النسخة الاحتياطية الأخيرة.**

---

## 🏆 **ملخص سريع عن `BACKUP DATABASE` في SQL Server**

|العملية|الأمر المستخدم|الوصف|
|---|---|---|
|**أخذ نسخة احتياطية**|`BACKUP DATABASE database_name TO DISK = 'path_to_backup_file.bak';`|إنشاء نسخة احتياطية من قاعدة البيانات|
|**خيارات النسخة الاحتياطية**|`WITH FORMAT`, `WITH INIT`, `WITH COPY_ONLY`|خيارات لتنسيق النسخة الاحتياطية|
|**أخذ نسخة احتياطية من ملف معين**|`BACKUP DATABASE database_name FILE = 'file_name' TO DISK = 'path_to_backup_file.bak';`|أخذ نسخة احتياطية من ملف معين داخل قاعدة البيانات|
|**استعادة قاعدة البيانات**|`RESTORE DATABASE database_name FROM DISK = 'path_to_backup_file.bak';`|استعادة قاعدة البيانات من النسخة الاحتياطية|
|**أخذ نسخة احتياطية من سجل المعاملات**|`BACKUP LOG database_name TO DISK = 'path_to_log_file.trn';`|أخذ نسخة احتياطية من سجل المعاملات|

---

## 🎯 **الخلاصة**

- **`BACKUP DATABASE` تُستخدم لإنشاء نسخة احتياطية من قاعدة بيانات SQL Server.**
- **يمكنك تحديد خيارات إضافية مثل `WITH FORMAT` و `WITH INIT` حسب الحاجة.**
- **`RESTORE DATABASE` تُستخدم لاستعادة قاعدة البيانات من النسخة الاحتياطية.**
- **من المهم أيضًا أخذ نسخة احتياطية من سجل المعاملات باستخدام `BACKUP LOG` لضمان القدرة على الاستعادة الدقيقة.**

---


## Connect Me :

- https://github.com/foefvjfev33
- https://t.me/It_auf
- https://www.youtube.com/@IT_red-j9b
- https://www.linkedin.com/in/mohamed-auf-860537353/