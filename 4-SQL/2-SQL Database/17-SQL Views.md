# 📌 **SQL Views**

## 🔹 **ما هي الـ `VIEW` في SQL؟**

**الـ View** في SQL هو عبارة عن جدول افتراضي يتم إنشاؤه باستخدام استعلام **`SELECT`**، حيث يُمكنك من عرض البيانات من جداول متعددة أو من نفس الجدول مع تحويل أو تصفية البيانات بطريقة معينة. **الـ View لا يحتوي على بيانات فعلية**، بل هو مجرد استعلام محفوظ يمكن استخدامه كما لو كان جدولًا عاديًا.

---

## 🔹 **1️⃣ كيفية إنشاء View**

### **أ. إنشاء View باستخدام `CREATE VIEW`**

لإنشاء View جديد، يمكنك استخدام الأمر **`CREATE VIEW`**، حيث تحدد اسم الـ View واستعلام **`SELECT`** الذي سيُستخدم لعرض البيانات.

✅ **مثال: إنشاء View لعرض أسماء الموظفين ورواتبهم**

```sql
CREATE VIEW employee_salaries AS
SELECT first_name, last_name, salary
FROM employees
WHERE salary > 5000;
```

🔹 **الشرح**:

- **تم إنشاء `employee_salaries` كـ View يعرض فقط الموظفين الذين يتجاوز راتبهم 5000.**
- **بدلاً من كتابة استعلام مع فلترة الرواتب في كل مرة، يمكنك ببساطة استدعاء هذا الـ View لعرض البيانات بسهولة.**

### **ب. استخدام `SELECT` من الـ View**

بمجرد إنشاء الـ View، يمكنك استعلامه كما لو كان جدولًا:

```sql
SELECT * FROM employee_salaries;
```

🔹 **النتيجة**: سيتم عرض أسماء الموظفين الذين يتجاوز راتبهم 5000.

---

## 🔹 **2️⃣ تعديل View**

### **أ. تعديل View باستخدام `CREATE OR REPLACE VIEW`**

إذا كنت بحاجة إلى تعديل الـ View بعد إنشائه، يمكنك استخدام **`CREATE OR REPLACE VIEW`** لتغيير الاستعلام الذي يتم استخدامه في الـ View.

✅ **مثال: تعديل الـ View لإضافة أعمدة إضافية**

```sql
CREATE OR REPLACE VIEW employee_salaries AS
SELECT first_name, last_name, salary, department
FROM employees
WHERE salary > 5000;
```

🔹 **الشرح**:

- **تم إضافة العمود `department` إلى الـ View.**
- **سيتم استبدال الـ View القديم بنسخة جديدة تحتوي على العمود الإضافي.**

### **ب. حذف الـ View باستخدام `DROP VIEW`**

إذا أردت حذف الـ View، يمكنك استخدام الأمر **`DROP VIEW`**:

```sql
DROP VIEW employee_salaries;
```

🔹 **الشرح**:

- **هذا سيحذف الـ View `employee_salaries` من قاعدة البيانات.**

---

## 🔹 **3️⃣ أنواع الـ Views**

1. **`Simple Views`**
    
    - هي Views تُستخدم لاستعلامات بسيطة يتم فيها عرض بيانات من جدول واحد فقط.
    - مثال:
        
        ```sql
        CREATE VIEW simple_view AS
        SELECT column1, column2 FROM table_name;
        ```
        
2. **`Complex Views`**
    
    - هي Views تستخدم استعلامات معقدة تتضمن دمج جداول متعددة باستخدام **`JOIN`**، **`GROUP BY`**، **`HAVING`**، إلخ.
    - مثال:
        
        ```sql
        CREATE VIEW complex_view AS
        SELECT e.first_name, e.last_name, d.department_name
        FROM employees e
        JOIN departments d ON e.department_id = d.department_id;
        ```
        
