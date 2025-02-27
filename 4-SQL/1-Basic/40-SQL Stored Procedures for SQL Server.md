# 📌 **الإجراءات المخزنة (Stored Procedures) في SQL Server**

## 🔹 **ما هي الإجراءات المخزنة (`Stored Procedures`)؟**

🚀 **الإجراء المخزن (`Stored Procedure`)** هو **مجموعة من استعلامات SQL محفوظة في قاعدة البيانات، يمكن استدعاؤها وتنفيذها عند الحاجة**.  
✅ **يُستخدم لتحسين الأداء وتقليل التكرار**.  
✅ **يقلل الحمل على الشبكة لأنه يتم تنفيذ الكود داخل SQL Server مباشرةً**.  
✅ **يوفر أمانًا لأن المستخدمين يمكنهم استدعاء الإجراء بدون الحاجة إلى رؤية كود SQL الداخلي**.

---

## 🔹 **إنشاء إجراء مخزن (`CREATE PROCEDURE`)**

📌 **الصيغة الأساسية لإنشاء إجراء مخزن بسيط بدون معاملات (`Parameters`)**:

```sql
CREATE PROCEDURE procedure_name  
AS  
BEGIN  
    -- SQL Statements  
END;
```

📌 **الصيغة لإنشاء إجراء مخزن مع معاملات (`Parameters`)**:

```sql
CREATE PROCEDURE procedure_name  
    @param1 datatype,  
    @param2 datatype  
AS  
BEGIN  
    -- SQL Statements  
END;
```

---

## 🔹 **1️⃣ إنشاء إجراء مخزن بسيط بدون معاملات**

✅ **مثال: إنشاء إجراء يعرض جميع الموظفين (`employees`)**

```sql
CREATE PROCEDURE GetAllEmployees  
AS  
BEGIN  
    SELECT * FROM employees;  
END;
```

📌 **لتنفيذ الإجراء المخزن (`EXEC` أو `EXECUTE`)**

```sql
EXEC GetAllEmployees;
```

---

## 🔹 **2️⃣ إنشاء إجراء مخزن مع معاملات (`Parameters`)**

✅ **مثال: إنشاء إجراء لإحضار موظف حسب `emp_id`**

```sql
CREATE PROCEDURE GetEmployeeById  
    @emp_id INT  
AS  
BEGIN  
    SELECT * FROM employees WHERE emp_id = @emp_id;  
END;
```

📌 **لتنفيذ الإجراء وتمرير قيمة (`emp_id = 1`)**

```sql
EXEC GetEmployeeById @emp_id = 1;
```

---

## 🔹 **3️⃣ إنشاء إجراء مخزن مع عدة معاملات (`Multiple Parameters`)**

✅ **مثال: إحضار الموظفين حسب القسم (`department_id`) والحد الأدنى للراتب (`min_salary`)**

```sql
CREATE PROCEDURE GetEmployeesByDeptAndSalary  
    @department_id INT,  
    @min_salary DECIMAL(10,2)  
AS  
BEGIN  
    SELECT * FROM employees  
    WHERE department_id = @department_id AND salary >= @min_salary;  
END;
```

📌 **تنفيذ الإجراء وتمرير القيم (`department_id = 1`, `min_salary = 5000`)**

```sql
EXEC GetEmployeesByDeptAndSalary @department_id = 1, @min_salary = 5000;
```

---

## 🔹 **4️⃣ إنشاء إجراء مخزن مع قيمة إرجاع (`Return Value`)**

✅ **مثال: إرجاع عدد الموظفين في قسم معين**

```sql
CREATE PROCEDURE GetEmployeeCountByDept  
    @department_id INT,  
    @count INT OUTPUT  
AS  
BEGIN  
    SELECT @count = COUNT(*) FROM employees WHERE department_id = @department_id;  
END;
```

📌 **تنفيذ الإجراء واسترجاع القيمة**

```sql
DECLARE @emp_count INT;  
EXEC GetEmployeeCountByDept @department_id = 1, @count = @emp_count OUTPUT;  
PRINT @emp_count;
```

---

## 🔹 **5️⃣ تعديل (`ALTER`) أو حذف (`DROP`) إجراء مخزن**

📌 **لتعديل إجراء مخزن (`ALTER PROCEDURE`)**

```sql
ALTER PROCEDURE GetAllEmployees  
AS  
BEGIN  
    SELECT name, salary FROM employees;  
END;
```

📌 **لحذف إجراء مخزن (`DROP PROCEDURE`)**

```sql
DROP PROCEDURE GetAllEmployees;
```

---

## 🏆 **ملخص سريع عن الإجراءات المخزنة**

|العملية|الأمر المستخدم|
|---|---|
|**إنشاء إجراء مخزن**|`CREATE PROCEDURE`|
|**تنفيذ إجراء مخزن**|`EXEC procedure_name`|
|**تعديل إجراء مخزن**|`ALTER PROCEDURE`|
|**حذف إجراء مخزن**|`DROP PROCEDURE`|
|**إرجاع قيمة**|`OUTPUT`|
|**إضافة معاملات**|`@param datatype`|

---

## 🎯 **الخلاصة**

- **الإجراءات المخزنة (`Stored Procedures`) توفر أداءً أفضل، وأمانًا أعلى، وتقلل من تكرار الكود**.
- **يمكن تمرير معاملات (`Parameters`) لتنفيذ أوامر مخصصة بناءً على المدخلات**.
- **يمكن استخدام معاملات `OUTPUT` لإرجاع قيم**.

---


## Connect Me :

- https://github.com/foefvjfev33
- https://t.me/It_auf
- https://www.youtube.com/@IT_red-j9b
- https://www.linkedin.com/in/mohamed-auf-860537353/