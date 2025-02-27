# 📌 **SQL AUTO INCREMENT Field**

## 🔹 **ما هو حقل `AUTO INCREMENT` في SQL؟**

🚀 **حقل `AUTO INCREMENT` يُستخدم لتوليد قيمة تلقائية وفريدة للعمود عند إدخال بيانات جديدة، عادةً ما يُستخدم لهذا النوع من الأعمدة العمود الذي يحتوي على معرّف فريد (مثل المعرف `ID`).**  
✅ **هذا النوع من الأعمدة يساعد في إنشاء قيمة جديدة تلقائيًا لكل سجل جديد دون الحاجة إلى تحديد هذه القيمة يدويًا.**

---

## 🔹 **1️⃣ خصائص حقل `AUTO INCREMENT`**

1. **توليد قيم فريدة تلقائيًا**
    
    - **يتم زيادة قيمة الحقل تلقائيًا لكل سجل جديد يتم إضافته إلى الجدول، مما يضمن أن القيم ستكون فريدة ومتصاعدة.**
2. **استخدامه في الأعمدة الرئيسية (Primary Keys)**
    
    - **عادةً ما يتم استخدام `AUTO INCREMENT` في الأعمدة التي تمثل المفاتيح الرئيسية (`PRIMARY KEY`) لأن هذا يضمن أن كل سجل في الجدول له معرّف فريد.**
3. **زيادة تلقائية**
    
    - **تُزاد القيمة بشكل تلقائي عند إدخال السجلات الجديدة، مما يوفر وقتًا وجهدًا في كتابة القيم يدويًا.**

---

## 🔹 **2️⃣ كيفية استخدام حقل `AUTO INCREMENT`**

### **أ. أثناء إنشاء الجدول**

✅ **مثال: إنشاء جدول مع حقل `AUTO INCREMENT`**

```sql
CREATE TABLE employees (
    employee_id INT AUTO_INCREMENT PRIMARY KEY,  -- العمود `employee_id` سيزداد تلقائيًا
    first_name VARCHAR(50),
    last_name VARCHAR(50),
    salary DECIMAL(10, 2)
);
```

🔹 **في هذا المثال**:

- **تم استخدام `AUTO_INCREMENT` على العمود `employee_id`، وهو العمود الذي سيُعطى قيمة فريدة تلقائيًا لكل سجل جديد.**
- **العمود `employee_id` سيكون المفتاح الرئيسي (`PRIMARY KEY`) في الجدول.**

### **ب. إضافة حقل `AUTO INCREMENT` إلى جدول موجود**

✅ **مثال: إضافة حقل `AUTO INCREMENT` إلى جدول موجود**

```sql
ALTER TABLE employees
ADD COLUMN employee_id INT AUTO_INCREMENT PRIMARY KEY;
```

🔹 **في هذا المثال**:

- **تم إضافة العمود `employee_id` إلى الجدول `employees` مع تعيينه ليكون حقل `AUTO_INCREMENT` و `PRIMARY KEY`.**

---

## 🔹 **3️⃣ تغيير خصائص `AUTO INCREMENT`**

📌 **إذا أردت تغيير القيمة التي يبدأ منها `AUTO INCREMENT` أو تحديد الزيادة لكل قيمة، يمكنك استخدام أوامر خاصة بذلك حسب قاعدة البيانات.**

### **أ. تغيير القيمة الابتدائية**

✅ **مثال: تحديد القيمة الابتدائية لحقل `AUTO INCREMENT`**

```sql
ALTER TABLE employees AUTO_INCREMENT = 100;
```

🔹 **في هذا المثال**:

- **تم تعيين القيمة الابتدائية لحقل `AUTO_INCREMENT` لتكون 100، لذا سيبدأ العد من 100 بدلاً من 1.**

### **ب. تغيير قيمة الزيادة**

✅ **مثال: تحديد الزيادة بين القيم**

```sql
ALTER TABLE employees AUTO_INCREMENT = 10;
```

🔹 **في هذا المثال**:

- **تم تحديد أن الزيادة بين القيم ستكون 10 بدلاً من الزيادة الافتراضية بمقدار 1.**

---

## 🔹 **4️⃣ ملاحظات مهمة حول `AUTO INCREMENT`**

1. **قيد الفهرس (Primary Key)**
    
    - **غالبًا ما يُستخدم `AUTO INCREMENT` في الأعمدة التي هي مفاتيح رئيسية (`PRIMARY KEY`)، مما يضمن أن كل سجل يحتوي على معرّف فريد.**
2. **التكرار أو التعيين اليدوي للقيم**
    
    - **لا يمكنك إدخال قيمة يدوية في العمود الذي يحتوي على `AUTO INCREMENT` (إلا إذا تم تعطيل هذا السلوك في بعض قواعد البيانات مثل MySQL باستخدام `SET` أو استخدام `INSERT` مع تعيين قيمة يدوية).**
3. **يختلف في قواعد البيانات المختلفة**
    
    - **طريقة تعريف `AUTO INCREMENT` قد تختلف حسب نوع قاعدة البيانات:**
        - **في MySQL وSQLite:** يستخدم `AUTO_INCREMENT`.
        - **في PostgreSQL:** يستخدم `SERIAL` أو `BIGSERIAL`.
        - **في SQL Server:** يستخدم `IDENTITY`.

---

## 🏆 **ملخص سريع عن `AUTO INCREMENT` في SQL**

|القيد|الوصف|
|---|---|
|**`AUTO_INCREMENT`**|يُستخدم لتوليد قيمة فريدة تلقائيًا في العمود، غالبًا في الأعمدة الرئيسية (`PRIMARY KEY`).|
|**الزيادة التلقائية**|يتم زيادة قيمة العمود تلقائيًا عند إدخال سجل جديد.|
|**تغيير القيمة الابتدائية**|يمكن تحديد القيمة التي يبدأ منها العد باستخدام `AUTO_INCREMENT = <value>`.|

---

## 🎯 **الخلاصة**

- **حقل `AUTO INCREMENT` يُستخدم لتوليد قيم فريدة تلقائيًا في الأعمدة، وهو مثالي للمفاتيح الرئيسية.**
- **يساعد في تبسيط إدارة البيانات دون الحاجة لتحديد القيم يدويًا في كل مرة يتم فيها إضافة سجل جديد.**
- **يمكن تعديل القيمة الابتدائية أو الزيادة للـ `AUTO INCREMENT` في بعض قواعد البيانات.**

---


## Connect Me :

- https://github.com/foefvjfev33
- https://t.me/It_auf
- https://www.youtube.com/@IT_red-j9b
- https://www.linkedin.com/in/mohamed-auf-860537353/