3. **`Updatable Views`**
    
    - يمكن تعديل البيانات من خلال الـ View إذا كان الاستعلام الأساسي بسيطًا (أي لا يحتوي على عمليات معقدة مثل **`GROUP BY`** أو **`JOIN`**).
4. **`Non-Updatable Views`**
    
    - هذه Views لا يمكن تعديل البيانات من خلالها. عادةً ما يكون هذا بسبب أن الاستعلام يحتوي على عمليات معقدة مثل **`JOIN`** أو **`DISTINCT`**.

---

## 🔹 **4️⃣ استخدامات الـ Views**

1. **تحسين الأمان**
    
    - **يمكنك استخدام الـ Views لتحديد البيانات التي يتم الوصول إليها.** على سبيل المثال، يمكنك إخفاء بعض الأعمدة من الجداول الأساسية عبر الـ View، بحيث يتم عرض بيانات معينة فقط.
    
    ✅ **مثال: عرض بعض الأعمدة فقط عبر الـ View**
    
    ```sql
    CREATE VIEW employee_details AS
    SELECT first_name, last_name FROM employees;
    ```
    
2. **تبسيط الاستعلامات المعقدة**
    
    - **يمكنك استخدام الـ Views لتبسيط الاستعلامات المعقدة.** إذا كنت تستخدم استعلامًا معقدًا بشكل متكرر، يمكن تخزينه في View، مما يقلل من الحاجة لإعادة كتابته.
    
    ✅ **مثال: تخزين استعلام معقد في View**
    
    ```sql
    CREATE VIEW top_salaries AS
    SELECT first_name, last_name, salary
    FROM employees
    WHERE salary > 10000;
    ```
    
3. **توحيد البيانات**
    
    - **الـ Views تساعد في دمج بيانات من جداول متعددة، مما يجعل الوصول إليها أكثر سهولة.**

---

## 🔹 **5️⃣ استعلامات متقدمة مع الـ Views**

### **أ. استخدام `JOIN` في الـ View**

✅ **مثال: إنشاء View لدمج جداول متعددة**

```sql
CREATE VIEW employee_department AS
SELECT e.first_name, e.last_name, d.department_name
FROM employees e
JOIN departments d ON e.department_id = d.department_id;
```

### **ب. استخدام `GROUP BY` و `HAVING` في الـ View**

✅ **مثال: إنشاء View لعرض إحصائيات الرواتب في الأقسام المختلفة**

```sql
CREATE VIEW department_salary_stats AS
SELECT department_id, AVG(salary) AS avg_salary
FROM employees
GROUP BY department_id
HAVING AVG(salary) > 6000;
```

---

## 🏆 **ملخص سريع حول الـ Views في SQL**

|العملية|الوصف|
|---|---|
|**إنشاء View**|`CREATE VIEW` لإنشاء View يحتوي على استعلام `SELECT`.|
|**استخدام View**|`SELECT * FROM view_name;` لاستعلام البيانات من الـ View.|
|**تعديل View**|`CREATE OR REPLACE VIEW` لتغيير استعلام الـ View.|
|**حذف View**|`DROP VIEW` لحذف الـ View من قاعدة البيانات.|
|**أنواع Views**|`Simple View`, `Complex View`, `Updatable View`, `Non-Updatable View`.|

---

## 🎯 **الخلاصة**

- **الـ View هو أداة قوية في SQL تتيح لك إنشاء جداول افتراضية لتبسيط الوصول إلى البيانات المعقدة أو تحسين الأمان عبر تقليل كمية البيانات المعروضة.**
- **يمكنك استخدام الـ Views مع عمليات `JOIN`، `GROUP BY`، و `HAVING` لدمج البيانات وتحليلها بسهولة.**

---


## Connect Me :

- https://github.com/foefvjfev33
- https://t.me/It_auf
- https://www.youtube.com/@IT_red-j9b
- https://www.linkedin.com/in/mohamed-auf-860537353/