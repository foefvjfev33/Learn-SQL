# 📌 **SQL Constraints**

## 🔹 **ما هي القيود (Constraints) في SQL؟**

🚀 **القيود هي قواعد تُطبق على الأعمدة في جداول قاعدة البيانات لضمان صحة البيانات وحمايتها.**  
✅ **تساعد القيود في ضمان أن البيانات التي يتم إدخالها في الجداول تلبي بعض الشروط المتفق عليها مثل الفريدة، أو عدم وجود قيم فارغة، أو علاقات بين الجداول.**

---

## 🔹 **1️⃣ أنواع القيود الرئيسية في SQL**

1. **`NOT NULL`**
    
    - **وصف**: يضمن أن العمود لا يحتوي على قيم فارغة (`NULL`).
    - **مثال**:
    
    ```sql
    CREATE TABLE employees (
        employee_id INT NOT NULL,
        first_name VARCHAR(50) NOT NULL,
        last_name VARCHAR(50)
    );
    ```
    
    - **في هذا المثال**: تم تحديد العمود `employee_id` و `first_name` ليكونا غير فارغين.

---

1. **`UNIQUE`**
    
    - **وصف**: يضمن أن جميع القيم في العمود فريدة (لا تتكرر).
    - **مثال**:
    
    ```sql
    CREATE TABLE employees (
        employee_id INT NOT NULL UNIQUE,
        first_name VARCHAR(50),
        email VARCHAR(100) UNIQUE
    );
    ```
    
    - **في هذا المثال**: لا يمكن تكرار قيمة `employee_id` ولا قيمة `email` في الجدول.

---

1. **`PRIMARY KEY`**
    
    - **وصف**: يجمع بين قيود `NOT NULL` و `UNIQUE` لضمان أن القيم في العمود فريدة وغير فارغة. يُستخدم لتحديد العمود الذي يمثل المفتاح الرئيسي للجدول.
    - **مثال**:
    
    ```sql
    CREATE TABLE employees (
        employee_id INT PRIMARY KEY,
        first_name VARCHAR(50),
        last_name VARCHAR(50)
    );
    ```
    
    - **في هذا المثال**: يُعتبر العمود `employee_id` هو المفتاح الرئيسي ويجب أن يكون فريدًا وغير فارغ.

---

1. **`FOREIGN KEY`**
    
    - **وصف**: يُستخدم لإنشاء علاقة بين جدولين، حيث يشير العمود في الجدول الحالي إلى العمود الذي يحتوي على مفتاح رئيسي في جدول آخر.
    - **مثال**:
    
    ```sql
    CREATE TABLE orders (
        order_id INT PRIMARY KEY,
        order_date DATE,
        customer_id INT,
        FOREIGN KEY (customer_id) REFERENCES customers(customer_id)
    );
    ```
    
    - **في هذا المثال**: يتم ربط العمود `customer_id` في جدول `orders` بالعمود `customer_id` في جدول `customers`.

---

1. **`CHECK`**
    
    - **وصف**: يُستخدم للتحقق من أن البيانات المدخلة تلتزم بشرط معين.
    - **مثال**:
    
    ```sql
    CREATE TABLE employees (
        employee_id INT PRIMARY KEY,
        first_name VARCHAR(50),
        salary DECIMAL(10, 2),
        CHECK (salary >= 0)
    );
    ```
    
    - **في هذا المثال**: يتم التأكد من أن الراتب في العمود `salary` لا يمكن أن يكون أقل من 0.

---

1. **`DEFAULT`**
    
    - **وصف**: يُستخدم لتعيين قيمة افتراضية للعمود إذا لم يتم إدخال قيمة عند إدراج البيانات.
    - **مثال**:
    
    ```sql
    CREATE TABLE employees (
        employee_id INT PRIMARY KEY,
        first_name VARCHAR(50),
        status VARCHAR(20) DEFAULT 'Active'
    );
    ```
    
    - **في هذا المثال**: إذا لم يتم إدخال قيمة للعمود `status`، سيتم تعيين القيمة الافتراضية "Active".

---

1. **`INDEX`**
    
    - **وصف**: يُستخدم لتحسين سرعة البحث في البيانات داخل الجدول. يمكن إنشاء فهرس على الأعمدة لتسريع الاستعلامات.
    - **مثال**:
    
    ```sql
    CREATE INDEX idx_email ON employees (email);
    ```
    
    - **في هذا المثال**: يتم إنشاء فهرس على العمود `email` لتحسين سرعة البحث عن الموظفين باستخدام هذا العمود.

---

## 🔹 **2️⃣ مثال على إنشاء جدول مع عدة قيود**

📌 **مثال لإنشاء جدول مع جميع القيود المذكورة:**

```sql
CREATE TABLE employees (
    employee_id INT PRIMARY KEY,  -- مفتاح رئيسي
    first_name VARCHAR(50) NOT NULL,  -- غير فارغ
    last_name VARCHAR(50),
    email VARCHAR(100) UNIQUE,  -- فريد
    salary DECIMAL(10, 2) CHECK (salary >= 0),  -- تحقق من قيمة الراتب
    department_id INT,
    status VARCHAR(20) DEFAULT 'Active',  -- قيمة افتراضية
    FOREIGN KEY (department_id) REFERENCES departments(department_id)  -- مفتاح خارجي
);
```

---

## 🏆 **ملخص سريع عن القيود (Constraints) في SQL**

|القيود|الوصف|
|---|---|
|**`NOT NULL`**|يضمن أن العمود لا يحتوي على قيم فارغة (`NULL`).|
|**`UNIQUE`**|يضمن أن جميع القيم في العمود فريدة.|
|**`PRIMARY KEY`**|مزيج من `NOT NULL` و `UNIQUE` ويستخدم لتحديد المفتاح الرئيسي للجدول.|
|**`FOREIGN KEY`**|يحدد علاقة بين جدولين باستخدام العمود الذي يشير إلى المفتاح الرئيسي في جدول آخر.|
|**`CHECK`**|يفرض شرطًا على القيم المدخلة في العمود.|
|**`DEFAULT`**|يحدد قيمة افتراضية للعمود إذا لم يتم إدخال قيمة.|
|**`INDEX`**|يُستخدم لتحسين أداء الاستعلامات عن طريق إنشاء فهرس على الأعمدة.|

---

## 🎯 **الخلاصة**

- **القيود (Constraints) هي آلية لتطبيق قواعد على الأعمدة والبيانات داخل الجداول لضمان صحتها.**
- **تساعد القيود في تحسين جودة البيانات، مثل منع القيم الفارغة أو غير الفريدة، وتوفير علاقات بين الجداول.**
- **من خلال استخدام القيود المناسبة، يمكنك تحسين أداء قاعدة البيانات وضمان تماسكها.**

---


## Connect Me :

- https://github.com/foefvjfev33
- https://t.me/It_auf
- https://www.youtube.com/@IT_red-j9b
- https://www.linkedin.com/in/mohamed-auf-860537353/