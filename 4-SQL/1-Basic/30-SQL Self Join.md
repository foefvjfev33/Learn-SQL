# 📌 **`SELF JOIN` في SQL – الانضمام الذاتي**

## 🔹 **ما هو `SELF JOIN`؟**

`SELF JOIN` هو نوع خاص من الـ **`JOIN`** حيث يتم **ضم الجدول إلى نفسه**.  
✅ يتم التعامل مع الجدول كما لو كان **جدولين منفصلين** باستخدام **أسماء مستعارة (`Aliases`)**.  
✅ يُستخدم عندما يكون هناك **علاقات بين الصفوف داخل نفس الجدول**، مثل **هيكلة الموظفين والمديرين** أو **العلاقات بين العملاء والموردين**.

---

## 🔹 **الصيغة العامة (`Syntax`)**

```sql
SELECT A.column1, B.column2, ...  
FROM table_name AS A  
JOIN table_name AS B  
ON A.common_column = B.common_column;
```

📌 **A و B هما أسماء مستعارة (`Aliases`) لنفس الجدول، مما يسمح بمعاملته كجدولين مختلفين.**

---

## 🔹 **مثال عملي على `SELF JOIN`**

### 🗄️ **جدول `employees` (الموظفون والمديرون)**

|id|name|manager_id|
|---|---|---|
|1|John|NULL|
|2|Alice|1|
|3|Bob|1|
|4|Carol|2|

🔹 **نريد استرجاع أسماء الموظفين مع أسماء مديريهم.**

```sql
SELECT emp.name AS Employee, mgr.name AS Manager  
FROM employees AS emp  
LEFT JOIN employees AS mgr  
ON emp.manager_id = mgr.id;
```

🔹 **النتيجة:**

|Employee|Manager|
|---|---|
|John|NULL|
|Alice|John|
|Bob|John|
|Carol|Alice|

📌 **تحليل النتيجة:**

- **John** ليس لديه مدير (`NULL`).
- **Alice و Bob** مديرهما هو **John**.
- **Carol** مديرها هو **Alice**.

---

## 🔹 **استخدام `SELF JOIN` مع `WHERE` لتصفية البيانات**

```sql
SELECT emp.name AS Employee, mgr.name AS Manager  
FROM employees AS emp  
JOIN employees AS mgr  
ON emp.manager_id = mgr.id  
WHERE mgr.name = 'John';
```

🔹 **النتيجة:**

|Employee|Manager|
|---|---|
|Alice|John|
|Bob|John|

📌 **يتم عرض الموظفين الذين مديرهم هو "John" فقط.**

---

## 🔹 **استخدام `SELF JOIN` لمقارنة البيانات بين صفوف الجدول**

مثال: لدينا جدول للمنتجات، ونريد معرفة المنتجات التي لها نفس السعر.

### 🗄️ **جدول `products`**

|id|name|price|
|---|---|---|
|1|Apple|10|
|2|Banana|5|
|3|Orange|10|
|4|Mango|15|

🔹 **نريد عرض المنتجات التي لها نفس السعر.**

```sql
SELECT A.name AS Product1, B.name AS Product2, A.price  
FROM products AS A  
JOIN products AS B  
ON A.price = B.price  
WHERE A.id <> B.id;
```

🔹 **النتيجة:**

|Product1|Product2|Price|
|---|---|---|
|Apple|Orange|10|
|Orange|Apple|10|

📌 **تمت مطابقة المنتجات التي لها نفس السعر، مع تجنب مقارنة المنتج بنفسه (`A.id <> B.id`).**

---

## 🏆 **ملخص سريع عن `SELF JOIN`**

|الميزة|التفاصيل|
|---|---|
|**يُستخدم لمقارنة البيانات داخل الجدول نفسه**|يسمح بربط الصفوف ببعضها البعض.|
|**يستخدم `Aliases`**|لتجنب الالتباس بين الجدول الأصلي والجدول المنضم إليه.|
|**مثالي للبيانات الهرمية**|مثل الموظفين والمديرين، أو المنتجات ذات الأسعار المتشابهة.|
|**يمكن تصفيته باستخدام `WHERE`**|للتركيز على بيانات محددة.|

---

## 🎯 **الخلاصة**

- **`SELF JOIN`** هو **انضمام الجدول إلى نفسه** لمقارنة البيانات بين الصفوف.
- **يستخدم `Aliases` (أسماء مستعارة) لتمييز الجدولين أثناء الربط.**
- **يُستخدم في العلاقات الهرمية** (مثل الموظفين والمديرين).
- **يمكن استخدامه لمقارنة القيم المتشابهة داخل نفس الجدول.**

---


## Connect Me :

- https://github.com/foefvjfev33
- https://t.me/It_auf
- https://www.youtube.com/@IT_red-j9b
- https://www.linkedin.com/in/mohamed-auf-860537353/