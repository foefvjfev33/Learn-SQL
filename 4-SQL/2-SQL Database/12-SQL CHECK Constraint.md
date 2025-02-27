# 📌 **SQL CHECK Constraint**

## 🔹 **ما هو قيد `CHECK` في SQL؟**

🚀 **قيد `CHECK` يُستخدم لتحديد شرط أو قاعدة يتم تطبيقها على عمود أو مجموعة من الأعمدة في الجدول.**  
✅ **يضمن قيد `CHECK` أن القيم المدخلة في الأعمدة تتوافق مع القيم المسموح بها وفقًا للشرط المُحدد.**

---

## 🔹 **1️⃣ خصائص `CHECK`**

1. **التأكد من القيم المدخلة**
    
    - **قيد `CHECK` يُستخدم لضمان أن القيم المدخلة في العمود تتوافق مع شرط معين، مثل التأكد من أن العمر أكبر من 18 أو أن الراتب أكبر من حد معين.**
2. **يمكن أن يكون الشرط معقدًا**
    
    - يمكن تحديد شروط معقدة باستخدام العوامل المنطقية مثل `AND` و `OR` و `NOT` داخل القيد.
3. **التأكد من صحة البيانات**
    
    - **يعمل قيد `CHECK` كآلية تحقق لضمان عدم إدخال بيانات غير صالحة في الجدول.**

---

## 🔹 **2️⃣ كيفية استخدام `CHECK`**

### **أ. أثناء إنشاء الجدول**

✅ **مثال: إنشاء جدول مع قيد `CHECK` للتحقق من أن العمر أكبر من 18 سنة**

```sql
CREATE TABLE employees (
    employee_id INT PRIMARY KEY,
    first_name VARCHAR(50),
    last_name VARCHAR(50),
    age INT,
    salary DECIMAL(10, 2),
    CHECK (age > 18)  -- العمر يجب أن يكون أكبر من 18
);
```

🔹 **في هذا المثال**:

- **قيد `CHECK` يضمن أن القيم المدخلة في عمود `age` ستكون أكبر من 18، وإذا تم إدخال قيمة أقل، سيتم رفض الإدخال.**

### **ب. أثناء تعديل الجدول**

✅ **مثال: إضافة قيد `CHECK` إلى عمود موجود في جدول موجود بالفعل**

```sql
ALTER TABLE employees
ADD CONSTRAINT check_salary CHECK (salary > 1000);  -- الراتب يجب أن يكون أكبر من 1000
```

🔹 **في هذا المثال**:

- **تم إضافة قيد `CHECK` على العمود `salary` لضمان أن القيم المدخلة في هذا العمود تكون أكبر من 1000.**

---

## 🔹 **3️⃣ استخدام شروط متعددة في `CHECK`**

📌 **يمكنك استخدام شروط متعددة داخل قيد `CHECK` للتحقق من أكثر من شرط على الأعمدة.**

✅ **مثال: تطبيق شرطين في قيد `CHECK` باستخدام `AND`**

```sql
CREATE TABLE employees (
    employee_id INT PRIMARY KEY,
    first_name VARCHAR(50),
    last_name VARCHAR(50),
    age INT,
    salary DECIMAL(10, 2),
    CHECK (age > 18 AND salary > 1000)  -- العمر يجب أن يكون أكبر من 18 والراتب أكبر من 1000
);
```

🔹 **في هذا المثال**:

- **يتم التحقق من أن العمر أكبر من 18 AND الراتب أكبر من 1000 عند إدخال البيانات في الجدول.**

---

## 🔹 **4️⃣ القيم الفارغة (`NULL`) مع `CHECK`**

📌 **يمكن لقيد `CHECK` تطبيق شرط على القيم الفارغة أيضًا، لكن القيم الفارغة عادةً ما تُعتبر متوافقة مع أي شرط.**  
✅ **إذا كان العمود يسمح بالقيم الفارغة (`NULL`)، فإن أي إدخال فارغ يتم قبوله بغض النظر عن القيد المحدد.**

- **إذا كان الشرط يتطلب قيمة معينة، لكن القيمة هي `NULL`، سيتم قبول القيمة الفارغة لأنها لا تُعتبر مخالفة للشرط.**

---

## 🔹 **5️⃣ إزالة أو تعديل قيد `CHECK`**

📌 **إذا كنت ترغب في إزالة أو تعديل قيد `CHECK`، يمكنك استخدام `ALTER TABLE`.**

✅ **مثال: إزالة قيد `CHECK`**

```sql
ALTER TABLE employees
DROP CONSTRAINT check_salary;
```

🔹 **في هذا المثال**: تم إزالة قيد `CHECK` الذي يفرض شرط الراتب.

---

## 🏆 **ملخص سريع عن `CHECK` في SQL**

|القيد|الوصف|
|---|---|
|**`CHECK`**|يُستخدم لتحديد شرط يجب أن تتوافق معه القيم المدخلة في عمود أو مجموعة أعمدة.|
|**إضافة شرط متعدد**|يمكن استخدام عوامل منطقية مثل `AND` و `OR` لتحديد شروط معقدة داخل `CHECK`.|
|**التعامل مع القيم الفارغة (`NULL`)**|القيم الفارغة عادةً ما تُعتبر متوافقة مع شروط `CHECK`.|

---

## 🎯 **الخلاصة**

- **قيد `CHECK` يُستخدم لضمان أن القيم المدخلة في الأعمدة تتوافق مع شروط معينة.**
- **يمكن تطبيق `CHECK` أثناء إنشاء الجدول أو تعديله لاحقًا.**
- **يُمكن استخدام شروط معقدة ودمج عوامل منطقية مثل `AND` و `OR`.**

---


## Connect Me :

- https://github.com/foefvjfev33
- https://t.me/It_auf
- https://www.youtube.com/@IT_red-j9b
- https://www.linkedin.com/in/mohamed-auf-860537353/